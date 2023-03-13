# 什么是无服务器？

> 原文：<https://acloudguru.com/blog/engineering/what-is-serverless>

无服务器到底意味着什么？亚马逊网络服务、微软 Azure 和谷歌云平台提供的无服务器选项相比如何？

在这篇文章中，我们探索了无服务器和 FaaS(或功能即服务)的基础，并考察了 AWS、Azure 和 GCP 的无服务器选项。请继续阅读了解更多信息！

* * *

**加速你的职业生涯**

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

* * *

## 什么是无服务器？

当我们说“无服务器”时，我们指的是什么

无服务器是那些用于各种东西的术语之一——有些是合法的，有些是营销上的。但是，本质上，无服务器是一种设计方法，允许您构建和运行整个应用程序，而不必直接管理服务器。

是的，还有*的*服务器处于无服务器状态，但你永远不必担心它们的容量、性能、补丁或容错能力。

这对开发人员来说是一大优势，但更大的好处是可伸缩性。

有了无服务器，应用程序可以扩展和缩小，而我们根本不用做任何事情。对于传统的基于服务器的应用程序，您可能总是有一些东西在运行，以备用户需要。有了无服务器，如果你不主动使用它，就不会有处理，也不用付费。

2008 年首次推出的 Google App Engine 被许多人认为是公共无服务器产品中的 OG。事实上，在谷歌云平台出现之前就有了谷歌应用引擎(如果你好奇，可以看看我们的谷歌云平台的[历史)。它采用了按消费计量付费的定价模式，并允许用户谨慎地执行 Python 代码。](https://acloudguru.com/blog/engineering/history-google-cloud-platform)

快进到今天，无服务器已经风靡一时！

## 什么是 FaaS(作为服务的功能)？

无服务器架构的核心是功能即服务，即 FaaS。

这些服务通常是事件驱动的，所以当发生一些事情时——例如，一个 REST API 请求进来——该函数将立即采取行动，执行您为它编写的任何任务。

AWS 称他们的 FaaS 产品为 [Lambda](https://aws.amazon.com/lambda/) ，Azure 有[功能](https://azure.microsoft.com/en-au/services/functions/)，GCP 有[云功能](https://cloud.google.com/functions)。

都支持 Python、Java、Node.js、C#等主流开发语言。如果您选择的语言没有包括在内，这些服务都允许您自带运行时。尽管实现这一点的方法因提供者而异，但基本上是创建一个定制的 Docker 容器，并将 FaaS 平台配置为使用它作为运行时。

## 什么是无服务器框架？

你可能会听到人们谈论创建无服务器框架。创建几个函数对于管理和部署来说通常没什么大不了的，但是如果您试图管理一个包含数百个函数的整个应用程序，就有问题了。这就是无服务器框架发挥作用的地方。它们通常是一组实用程序，使您能够轻松管理和部署大量无服务器资源和功能。

AWS 构建了自己的框架，名为[无服务器应用模型](https://aws.amazon.com/serverless/sam/)，或 Sam，配有一只可爱的松鼠吉祥物(我们猜测它叫 SAM)。它完全是为了使用 AWS 资源而构建的，使得在 AWS 上创建和部署功能变得非常简单。

不利的一面是，它只适用于 AWS。如果你正在寻找多云兼容性，你可能想看看[无服务器框架](https://www.serverless.com/)。它支持多种云，包括 AWS、Azure 和 GCP，并且是一个非常受欢迎和文档完善的框架。

还有一些其他的框架，比如 [Zappa](https://github.com/zappa/Zappa) 、 [Apex Up](https://apex.sh/up/) 和 [Architect](https://arc.codes/docs/en/get-started/quickstart) 。有些人也使用 [Terraform](https://www.terraform.io/) 和 [Pulumi](https://www.pulumi.com/) 作为他们的无服务器平台，特别是如果他们已经使用这些作为基础设施的代码。

## 什么是编排？

拥有一个框架和一组函数固然很好，但是对于严肃的应用程序，您需要某种方式将这些函数联系在一起。我们称之为编排。如果你来自更传统的 IT 架构背景，这将是我们的中间件，让我们将离散的功能链接到一起，做我们需要它做的事情。

现在，你可以使用传统的中间件，但是云提供商有他们自己的一些工具。Azure 持久功能是 Azure 功能的一个扩展，允许你使用它所谓的编排功能和实体功能来创建有状态的工作流。GCP 推荐的无服务器编排工具是[工作流](https://cloud.google.com/workflows)，AWS 也有类似的叫做[的步骤函数](https://aws.amazon.com/step-functions/)。

## 排除故障

尽管有这些承诺，无服务器应用程序的故障诊断和调试可能是一件痛苦的事情。调试无服务器组件最常见的方法通常是在部署到云之前在本地进行调试。AWS、Azure 和 GCP 都有一套丰富的工具，允许你在本地模拟大多数组件，并让你在 IDE 中单步调试你的无服务器代码。

一旦你的无服务器应用程序出现在现实世界中，事情就变得有点棘手了。如果你在 AWS 上工作，你可以使用 [AWS X 射线](https://aws.amazon.com/xray/)来跟踪你的应用程序，以帮助查明错误或性能瓶颈。有了 GCP，你可以用[云迹](https://cloud.google.com/trace)做类似的事情。Azure 的分布式跟踪工具叫做[应用洞察](https://docs.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview)。

当然，如果你愿意，你仍然可以使用你的无服务器应用程序的日志。AWS 通过 [Amazon CloudWatch](https://aws.amazon.com/cloudwatch/) 提供这种服务，你可以在 GCP 通过[云日志](https://cloud.google.com/logging)和[错误报告](https://cloud.google.com/error-reporting)服务做同样的事情。Azure 允许你查看来自[应用服务](https://azure.microsoft.com/en-au/services/app-service/)平台的日志，或者你也可以将它们传送给应用洞察。

## 想了解更多关于无服务器的信息吗？

我们在这里只是触及了表面，但希望这能让你对 AWS、Azure 和 GCP 在无服务器方面的比较有所了解。要真正深入研究，请查看 AWS Lambda、Azure 函数和 Google Cloud 函数的更详细比较。

我们还有大量非常棒的无服务器培训内容和动手实验，以下是我们的一些建议！

* * *

[**获得痛苦的云词典**](https://get.acloudguru.com/cloud-dictionary-of-pain)
说云不一定要努力。我们分析了数以百万计的回复，找出了最容易让人犯错的概念。抓住这个[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)获取一些最痛苦的云术语的简洁定义。