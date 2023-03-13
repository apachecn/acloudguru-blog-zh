# MongoDB 适合我的应用吗？￼ 

> 原文：<https://acloudguru.com/blog/engineering/is-mongodb-right-for-my-application%ef%bf%bc>

好奇如何确定 MongoDB 是否适合您的应用程序？在本文中，我将描述两种不同的应用场景，并展示如何在每种场景中使用 MongoDB。在讨论了这些场景之后，我们将通过指出 MongoDB 对于每个工作负载的优缺点来结束本文。

* * *

**加速您的云计算职业生涯**

云专家让你轻松(也很棒)提升你的云事业——即使你对技术完全陌生。查看 [ACG 目前的免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)或[立即开始](https://acloudguru.com/pricing)免费试用。

* * *

## 什么是 MongoDB？

MongoDB 是一个开源的文档数据库，它具有许多企业级特性，这些特性使它适合于各种(但不是所有)应用程序。了解这些特性以及它们如何影响不同的工作负载可以帮助您确定 MongoDB 是否适合您的应用程序。

让我们探索几个场景，讨论如何在每个场景中使用 MongoDB。

## 场景一

Lisa 为一家构建 web 应用程序的互联网初创公司工作。她所在的团队精通最新的基于 web 的开发技术。他们的应用程序构建在 Node.js JavaScript 框架上。

各种各样的云平台被用来部署应用程序。该团队希望利用全球分布的节点来确保他们的数据对全球客户群高度可用。

数据的结构往往会频繁变化以满足客户的需求。为了支持这一点，所选择的数据存储将需要能够轻松更改数据模式的灵活性。

## 场景二

Sam 在一家本地制造公司工作，构建一个应用程序来管理他们的质量保证和测试程序。该公司只有一个办公地点，并且之前没有将应用程序部署到云中。他们最喜欢传统的现场部署。

Sam 使用的应用程序必须与旧的制造设备接口，因此升级到最新版本可能会很困难。

Sam 正在处理的数据集的结构没有太大的变化，而且它高度规范化了表之间的许多关系。

* * *

[![Complete guide to the Cloud and Dictionary ](img/93ebf63b88ab7fbd48705a01952ba688.png)](https://get.acloudguru.com/cloud-dictionary-of-pain)

[**获得痛苦的云词典**](https://get.acloudguru.com/cloud-dictionary-of-pain)
说云不一定要努力。我们分析了数以百万计的回复，找出了最容易让人犯错的概念。抓住这个[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)获取一些最痛苦的云术语的简洁定义。

* * *

## 如何使用 MongoDB？

上面描述的两个场景非常不同，并且举例说明了典型应用程序使用模式的不同方面。让我们看看如何在这些用例中使用 MongoDB。

在第一个场景中，Lisa 的应用程序对于 MongoDB 来说是理想的，因为该团队精通最新的基于 web 的开发技术。MongoDB 是一个 JSON 文档存储，JSON 文档格式基于 JavaScript 对象符号。用 JavaScript 编写的应用程序可以很容易地利用 MongoDB。

另一方面，场景二中 Sam 的应用程序必须利用较旧的技术来保持与制造设备的兼容性。这使得与 MongoDB 的接口变得更加困难。许多官方驱动程序都可用，但是你可能需要搜索 T2 社区支持的驱动程序来找到不知名的。

快速变化的模式和对全球分布式节点的需求使得 Lisa 的应用程序非常适合 MongoDB。通过利用 json 文档的灵活模式和全球分布的副本集或碎片，MongoDB 可以满足 Lisa 应用程序的这两种需求。

具有静态数据模式和单一位置的 Sam 应用程序不需要 MongoDB 的这些企业功能。Sam 数据集的高度相关特性也使其更难实现。通过利用嵌入式文档，可以在维护原子操作的同时表示关系。虽然在 MongoDB 中多文档事务是可能的，但这会导致性能下降，最好避免。

## 了解更多关于 MongoDB 的信息

虽然很灵活，能够满足大多数应用程序的需求，但 MongoDB 用例有一个最佳点。理解您的应用程序需求并了解可用的 MongoDB 特性有助于确保您做出最佳选择。

准备好学习更多关于 MongoDB 的知识了吗？查看我们的新课程 [MongoDB Deep Dive](https://learn.acloud.guru/course/mongo-db-deep-dive) ，更好地了解 MongoDB 中可用的特性以及如何在您的应用程序中利用它们。我们将探讨复制和分片，以及监控和备份。我们还将了解各种云供应商对 MongoDB 的支持，以及如何通过 mongosh shell 进行连接。我们将在命令行上操作文件，因此需要一些基本的 Linux 知识。熟悉文档数据库是有用的，但不是强制性的。

* * *

*想了解更多关于云计算和科技领域最热门的技能吗？[开始免费试用](https://acloudguru.com/pricing)或查看[本月免费云培训](https://acloudguru.com/blog/news/whats-free-at-acg)。你还可以[在 YouTube 上订阅一位云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每周云新闻，就像我们在[脸书](https://www.facebook.com/acloudguru)上一样，在[推特](https://twitter.com/acloudguru)上关注我们，并在[不和谐](http://discord.gg/acloudguru)上加入对话。*