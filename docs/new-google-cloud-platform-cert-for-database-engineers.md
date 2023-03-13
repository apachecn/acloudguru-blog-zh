# 面向数据库工程师的新谷歌云平台证书

> 原文：<https://acloudguru.com/blog/engineering/new-google-cloud-platform-cert-for-database-engineers>

谷歌云平台[本月](https://acloud.guru/series/gcp-this-month/view/404)有什么新消息？我们获得了针对数据库工程师的 Google Cloud 认证(测试版)和新产品 BigLake，帮助管理 GCP、AWS 和 Azure 的数据湖和数据仓库。我们还将了解云扳手、GCE(谷歌计算引擎)虚拟机暂停、媒体 CDN 以及即将举行的谷歌安全和机器学习峰会的更新。我们走吧！

* * *

**通往更好职业的钥匙**

[立即开始 ACG](https://acloudguru.com/pricing) 通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室来改变你的职业生涯。

* * *

## 专业云数据库工程师测试版

如果你在谷歌云平台中使用结构化数据，或者如果你想，那么你可能会对谷歌新的专业云数据库工程师认证感兴趣，目前正在测试中。

[正如谷歌所描述的](https://cloud.google.com/certification/cloud-database-engineer)，具有这种资格的人“设计、创建、管理应用程序用来存储和检索数据的谷歌云数据库，并对其进行故障排除”。他们“应该能够轻松地将业务和技术需求转化为可扩展且经济高效的数据库解决方案”。

测试版考试现在的费用比它全面上市时要低，而且你可能会因为参与而获得一些独家赠品。代价是考试时间更长(四个小时！)而且你可能要几个月才能得到结果。

* * *

* * *

## GCE 虚拟机现在暂停正式发布

如果你仍然在直接使用虚拟机，而不是更高级的服务，那么 GCP 的最新消息可能会让你感兴趣:你现在可以通过 ACPI·S3 信号[暂停和恢复计算引擎实例](https://cloud.google.com/blog/products/compute/save-by-suspending-vms-on-google-compute-engine)！当实例处于暂停状态时，您可以为高级操作系统许可证支付更少的费用，并且您根本不需要为内核和 RAM 付费。你*将*仍然必须为实例内存支付存储成本。

这方面的一个用例是预热一些启动缓慢的实例，以便稍后可以使用它们进行扩展。谷歌声称，他们的方法比其他云的工作方式有一些优势，但他们可能也忘记了，自 2018 年[以来，其他一些云已经允许你这样做了。哎呀！](https://aws.amazon.com/blogs/aws/new-hibernate-your-ec2-instances/)

## 即将举行的安全和应用 ML 谷歌云平台在线峰会

标记你的日历，因为谷歌将在 5 月 17 日举办一个安全峰会，在 6 月 9 日举办一个应用 ML 峰会，这两个峰会都是在线的。我们都对安全负责，机器学习只有在我们能够有效地应用它来解决问题时才对我们有好处，所以这两天可以为你提供有价值的见解，并帮助你取得有意义的进展。

## 改进的语音转文本(STT)人工智能

谷歌云平台在通过他们的 STT API 将语音转换为文本方面已经非常棒了，但它刚刚变得更好。最新款以一些新的标签提供给我们。“最近的短”标签是针对那些被调整到像语音命令这样的短短语的模型，而“最近的长”是针对更长形式的演讲，比如[这个博客的视频版本](https://learn.acloud.guru/series/gcp-this-month/view/404)！我们用它写了这篇文章吗？你永远不会知道！

鉴于 YouTube 在处理大规模视频方面相当不错，很高兴看到[谷歌的新媒体 CDN 服务](https://cloud.google.com/blog/products/networking/introducing-media-cdn)，已经普遍可用，将让我们利用 YouTube 用于以非常低的延迟在全球提供视频的相同技术。无需您付出任何努力，它就支持 HTTP/3、TLS 1.3 和 BBR 拥塞控制。

## 云扳手改变流即将推出

Cloud Spanner 是 Google 的全球和无限可扩展的关系数据库，但它不是您想要拥有数据的唯一地方。这就是为什么即将推出的[云扳手改变流功能](https://cloud.google.com/blog/products/databases/track-and-integrate-change-data-with-spanner-change-streams)会如此有趣。

首先，您可以使用它将 Cloud Spanner 数据复制到其他各种存储中，比如 BigQuery 或云存储。你也可以通过类似数据流的东西来处理数据变化对依赖系统的影响，或者用 PubSub 触发任何你想要的东西。如果您只关心一些更改，您甚至可以按表或列进行过滤。

值得庆幸的是，这不需要任何额外的基础设施-您只需打开它，您现有的云扳手实例就能满足您的需求！

* * *

## 新的 BigLake 产品统一了跨云的数据湖和数据仓库

最近宣布， [BigLake](https://cloud.google.com/blog/products/data-analytics/unifying-data-lakes-and-data-warehouses-across-clouds-with-biglake) 是谷歌的新产品，用于管理 GCP、AWS 和 Azure 的数据湖和数据仓库。谷歌认识到，除了基于 GCP 的数据之外，组织可能在 Azure 和 AWS 上都有大量数据，他们希望在一个地方一致地管理和利用这些数据。

因此，数据可能会以 Parquet 或 ORC 等开放格式存储在 S3 或 GCS 或 Azure Blob 上，然后开发人员和数据分析师只需与 BigLake 打交道。顺便说一下，这更安全，因为最小特权不包括任何原始数据。然后，BigLake 会将这些查询外包给 GCP 的 BigQuery，以及 AWS 和 Azure 的 BigQuery Omni。

### 获得更多的 GCP 新闻善良在你身上！

想了解所有 GCP 新闻吗？在推特[上关注 ACG](https://twitter.com/acloudguru)和[脸书](https://www.facebook.com/acloudguru)，[在 YouTube](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1) 上订阅一位云专家的 GCP 每月更新，并在 [Discord](http://discord.gg/acloudguru) 上加入对话。

想了解更多关于云和 GCP 的信息吗？查看我们每月更新的[免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)的轮换阵容。(不需要信用卡！)