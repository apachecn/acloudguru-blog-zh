# 什么是谷歌云平台(GCP)？|云专家

> 原文：<https://acloudguru.com/blog/engineering/what-is-google-cloud-platform-gcp>

你听说过 YouTube 吗？Gmail 或者谷歌地图怎么样？答案很可能是肯定的，但你可能没有听说过谷歌云平台(或 GCP)。

我们将讨论构成谷歌云的产品。我们还将涉及 [GCP 的历史](https://acloudguru.com/blog/engineering/history-google-cloud-platform)、基础设施、优势、劣势以及谷歌云平台的理想用例。我们开始吧！

什么是 GCP？

GCP 是一家公共云供应商——就像竞争对手[亚马逊网络服务(AWS)](https://acloudguru.com/blog/engineering/what-is-amazon-web-services-aws) 和[微软 Azure](https://acloudguru.com/blog/engineering/what-is-microsoft-azure) 。通过 GCP 和其他云供应商，客户可以免费或按次付费访问谷歌全球数据中心的计算机资源。

## GCP 提供一套计算服务来做一切事情，从 GCP 成本管理到数据管理，到通过网络向人工智能和机器学习工具提供网络和视频。

谷歌云 vs 谷歌云平台

谷歌云包括一系列互联网上可用的服务，可以帮助组织实现数字化。谷歌云平台(为托管基于网络的应用程序提供公共云基础设施，也是这篇博客文章的重点)是谷歌云的*部分*。

#### 谷歌云的其他一些服务包括:

Google Workspace，原名 G Suite 和 Google Apps。该产品为组织、Gmail 和协作工具提供身份管理。

Android 和 Chrome OS 的企业版。这些手机和笔记本电脑操作系统是用户连接到基于网络的应用程序的途径。

*   用于机器学习和企业地图服务的应用编程接口(API)。这些提供软件到软件的通信。

*   虽然谷歌的 GCP 云基础设施是谷歌工作场所(Google Workplace)等应用的支柱，但这些应用*并不是我们在谈论 GCP 时所谈论的*。在这篇文章中，我们主要关注谷歌云平台。

*   谷歌云平台的历史

回顾一下，让我们从 GCP 的历史开始。

## GCP 首次上线是在 2008 年，当时推出了一款名为 App Engine 的产品。2008 年 4 月，谷歌[宣布](https://googleappengine.blogspot.com/2008/04/introducing-google-app-engine-our-new.html)App Engine 的预览版，这是一个开发者工具，允许用户在谷歌基础设施上运行他们的网络应用。(从长远来看，这是在亚马逊推出其云计算服务两年后，从发布 S3 云存储和 EC2 开始。)

根据谷歌的说法，App Engine 的目标是“让一个新的网络应用程序更容易上手，然后当该应用程序达到接收大量流量并拥有数百万用户的时候，让它更容易扩展。”

为了收集改进此预览版所需的反馈，App Engine 向 10，000 名开发人员开放。这些早期采用者开发者可以运行具有 500 MB 存储空间、每天 2 亿兆 CPU 周期和每天 10 GB 带宽的应用程序。

到 2011 年底，谷歌将 App Engine 从预览模式中撤出，并使其成为正式的、完全受支持的谷歌产品。在此后的十年里，谷歌建立并收购了更多的服务和产品，以增强其云平台的用户体验。

如今，谷歌云平台是全球顶尖的公共云厂商之一。谷歌云的客户包括任天堂、易贝、UPS、家得宝、Etsy、PayPal、20 世纪福克斯和 Twitter。

谷歌云平台基础设施、地区和区域

谷歌的全球基础设施目前在全球有 24 个地点提供谷歌云平台资源。

## 位置以区域开始，区域内是可用性区域。这些区域与单点故障隔离开来。一些资源，如 HTTP 全局负载平衡器是全局的，可以接收来自任何 Google edge 位置和区域的请求。

其他资源，如存储，可以是区域性的。存储分布在一个区域内的多个分区中，以实现冗余。

最后，包括计算实例在内的分区资源仅在一个特定区域内的一个特定分区中可用。

在 GCP 上部署应用程序时，必须根据组织的性能、可靠性、可伸缩性和安全性需求来选择位置。

什么是谷歌云平台服务？

每个 GCP 地区都提供一类服务。有些服务仅限于特定地区。谷歌云平台的主要服务包括:

## 计算和托管

存储和数据库

*   建立工作关系网
*   大数据
*   机器学习
*   你可以点击查看 GCP 产品的完整列表[。](https://cloud.google.com/products)
*   [**获得痛苦的云词典**](https://get.acloudguru.com/cloud-dictionary-of-pain)
    说云不一定要努力。我们分析了数以百万计的回答，以确定哪些概念会让人犯错。抓住这个[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)获取最痛苦的云术语的简洁定义。

GCP 竞赛

* * *

谷歌拥有可与 AWS 和 Azure 相媲美的服务。AWS 处于明显的领先地位，微软正在取得进展，谷歌平台也在增长。(马上会有更多的介绍。)

* * *

## 查看我们的其他云平台概述:

*想知道不同云提供商的各个方面与 GCP 的产品相比如何吗？查看我们的概述，比较[无服务器](https://acloudguru.com/blog/engineering/serverless-showdown-aws-lambda-vs-azure-functions-vs-google-cloud-functions)、 [NoSQL 数据库](https://acloudguru.com/blog/engineering/comparing-cloud-nosql-databases-dynamodb-vs-cosmos-db-vs-cloud-datastore-and-bigtable)、 [IAM 服务](https://acloudguru.com/blog/engineering/comparing-aws-azure-and-google-cloud-iam-services)和[虚拟机(VMs)](https://acloudguru.com/blog/engineering/cloud-comparison-aws-ec2-vs-azure-virtual-machines-vs-google-compute-engine) 。*

谷歌云平台的利弊

GCP 的优势

## 谷歌是我的首选云。以我的经验，感觉就像用乐高搭建建筑。每个服务都有自己的用例，并且被设计为与下一个服务及其定义良好的参与规则一起工作。

### 说到优势，Google 云平台文档是首屈一指的。顺便说一下，阅读文件是改变职业的艺术。)人们最喜欢的是谷歌如何将动作融入 GCP 的文档中。它们分为概述部分，随后是实践部分，引导读者完成特性或服务的实现。

GCP 的另一个优势是全球骨干网络，该网络使用高级软件定义网络和边缘缓存服务来提供快速、一致和可扩展的性能。是的，顶级全球网络成本稍高，但在我看来，使用虚拟专用云(VPC)设计架构，在全球网络上自动路由流量是值得的。

*   *创建虚拟专用网络和子网是在 GCP 使用资源或任何基础设施的基础。尝试我们的动手实验室，了解如何使用 Terraform 创建一个 [Terraform VPC](https://acloudguru.com/hands-on-labs/using-terraform-to-create-a-new-vpc-and-public-subnet-in-gcp) 和公共子网。学习以代码形式创建 VPC 和基础设施子网，以便在必要时测试和启动 GCP 资源。*

*   GCP 的弱点

* * *

如果我不得不说 GCP 有一个弱点，那就是谷歌云平台提供的服务远远少于 AWS 和 Azure。

* * *

### 除此之外，GCP 对如何使用他们的云服务有一个固执的模型——这是面向软件开发人员的。

*   最主要的一点是，谷歌是在 GCP 投资，而不是寻求市场主导地位或增长。我的想法是，谷歌很难将 GCP 置于搜索、广告和 YouTube 这些更大的收入来源之上。

*   谷歌云平台用例

这里有一些理想的 GCP 场景。

## 如果你是一个大型组织，在进行项目时需要设置很多权限，谷歌有一个优秀的组织层次结构，允许你在顶层设置政策，然后忘记它。这使得部门能够快速行动，但仍然受到组织约束。

在 GCP，所有资源都属于一个特定的 GCP 项目。当该项目被删除时，所有资源都从平台上移除，从而防止留下导致成本增加的资源。

此外，还有一个很好的功能，允许项目随着时间的推移被分配到不同的计费帐户。

*   使用 GCP 的另一个理想用例是需要高级大数据、机器学习和分析优势的组织。

    企业可以将数据导入 GCP，然后对其产品的关键性能指标进行数据挖掘，或者收集客户数据，根据购买历史推荐额外的购买建议。

准备好学习 GCP 了吗？

*   下一步是什么？好吧，如果你有兴趣磨练你的谷歌云技能，并引领你的组织的未来目标，你可能会考虑[哪条 GCP 认证道路或职业道路适合你](https://acloudguru.com/blog/engineering/which-google-cloud-certification-is-best-for-me)。

## 通过我们本月的原创系列[GCP](https://acloud.guru/series/gcp-this-month)来了解谷歌云平台的所有最新消息。

如果这篇文章激起了你对谷歌云平台的兴趣，看看我们轮流推出的[免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)或[免费试用](https://acloudguru.com/pricing)，开始你的旅程！

*   **改变职业，改变企业**

学得更快。动作快点。借助 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室，立即实现转型。

* * *

## GCP 是一家公共云供应商，提供一套计算服务，从数据管理到通过网络提供 web 和视频，再到人工智能和机器学习工具。用户可以免费或按次付费使用谷歌全球数据中心的计算机资源。

谷歌云包括一系列互联网上可用的服务，可以帮助组织实现数字化。谷歌云平台为托管基于网络的应用程序提供公共云基础设施，是这篇博客文章的重点，是谷歌云的*部分*。

**What is GCP?**

GCP 首次上线是在 2008 年，当时推出了一款名为 App Engine 的产品:一款开发者工具，允许客户在谷歌基础设施上运行他们的网络应用。到 2011 年底，谷歌将 App Engine 从预览模式中撤出，并使其成为正式的、完全受支持的谷歌产品。在此后的十年里，谷歌建立并收购了更多的服务和产品，以增强其云平台的用户体验。

**What is the difference between Google Cloud and Google Cloud Platform?**

GCP 提供许多服务，但仅举几个例子:计算和托管、存储和数据库、网络、大数据和机器学习

**How did Google Cloud Platform start?**

GCP first came online in 2008 with the launch of a product called App Engine: a developer tool that allowed customers to run their web applications on Google infrastructure. By late 2011, Google pulled App Engine out of preview mode and made it an official, fully supported Google product. In the decade since, Google has built and acquired more services and products to enhance the user experience of its cloud platform.

**What are Google Cloud Platform services?**

There are many services that GCP offers, but just to name a few: Computing and hosting, Storage and database, Networking, Big Data and Machine learning