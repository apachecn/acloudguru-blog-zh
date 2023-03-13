# 如何使用 AWS |云专家跟踪、分析和可视化数据

> 原文：<https://acloudguru.com/blog/engineering/how-to-track-analyze-and-visualize-user-group-data-using-aws>

*在本帖中，我们将讨论如何使用亚马逊定位服务对地址进行地理编码，如何使用亚马逊 EventBridge 和 AWS Lambda 每天将数据转换和加载到 S3，如何使用亚马逊 QuickSight 可视化和共享存储的数据，以及如何使用 SAM 自动化和协调整个解决方案*

## *使用 AWS 了解用户群数据的趋势*

新冠肺炎疫情已经将许多面对面的社区聚会转变为虚拟活动。发表在《应用心理学杂志》上的新研究表明，在虚拟会议、聚会和社交活动的时代，“变焦疲劳”是真实存在的。

社区总是询问支持用户组的方法。为此，我一直在寻找一种快速、有效、可靠的方法来分析用户组数据，并将其可视化到仪表板中。该解决方案有助于以多种方式获得洞察力:

*   **跟踪活跃的会议:**了解哪些用户组在过去 12 个月、6 个月或 3 个月一直活跃。

*   **可视化成员的位置:**使用地图查看我们团队的位置，以及他们的足迹有多大。

*   **跟踪事件:**使用一个按最后事件时间戳排序的表，查看哪些组最近发生了事件

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## 解决方案概述

这篇文章描述了我是如何构建这个解决方案的，从地理编码地址数据到在亚马逊 QuickSight 上的最终可视化。

