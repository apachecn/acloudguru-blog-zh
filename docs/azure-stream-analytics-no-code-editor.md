# Azure Stream Analytics 没有代码编辑器和 NGINX Plus，现在是 Azure native 

> 原文：<https://acloudguru.com/blog/engineering/azure-stream-analytics-no-code-editor>

在构建的前一周，Azure 为云开发者提供了许多新工具和新功能。NGINX Plus 现在是 Azure 上的原生 SaaS 产品；为你的流数据设计分析得到一个拖放式的体验，一个改进版的草稿工具使得迁移到 Kubernetes 更加容易。让我们来看看这周的 Azure 新闻都发生了什么。

* * *

**通往更好职业的钥匙**

[立即开始 ACG](https://acloudguru.com/pricing) 通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室来改变你的职业生涯。

* * *

## Azure 上的 NGINX Plus native 一个强大的组合

20 年前，NGINX 最初只是一个 web 服务器，用于处理大量并发请求，这些请求来自俄罗斯搜索引擎 Rambler，现在它已经成为世界上最受欢迎的服务器之一。

现在由 F5 组织管理，他们的旗舰产品“NGINX Plus”是一款用于管理分布式应用的常用工具。但直到现在，在 Azure 生态系统中使用 NGINX Plus 一直是一个挑战。经过两年的共同努力， [Azure 和 F5 在 Azure 上发布了 NGINX Plus](https://www.nginx.com/blog/introducing-f5-nginx-for-azure-load-balancing-available-natively-as-saas-offering-on-microsoft-azure/) 作为完整的 SaaS 产品。

这个新的 SaaS 产品不仅仅让你使用 NGINX Plus 的强大功能作为反向代理和负载平衡器。您还可以通过其 BYOC(自带配置)功能利用您的现有资产。这里最大的优势之一是，当您将工作负载迁移到云时，学习曲线会降低。您将花费更少的时间将所有东西连接在一起，并将更多的时间用于优化您的云架构和定制您的系统以满足您的独特需求。

随着 IT 世界转向分布式计算系统，这真是一个大新闻，我想你会非常喜欢使用它的。

## **构建拖放式流数据分析系统**

Azure Event Hub 服务是一个强大的实时摄取服务，在当今大规模运行并生成大量数据的物联网设备和分布式应用程序世界中，它越来越有用。然而，这些数据的价值取决于你的分析能力，Azure 刚刚发布了一个工具，通过新的 Stream Analytics no code editor 的公共预览版，使这一过程变得更加容易。

[使用其拖放界面，您可以快速创建分析作业，而无需编写任何代码](https://docs.microsoft.com/en-us/azure/stream-analytics/no-code-stream-processing)。无论您需要将数据过滤和接收到 Azure Synapse SQL 服务，将数据放入 Apache Parquet 表格并将其转储到您的数据湖，还是将数据具体化到 Azure Cosmos DB，您都可以在几分钟内开始。

这项新服务本质上为您提供了一个画布，让您可以查看所有传入的数据流，然后在将它们写入您选择的目的地之前，以您需要的任何方式对它们进行转换——所有这一切都是以无代码的方式进行的。你可以利用 Azure 的数据专家多年来积累的深厚知识，花时间思考塑造数据的最佳方式，而不是陷入设计数据查询和转换操作的语法中。

您的数据接收、转换和加载任务变得简单多了。我猜下一步是构建人工智能来告诉你数据的真正含义——但这听起来有点太像奇点了，所以希望 Azure 会推迟一段时间。

## ****使用微软草稿 2**** 轻松迁移到 Kubernetes

有效使用容器和 Kubernetes 的学习曲线可能有点艰难。2017 年，微软推出了 Draft，这是一个开源工具，可以帮助开发人员构建面向容器世界的应用程序，即使他们的技能还不太好。他们在已经使用了五年的草案中学到了很多，现在他们发布了一个重新设计的版本，名为[草案 2](https://azure.microsoft.com/en-au/updates/draft-2-an-opensource-project-for-developers-building-apps-on-kubernetes/) 。

Draft 2 工具可以让你在没有深入了解容器化概念和工件的情况下编写你的应用程序，它实际上创建了你将这些应用程序轻松部署到 Kubernetes 所需的所有工件。使用您完成的应用程序，它将制作您需要的一切:Dockerfile、Kubernetes 清单、舵图等等。为您的应用程序准备一个完善的、可工作的部署系统，您可以根据自己的特定需求进行调整，这使得向容器和 Kubernetes 的过渡更加容易。

如果您还没有深入到容器池中，这是一个很好的尝试方式——即使您已经深入到容器池中，为什么不让 Draft 2 为您做好一切，让您的工作变得简单一点呢？

## 跟上所有蓝色的事物

好了，这就是本周的全部内容！想要跟上云的所有事物？在推特上关注 ACG，关注 T2 和脸书。你还可以[在 YouTube 上订阅一位云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的 Azure 每周更新，并在 [Discord](https://discord.gg/zbvhJz66VE) 上加入对话。

想了解更多关于云和 Azure 的信息，或者想在 2022 年开始你的云计算生涯？查看我们每月更新的[免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)的轮换阵容。(不需要信用卡！)