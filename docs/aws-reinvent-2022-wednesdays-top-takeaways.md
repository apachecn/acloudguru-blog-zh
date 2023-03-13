# AWS re:Invent 2022:周三的顶级外卖

> 原文：<https://acloudguru.com/blog/engineering/aws-reinvent-2022-wednesdays-top-takeaways>

周一，我们得到了令人兴奋的消息，λ寒冷开始成为过去，周二[发布了一大堆公告](https://acloudguru.com/blog/engineering/aws-reinvent-2022-tuesdays-top-7-takeaways)。那么周三要带什么呢？以下是你需要知道的关于 re:Invent 2022 第三天发生的事情！

## 关于机器学习还有很多要学

今天，AWS 负责数据库、分析和机器学习的副总裁 Swami Sivasubramanian 博士[走上了舞台](https://acloudguru.com/blog/engineering/aws-reinvent-2022-swami-keynote)。在首席执行官[亚当·塞利普斯基昨天的主题演讲](https://acloudguru.com/blog/engineering/reinvent-adam-selipsky-keynote)之后，我们迫不及待地想听听他要说些什么！

Sivasubramanian 博士首先谈到我们如何需要一个面向未来的数据基础，一个我们不需要不断重新架构的数据基础。他强调，没有为明天构建的战略，企业将失去竞争优势，并重申我们应该让 AWS“移除无差别的重担”。他的演讲还呼吁在我们的组织中编织结缔组织，并通过工具和教育使数据民主化。

主题演讲的主题是“数据是极其强大的”，他用几种富有诗意的方式将这一理念贯穿于他的主题演讲中。用蜘蛛侠的话说，权力越大，责任越大，这意味着安全。那么，让我们开始宣布吧。

## 新的 pagemaker ml 治理功能

融入这个责任主题的是新的 [SageMaker ML 治理特性](https://aws.amazon.com/blogs/aws/new-ml-governance-tools-for-amazon-sagemaker-simplify-access-control-and-enhance-transparency-over-your-ml-projects/)，它帮助你掌控你的机器学习模型。其中包括亚马逊 SageMaker 角色管理器、亚马逊 SageMaker 模型卡和亚马逊 SageMaker 模型仪表板。“亚马逊 SageMaker”命名真多！

除了 AWS GovCloud 和 AWS 中国地区，所有这些[现在都可以在亚马逊 SageMaker 可用的所有 AWS 地区免费获得](https://aws.amazon.com/sagemaker/ml-governance)。

## 现在，您可以使用 Data Wrangler 从更多数据源中提取数据

说到 SageMaker，SageMaker Data Wrangler 现在[支持超过 40 个数据源](https://aws.amazon.com/blogs/aws/new-amazon-sagemaker-data-wrangler-supports-saas-applications-as-data-sources/)。它使用与 AppFlow 集成的机器学习数据源。这意味着现在从 40 多个第三方 SaaS 应用来源(包括 Salesforce 和 Google Analytics)聚合数据比以往任何时候都更容易，所以你最好开始争论吧！

## Amazon Athena for Apache Spark 现已上市

雅典娜很酷——服务和希腊神都很酷——如果你不知道前者，你应该[阅读诺琳·哈桑关于服务的优秀介绍文章](https://acloudguru.com/blog/engineering/amazon-athena-explained-what-is-it-and-when-should-i-use-it)(如果你需要了解后者，请查看维基百科)。现在，你[可以使用 Jupyter 笔记本](https://aws.amazon.com/blogs/aws/new-amazon-athena-for-apache-spark/)作为接口运行 Apache Spark 工作负载。您可以在 Athena 上执行数据处理，并使用 Athena APIs 与 spark 应用程序进行交互。

## 亚马逊红移现在支持从 S3 自动复制

转向零 ETL(即:提取、转换、加载)，Amazon Redshift 的[新的 S3 自动复制功能](https://aws.amazon.com/about-aws/whats-new/2022/11/amazon-redshift-supports-auto-copy-amazon-s3/)将肯定有助于实现我们知道 AWS 正在努力实现的零 ETL。

## 加入预览:粘合数据质量，验证访问

预览是伟大的，这里有两个值得一试: [AWS 胶水数据质量](https://aws.amazon.com/blogs/aws/join-the-preview-aws-glue-data-quality/)和 [AWS 验证访问](https://aws.amazon.com/blogs/aws/aws-verified-access-preview-vpn-less-secure-network-access-to-corporate-applications/)。

**AWS Glue Data Quality** 是一款自动测量和监控您的数据湖、分析您的数据并收集统计数据的工具。然后，它会推荐数据质量规则，您也可以添加自己的规则。这有助于防止您污染数据湖，将它变成数据沼泽。

**AWS 验证访问**是一种保护企业应用程序网络访问安全的无 VPN 方式。这是为了实现“零信任”网络——有时也被称为 beyond corp——这项服务似乎是亚马逊对谷歌身份感知代理的回应。

## Amazon AppFlow 的更多连接器

我感觉到了一种联系，这种联系就是与 AppFlow 的联系。[亚马逊 AppFlow](https://aws.amazon.com/blogs/aws/announcing-additional-data-connectors-for-amazon-appflow/) 宣布发布 22 个新的数据连接器，现在 AppFlow 支持超过 50 个应用。这使您可以在 SaaS 应用程序和亚马逊 S3 和红移之间安全地传输数据。你现在可以为脸书广告、Mailchimp、微软团队等等建立数据流。

## amazon pagemaker 现在支持地理空间 ml

是的，你听到了。这意味着使用[地理空间数据](https://aws.amazon.com/blogs/aws/preview-use-amazon-sagemaker-to-build-train-and-deploy-ml-models-using-geospatial-data/)轻松构建、训练和部署机器学习模型。它还包括内置的 3D 可视化和神经地图！

## 第三天到此为止！

请继续关注《re:Invent 2022》的更多新闻。一如既往地保持敬畏，云大师们！

* * *

## 跟随所有关于“重新发明 2022”的报道

查看 [ACG 和 Pluralsight re:Invent 内容中心](https://www.pluralsight.com/reinvent-2022)以了解 re:Invent 2022 的所有信息。

你也可以在推特[和](https://twitter.com/acloudguru)[上关注 ACG](https://www.facebook.com/acloudguru)和【脸书】上关注，在 YouTube 上订阅云专家[上所有你能处理的关于 re:Invent 2022 的更新！](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)

加入我们令人敬畏的 [Discord 社区](https://discord.com/invite/acloudguru),与 AWS 培训架构师和其他志趣相投的阴云密布的人进行数字交流。