在这个解决方案中，我从开发 Python 代码开始，从 [Meetup](http://www.meetup.com/) 收集用户组数据。

为了在地图上标出每次聚会，需要地理位置数据。我使用亚马逊定位服务将地址地理编码为经度和纬度坐标。

然后，转换后的数据被发布到一个[亚马逊简单存储服务](http://aws.amazon.com/s3)(亚马逊 S3)桶中。

我使用 Amazon EventBridge 设置了一个每日作业来触发一个 lambda 函数来收集用户组数据。报告和可视化层是使用 [QuickSight](https://acloudguru.com/blog/engineering/amazon-quicksight-how-to-put-eyes-on-your-data-with-this-aws-bi-tool) 构建的。最后，使用 AWS SAM 部署整个管道。

下图说明了这种体系结构。

### 收集用户组数据

AWS 用户组是定期聚会以分享想法、回答问题并了解新服务和最佳实践的社区。用户组使用 meetup.com 组织他们的活动。我对美洲页面的[用户组中列出的加拿大和美国的用户组很好奇。](https://aws.amazon.com/developer/community/usergroups/americas/)

我使用了`BeautifulSoup`和 requests 库从 AWS 用户组网站抓取内容。

该脚本首先通过`get_user_group_data`函数获取每个用户组的 meetup URL。基于某些 div 属性的存在，它将相关的 meetup URL 和名称存储在一个要废弃的列表中。

接下来，`get_meetup_info`函数遍历列表并解析每个 meetup 页面上的信息，比如成员数量和 meetup 位置。原始数据保存为 CSV 格式，以便进一步处理。

本文中的解决方案仅用于演示目的。我们建议在与管理这些脚本的团队协商后，仅在您自己的网站上运行类似的脚本，或者确保遵守您试图抓取的网站的服务条款。

下面显示了该脚本的一个示例。

```
meetup_json = {}
	page = requests.get(meetup_url)
	usergroup_html = page.text
	soup = BeautifulSoup(usergroup_html, "html.parser")

	# Get Meetup Name
	meetup_name = soup.findAll("a", {"class": "groupHomeHeader-groupNameLink"})[0].text

	# Meetup location
	meetup_location = soup.findAll("a", {"class": "groupHomeHeaderInfo-cityLink"})[
    	0
	].text

	# Number of members
	meetup_members = (
    	soup.findAll("a", {"class": "groupHomeHeaderInfo-memberLink"})[0]
    	.text.split(" ")[0]
    	.replace(",", "")
	)

	# Past events
	past_events = (
    	soup.findAll("h3", {"class": "text--sectionTitle text--bold padding--bottom"})[
        	0
    	]
    	.text.split("Past events ")[1]
    	.replace("(", "")
    	.replace(")", "")
	)
```

### 地理编码用户组

为了在地图上绘制每个 meetup 组，我们需要 meetup 组中每个城市的经度和纬度。我可以使用亚马逊定位服务，通过地点索引将每个城市的名称地理编码成经度和纬度坐标。有关创建地点索引的更多信息，请参见[亚马逊位置服务开发者指南](https://docs.aws.amazon.com/location/latest/developerguide/places-prerequisites.html)。

以下是使用地点索引进行地理编码的示例 Python 代码。

```
import boto3

def get_location_data(location: str):
	"""
	Purpose:
    	get location data from name
	Args:
    	location - name of location
	Returns:
    	lat, lng -  latitude and longitude of location
	"""
	client = boto3.client("location")
	response = client.search_place_index_for_text(
    	IndexName="my_place_index", Text=location
	)

	print(response)
	geo_data = response["Results"][0]["Place"]["Geometry"]["Point"]

	#  Example output for Arlington, VA:   'Results': [{'Place': {'Country': 'USA', 'Geometry': {'Point': [-77.08628999999996, 38.89050000000003]}, 'Label': 'Arlington, VA, USA', 'Municipality': 'Arlington', 'Region': 'Virginia', 'SubRegion': 'Arlington County'}}
	lat = geo_data[1]
	lng = geo_data[0]

	print(f"{lat},{lng}")

	return lat, lng 
```

### 使用 SAM 来协调部署

在本地测试脚本之后，下一步是创建一个机制来每天运行脚本并将结果存储在 S3。我使用 AWS 无服务器应用程序模型(SAM)创建了一个无服务器应用程序，它执行以下操作。

1.  创建 S3 存储桶
2.  创建每 24 小时触发一次的 CloudWatch 事件
3.  部署 Python lambda 函数来运行数据抓取代码

下面是用于部署无服务器应用程序的大纲，突出显示了我使用的示例代码。

**1。从终端窗口，初始化一个新的应用**
`sam init`

**2。更改目录:** `cd ./sam-meetup`

**3。**更新依赖关系
*更新 my_app/requirements.txt

`requests`
`pandas`


**4。更新代码**
将您的代码添加到示例` my_app/app.py `中

```
import json
import logging

import get_meetup_data

def lambda_handler(event, context):

	logging.info("Getting meetup data")

	try:
    	get_meetup_data.main()
	except Exception as error:
    	logging.error(error)
    	raise error

	return {
    	"statusCode": 200,
    	"body": json.dumps(
        	{
            	"message": "meetup data collected",
        	}
    	),
	}
```

**5。更新模板. yml〔t1〕**

```
Globals:
  Function:
	Timeout: 600
Resources:
  S3Bucket:
	Type: 'AWS::S3::Bucket'
	Properties:
  	BucketName: MY_BUCKET_NAME
  GetMeetupDataFunction:
	Type: AWS::Serverless::Function
	Properties:
  	CodeUri: my_app/
  	Handler: app.lambda_handler
  	Policies:
    	- S3WritePolicy:
        	BucketName: MY_BUCKET_NAME
  	Runtime: python3.9
  	Architectures:
    	- x86_64
  	Events:
    	GetMeetupData:
      	Type: Schedule
      	Properties:
        	Schedule: 'rate(24 hours)'
        	Name: MeetupData
        	Description: getMeetupData
        	Enabled: True
```

**6。跑``sam build` `**

**7。将应用程序部署到 AWS** `sam deploy --guided`

有关开发 SAM 应用程序的更多详细信息，请查看[AWS SAM 入门](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-getting-started.html)。

* * *

[**自动化 AWS 成本优化**](https://go.acloudguru.com/AWS-Cost-Optimization-Webinar)
AWS 为您的企业提供了前所未有的价值，但经济高效地使用它可能是一项挑战。在这个[免费点播的网络研讨会](https://go.acloudguru.com/AWS-Cost-Optimization-Webinar)中，您将了解 AWS 成本优化工具和策略的概况。

* * *

## 使用 QuickSight 可视化数据

为了共享用户组数据，我选择使用亚马逊 S3 的 [QuickSight](https://acloudguru.com/blog/engineering/amazon-quicksight-how-to-put-eyes-on-your-data-with-this-aws-bi-tool) 作为数据源。

QuickSight 是一项原生 AWS 服务，可与其他 AWS 服务无缝集成，如亚马逊红移、雅典娜、亚马逊 S3 和许多其他数据源。

作为一项完全托管的服务，QuickSight 使团队能够轻松创建和发布交互式仪表盘。除了构建强大的可视化功能，QuickSight 还提供了数据准备工具，可以轻松过滤数据并将其转换为所需的数据集。有关创建数据集的更多信息，请参见[使用亚马逊 S3 文件创建数据集](https://docs.aws.amazon.com/quicksight/latest/user/create-a-data-set-s3.html)。

以下是仪表板的屏幕截图示例。

* * *

*参加 [Amazon QuickSight 速成班，学习如何使用这款 AWS BI 工具](https://acloudguru.com/blog/engineering/amazon-quicksight-how-to-put-eyes-on-your-data-with-this-aws-bi-tool)* 查看您的数据。

* * *

### 结论

在本帖中，我们讨论了如何成功实现以下目标:

*   使用亚马逊定位服务对地址进行地理编码
*   使用 Amazon EventBridge 和 AWS Lambda 每天将数据转换并加载到 S3
*   使用 Amazon QuickSight 可视化和共享存储的数据
*   使用 SAM 自动化和协调整个解决方案

该解决方案可用于深入了解与技术社区的互动。如果你有兴趣加入当地社区，请点击这里查看 AWS 用户组页面。

#### **关于作者**

Banjo 是 AWS 的一名高级开发人员，他在那里帮助开发人员对使用 AWS 感到兴奋。Banjo 热衷于将数据操作化，并围绕利用数据启动了一个播客、一个 meetup 和开源项目。当没有建造下一个大东西时，Banjo 喜欢通过玩视频游戏特别是 JRPGs 和探索他周围发生的事件来放松。