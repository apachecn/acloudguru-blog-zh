# DynamoDB 流:如何构建聚合

> 原文：<https://acloudguru.com/blog/engineering/building-aggregations-with-dynamodb-streams>

随着[Cloud Adventure:Race To Cloud Castle](https://acloudguru.com/blog/news/its-time-to-play-cloud-adventure-race-to-cloud-castle)游戏的全面展开(请在 9 月 4 日前进入！)现在似乎是一个很好的时机来打破游戏建设的一个有趣的方面:排行榜聚合。

### 游戏如何运作

在“云冒险”中，玩家们竞相寻找和报告由隐藏在各种云服务中的宝石标记的路径。当你点击游戏页面上的“提交路径”时，会触发以下事件流:

![event flow diagram](img/60f0a1a19c8ad2f6fef8b30b43a77cc8.png)

如果您的路径是有效的，我们将它存储在 DynamoDB 表中，格式如下:

![DynamoDB table format](img/d046025ce02a8c88c729561153e9fc89.png)

这对于存储和检索路径非常有用。通过将我们的用户标识符存储在分区键中，将我们提交的路径存储在排序键中，我们可以查询用户标识符，一次性获得与该用户相关的所有路径——这对于检查游戏进度非常有用。

## 向 DynamoDB 添加聚合

但是我们想做的不仅仅是存储和检索路径。正如您在[排行榜页面](https://adventure.acloud.guru)上看到的，我们想就我们的数据提出以下问题:

*   有多少人(“活跃玩家”)向排行榜提交了至少一条有效路径？
*   有多少人找到了 X 条有效路径，其中 X 是 1 到 12 之间的任意数字？
*   所有玩家总共发现了多少条路径(有重叠)？

对于上面展示的 DynamoDB 模型，没有简单的查询可以找到这些问题的答案；您必须扫描整个表中的每一项，并进行一系列客户端计算。又慢又贵！

相反，我们需要[构建一些聚合](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/bp-gsi-aggregation.html)。如果您觉得这一定比将数据放入关系数据库和编写 SUM 查询复杂得多，请不要担心:有了 AWS SAM 的一点帮助，我们只需几分钟就可以启动并运行。

* * *

[**成年人的 NoSQL:dynamo db 单表建模 w/里克·霍利汉**](https://get.acloudguru.com/nosql-for-grownups-dynamodb-webinar) DynamoDB 可以作为传统关系数据库的可伸缩、经济高效的替代品。。。如果正确使用的话！在[这个免费的点播网络研讨会](https://get.acloudguru.com/nosql-for-grownups-dynamodb-webinar)中，AWS 的高级实践经理、单表 DynamoDB 设计的发明者里克·霍利汉展示了他在 DynamoDB 中建模复杂数据访问模式的技巧。

* * *

## DynamoDB 表格布局

请记住，DynamoDB 表是“读模式的”，而不是“写模式的”——您可以将任何数据放入您想要的属性中；正确地解释它们取决于客户。这允许我们做一些叫做 **[的事情，索引重载](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/bp-gsi-overloading.html)。**我们可以将聚合作为*附加记录存储在同一个 DynamoDB 表*中。毕竟，当我们可以轻松地使用一个表时，为什么要配置两个表呢？

这就是为什么我给我的分区和排序键取了一个通用的名字(“pk”和“sk”)，这样我就不会局限于把它们看作“用户名”或“路径”字段。

![example partition and sort key names](img/22e6d0913826f7095d248ed7f7baf6dc.png)

## 设置 DynamoDB 流

现在，我们所要做的就是更新这些集合。我们可以通过每当用户报告新路径时同步更新 DynamoDB 中的一组聚合字段来做到这一点。但这将很快开始阻碍用户体验。

相反，我们可以将路径更新视为事件，并背着用户异步处理它们。鬼鬼祟祟！

很方便地， [DynamoDB 给了我们一个很酷的特性，叫做 Streams](https://acloudguru.com/blog/engineering/using-the-dynamodb-document-client-with-dynamodb-streams-from-aws-lambda) ，它的行为很像是与我们的表直接集成的 Kinesis。设置好之后，我们就可以将对表数据的任何更改作为事件导出，以便进行后续处理。

![diagram of how synchronous and asynchronous Streams interact](img/c115ce4a78d5e96d7ca8865c85300b4c.png)

(我指的是“任何事件”。DynamoDB 流不支持过滤。因此，我们的处理程序必须挑选所有的表变化，以便找到他们关心的变化。)

好消息是，我们可以在一个 [AWS SAM 模板](https://aws.amazon.com/serverless/sam/)中用最少的配置定义 DynamoDB 流。以下是我的表格资源:

```
AWSTemplateFormatVersion: '2010-09-09'
Transform: AWS::Serverless-2016-10-31
Description: SAM template for DynamoDB aggregations
Resources:
  ResultsTable:
    Type: AWS::DynamoDB::Table
    Properties:
      StreamSpecification:
        StreamViewType: NEW_AND_OLD_IMAGES
      AttributeDefinitions:
        - AttributeName: "pk"
          AttributeType: "S"
        - AttributeName: "sk"
          AttributeType: "S"
      KeySchema:
        - AttributeName: "pk"
          KeyType: "HASH"
        - AttributeName: "sk"
          KeyType: "RANGE"
      BillingMode: "PAY_PER_REQUEST"
```

SAM 使用`StreamViewType`属性来直觉判断我们想要将一个流连接到这个表。`NEW_AND_OLD_IMAGES`值意味着每次对表进行更改时，我们都希望看到流中旧的和修改过的数据。

注意，我们没有在这个表上定义任何额外的辅助索引——我们将只使用主表索引来进行聚合！

现在我们只需要将流连接到将处理聚合的 Lambda 函数。在 Lambda 资源的`Events`部分，我们将添加一个类型为`DynamoDB`的函数触发器，连接到我们在表上隐式创建的流。`TRIM_HORIZON`的`StartingPosition`意味着我们总是希望从流中最早的未处理记录开始，而`BatchSize`意味着我们一次将处理多达十个记录。

```
 AggregatorFunction:
    Type: AWS::Serverless::Function
    Properties:
      CodeUri: backend/
      Handler: handler.aggregation_handler
      Runtime: python3.8
      Policies:
        - DynamoDBCrudPolicy:
            TableName: !Ref ResultsTable
      Environment:
        Variables:
          TABLE_NAME: !Ref ResultsTable
      Events:
        DynamoDBEvent:
          Type: DynamoDB
          Properties:
              Stream:
                  !GetAtt ResultsTable.StreamArn
              StartingPosition: TRIM_HORIZON
              BatchSize: 10
```

### 构建聚合

正如您在函数定义中看到的，我选择用 Python 3 编写我的 Lambda。你会注意到我正在使用 Python 的`logger`模块将结构化输出写到 cloud watch——如果你试图解析成堆的调试日志，这非常有用！我还选择在全局空间中初始化我的 boto3 资源和表对象，在函数处理程序之外，所以我只在冷启动时招致初始化时间损失。

```
import os
import logging
import boto3

logger = logging.getLogger()
logger.setLevel(os.environ.get("LOG_LEVEL", "INFO"))

dynamodb = boto3.resource('dynamodb')
table = dynamodb.Table(os.environ["TABLE_NAME"])

def aggregation_handler(event, context):
    logger.info(event)
    for record in event['Records']:
        if record['eventName'] == "INSERT" and "user_submitted_path" in record["dynamodb"]["NewImage"]:
            #Make sure the user hasn't already reached their 12-path limit
            num_paths = len(get_recorded_paths_for(record["dynamodb"]["Keys"]["pk"]["S"]))
            if num_paths <= 12:
                #Perform Aggregations
```

在`aggregation_handler`本身(DynamoDB 流调用函数时触发的代码)中，我循环遍历 DynamoDB 将发送给我的多达 10 条记录的集合。

*注意:因为这是一个单生产者系统，我自己的代码控制着写入表中的内容，所以我并不太担心畸形的事件进入流中。但是如果我是，这段代码将需要更多的错误处理来处理记录中的意外数据。否则，当 Lambda 试图一次又一次地处理相同的记录集而失败时，流将会备份。*

在循环内部，我们首先需要对记录执行过滤检查，因为不是流中的每个记录都与我们的聚合相关。在我们的例子中，我们正在寻找新插入的包含`user_submitted_path`的记录，也就是说，我们需要将路径聚合到我们的各种度量中。

假设这是一个相关的记录，那么我们将不得不创建一个 DynamoDB `QUERY`来检索这个用户以前报告的路径的完整集合。值得注意的是，这是我们在聚合工作中唯一需要做的额外查询；所有其他信息都包含在流式记录中。查询助手函数看起来像这样:

```
def get_recorded_paths_for(user):
    response = table.query(KeyConditionExpression=Key('pk').eq(user))
    logger.info(response)
    paths = response['Items'] if 'Items' in response else []
    return paths
```

好了，现在我们有了数据，我们将按如下方式构建聚合:

```
Aggregation #1: update total paths found
                response = table.update_item(
                    Key={
                        'pk': 'AGGREGATES',
                        'sk': 'TOTAL_PATHS_FOUND'
                    },
                    ReturnValues='UPDATED_NEW',
                    UpdateExpression='ADD data_value :d',
                    ExpressionAttributeValues={':d': 1}
                )
                logger.info(response)
                #Aggregation #2: update number of players who have found this number of paths
                response = table.update_item(
                    Key={
                        'pk': 'AGGREGATES',
                        'sk': str(num_paths) + '_PATHS_FOUND'
                    },
                    ReturnValues='UPDATED_NEW',
                    UpdateExpression='ADD data_value :d',
                    ExpressionAttributeValues={':d': 1}
                )
                logger.info(response)
                #Aggregation #3: update total number of players (if necessary)
                if num_paths == 1:
                    response = table.update_item(
                        Key={
                            'pk': 'AGGREGATES',
                            'sk': 'TOTAL_PLAYERS'
                        },
                        ReturnValues='UPDATED_NEW',
                        UpdateExpression='ADD data_value :d',
                        ExpressionAttributeValues={':d': 1}
                    )
                    logger.info(response)
```

我在 DynamoDB 更新中使用了`ADD`动作，而不是通常推荐的`SET`，因为如果记录不存在，它会初始化记录——在这种情况下，这总是可取的。

如果您想知道，是的，这些更新中的每一个都会触发表上的一个变化，它本身会在流上放置一个新记录，并再次触发相同的聚合函数！现在你明白为什么把过滤器检查放在代码的顶部是如此重要了——否则我们将陷入一个无限的 Lambda 循环。

您可能想知道:将我们的聚合放在一个单独的 DynamoDB 表中是否更有意义，这样我们就不会在更新它们时触发递归流操作？ *是啊，也许吧！只要我们不认为我们需要编写一个查询来同时检索聚合数据和单个数据。*

### 检索我们的聚合

现在，从我的前端，我可以发出一个请求聚合的 API 调用，并按如下方式检索它们:

```
table.query(KeyConditionExpression=Key('pk').eq("AGGREGATES"))
```

这使得载入排行榜变得相当快–[试试看](https://adventure.acloud.guru)！如果您想知道，异步构建和更新聚合的总时间始终低于一秒，因此排行榜会像实时一样更新。

### 外卖食品

是的，这似乎是一种更复杂和脆弱的方式来构建聚合，而不仅仅是将我们的数据放在关系数据库中，并在每次加载排行榜时进行一点数学计算。但是因为总量是预先计算的，所以这个排行榜将在恒定的时间内快速加载——甚至在数百万条记录的情况下。在小规模的情况下，我的餐桌成本保持在免费层。

此外，一旦设置好 DynamoDB Streams 基础设施，添加额外聚合的工作对我来说不会比用 ORM 库将新的后端函数映射到关系数据库更糟糕。您在那里的里程可能会有所不同。

不管怎样，享受这个游戏吧，我希望排行榜的知识能让它更有趣一点！