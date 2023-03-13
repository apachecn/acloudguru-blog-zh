# Geohash 和 DynamoDB 用于基于位置的搜索结果

> 原文：<https://acloudguru.com/blog/engineering/location-based-search-results-with-dynamodb-and-geohash>

得益于 [DynamoDB](https://acloudguru.com/course/amazon-dynamodb-deep-dive) 和一个小型地理编码 NPM 包，搜索最近或最远的位置变得很容易。

现在，许多数据集都包含地理空间信息，尤其是当您使用移动应用程序或谷歌地图时。地理空间数据是描述包含纬度和经度的项目的一种奇特方式，但是处理基于最近的、*最远的*或在一定距离内的的查询有些复杂。

这有什么难的？假设您有 10 家零售店，一位客户想知道最近的位置。显而易见的方法是找到顾客的位置，然后[计算该位置和每个商店之间的距离](https://orion.math.iastate.edu/dept/links/formulas/form2.pdf)。

### 有什么问题？

嗯，有两个问题——第一个是之前的计算假设两点在一个平面上，而世界不是平的(事实上，它不是平的)。你必须考虑我们居住的岩石的圆形，这就引出了[哈弗辛公式](https://en.wikipedia.org/wiki/Haversine_formula)。

虽然第一个问题会导致计算错误，但第二个问题更成问题。随着零售店数量的增加，你的搜索速度会变慢——可怕的[O(*n*)](https://en.wikipedia.org/wiki/Big_O_notation)——因为你必须将用户的位置与每家店的*进行对比。如果用户正在移动，因此原始位置会频繁更新，该怎么办？*

如果你将问题扩大到“找到最近的咖啡店”，我们的第一个解决方案将要求我们将用户的位置与地球上的每一家咖啡店进行比较。因此，我们需要一个更好的方法来解决这个问题，最好是一个能够管理全球规模的方法。基本上，类似于谷歌地图的做法。

### Geohash 的力量

Geohashes 有点复杂，但需要知道的关键是，它将世界划分为网格中的许多方块。通过这样做，我们可以预先消除大部分数据，只关注我们的潜在目标所在的方格。这是一个非常优雅的解决方案。

*   哈希最长为 12 个字符，哈希越长，它引用的方块越小。
*   哈希的第一个字符标识了网格中 32 个单元中的一个，大约是地球上 5000 公里 x 5000km 公里。
*   第二个字符标识第一个单元格中 32 个方块中的一个，因此这两个字符的分辨率现在是 1250km x 1250km。
*   这种情况一直持续到第十二个字符，它可以识别地球上只有几平方英寸的区域。

如果你使用的散列太长——换句话说，方块太小——你最终会搜索更多的方块来得到结果。如果你使用一个太短的 hash，你将会在方块中返回太多的条目，你的搜索将不会很快。因此，在选择散列长度之前，您需要知道搜索的分辨率。

这听起来可能很难，但比你想象的要容易。对于我们查找零售店和咖啡店的例子，没有必要有一个 2 英寸的地球网格。我们可以用 5-7 个字符解决 1-10 公里的搜索。

### 亚马逊 DynamoDB 的地理库

有一篇来自 2013 年的 [AWS 博客文章](https://aws.amazon.com/blogs/mobile/geo-library-for-amazon-dynamodb-part-1-table-structure/)详细介绍了 Geo 库，但它是一个需要服务器的特定于 Java 的解决方案。最近有一个 [NPM 包](https://www.npmjs.com/package/dynamodb-geo)将这项工作移植到 Node，可以在[无服务器](https://acloudguru.com/course/serverless-concepts)架构中使用。

为了验证这一点，我找到了美国所有星巴克门店的列表，然后发现了一个链接，在那里有人把这个链接从 T2 变成了 JSON。按照 NPM 包中的文档，我拼凑了这个脚本来配置 DynamoDB 表并加载数据。

让我给你介绍一下亮点。

首先，让我们创建一个表，该表旋转出一个新的 DynamoDB 表，该表具有使搜索工作所需的分区键和索引。

```
const ddbGeo = require('dynamodb-geo')

const config = new ddbGeo.GeoDataManagerConfiguration(ddb, 'yourTableName')
config.hashKeyLength = 5
const myGeoTableManager = new ddbGeo.GeoDataManager(config)
const setupTable = () => {

   const createTableInput = ddbGeo.GeoTableUtil.getCreateTableRequest(config)

  createTableInput.ProvisionedThroughput.ReadCapacityUnits = 5
  console.dir(createTableInput, { depth: null })
  ddb.createTable(createTableInput).promise()
    .then(function () { return ddb.waitFor('tableExists', { TableName: config.tableName }).promise() })
    .then(function () { console.log('Table created and ready!') })
}
```

接下来，我们加载数据:

```
const loadTable = () => {

  const data = require('../data/starbucks_us_locations')

  const putPointInputs = data.map(function (location) {
      return {
          RangeKeyValue: { S: uuid.v4() }
          GeoPoint: {
              latitude: location.position.lat,
              longitude: location.position.lng
          },
          PutItemInput: {
              Item: {
                name: { S: location.name }, 
                address: { S: location.address }
              }
          }
      }
  })

  const BATCH_SIZE = 25
  const WAIT_BETWEEN_BATCHES_MS = 1000       
  let currentBatch = 1

  function resumeWriting() {
    if (putPointInputs.length === 0) return Promise.resolve()
    const thisBatch = []
    for (let i = 0, itemToAdd = null; i < BATCH_SIZE && (itemToAdd = putPointInputs.shift()); i++) {
      thisBatch.push(itemToAdd)
    }
    console.log('Writing batch ' + (currentBatch++) + '/' + Math.ceil(data.length / BATCH_SIZE))

    return myGeoTableManager.batchWritePoints(thisBatch).promise()
      .then(function () {
        return new Promise(function (resolve) {
          setInterval(resolve,WAIT_BETWEEN_BATCHES_MS)
        })
      })
      .then(function () {
        return resumeWriting()
      })
  }
  return resumeWriting().catch(function (error) {
    console.warn(error)
  })
}
```

这将从 json 文件加载 Starbucks 位置，创建一个要插入到表中的项目数组，并以 25 个项目为一批上传到 DynamoDB。每批之间会有一个延迟，以减缓插入过程，并减少写入容量单元(wcu)的消耗。

上传后，您可以看到所有位置及其由库自动计算的地理哈希值和哈希键:

加载数据后，查询就很简单了——我们只需提供搜索位置的纬度和经度，以及搜索区域的半径:

```
const AWS = require('aws-sdk')
AWS.config.update({region: 'us-east-1'})

const ddb = new AWS.DynamoDB() 
const ddbGeo = require('dynamodb-geo')

const config = new ddbGeo.GeoDataManagerConfiguration(ddb, 'yourTableName')
config.hashKeyLength = 5

const myGeoTableManager = new ddbGeo.GeoDataManager(config)

myGeoTableManager.queryRadius({
  RadiusInMeter: 1000,
  CenterPoint: {
      latitude: 40.7769099,
      longitude: -73.9822532
  }
})
.then((locations) => console.log(locations))
```

### 我们来试试吧！

我构建了一个[简单的前端](https://caffeinate.jbes.dev/),它使用星巴克数据列表来显示 1 公里内最近的星巴克——它默认为纽约市，因为这看起来像是他们商店最密集的位置。

如果您在地图周围单击，它会根据地图的新中心从 DynamoDB 获取列表:

总的来说，在这个解决方案中使用 DynamoDB 的优点是在负载下非常稳定的性能。借助 DynamoDB 现在可用的按需容量，它可以处理峰值流量，而无需您管理调配的吞吐量。

* * *

## 获得更好职业所需的技能。

掌握现代技术技能，获得认证，提升您的职业生涯。无论您是新手还是经验丰富的专业人士，您都可以通过实践来学习，并在 ACG 的帮助下推进您的云计算职业生涯。

* * *

请在下面的评论中告诉我你的想法！