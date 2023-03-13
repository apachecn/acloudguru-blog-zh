# 初次接触 Azure，经验丰富。网？试试这 5 种 Azure 服务|云专家

> 原文：<https://acloudguru.com/blog/engineering/new-to-azure-and-experienced-with-net-try-these-5-azure-services>

任何成功的现代技术体系都会解决数据管理、计算、安全和监控的问题。维护这些的挑战性部分从成本到配置各不相同，浪费了宝贵的资源:时间和金钱。有了经济高效且可靠的云计算，这些问题中的一些变得不那么令人担忧了。

随着世界上令人激动的变化。NET 生态系统，有相当多的东西开发者可以得到。对于云来说也是如此，特别是 Azure，它一直为。网络开发。

* * *

* * *

## 5 Azure 服务。NET 开发人员

如果你不熟悉 Azure，并且对它的好处感到好奇。NET 开发，这里有五个有用的服务，你应该尝试一下。选择这些服务是因为它们的易用性、丰富的工具以及. NET 技术堆栈中的共同点。

![](img/16ec18d86f4e167d324f866a9972ecb6.png)

*Accessing blobs in Azure Storage Explorer*

### 1.Azure 存储

Azure 存储帐户是一个与大量服务一起使用的公共服务，所以你很可能会在使用 Azure 时与它进行交互。存储帐户的独特之处在于，它是一项服务，可用于多种用途。您可以使用 Blob 服务和数据湖存储和访问各种类型的文件，使用文件服务创建文件共享，以及使用队列与本地系统和/或服务进行通信。

在本地机器上使用存储有很多选择，从带有 Azure Storage Explorer 的独立 UI，或者作为 Visual Studio 或 Visual Studio 代码中的扩展集成到开发环境中。这些工具的设置非常简单:只需要你通过浏览器验证你的 Azure 账户。的 Azure 存储客户端库。NET 为与存储帐户中所有可用存储选项的交互提供同步和异步支持。

* * *

![](img/593de2f02fbe2d09fb867a3717f01afa.png)

*What do the pros steeped in Azure and serverless think about where it’s at today? Read our [Q&A on the state of Azure serverless](https://acloudguru.com/blog/engineering/qa-the-state-of-azure-serverless).*

* * *

### 2.Azure 函数

你很可能已经遇到了无服务器的概念。这消除了管理基础架构的需要，使您能够专注于构建而不是配置。Azure Functions 是 Azure 中无服务器选项的流行选择。为什么？有许多方法可以开始，它有一个[成本效益的定价结构](https://azure.microsoft.com/en-us/pricing/calculator/?service=functions)。

![](img/dfab0ffb7e87618a6a88c2f1a1c7cb37.png)

*The Azure Functions and Web Jobs Tools Extension in Visual Studio*

无服务器函数涉及触发事件驱动的代码来运行和响应事件，但是是无状态的，并且不知道来自先前执行的值。然而，使用[持久函数](https://docs.microsoft.com/en-us/azure/azure-functions/durable/durable-functions-overview?tabs=csharp&WT.mc_id=dotnet-13637-jasmineg)，您可以使用 orchestrator 函数编写有状态的无服务器应用程序，以编程方式管理执行，使用实体函数管理状态。

有一组丰富的工具可用于功能开发、调试、部署和测试，这些都可以在本地或 Azure 门户中完成。你可以通过命令行用 [Azure Function Core Tools](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local?WT.mc_id=dotnet-13637-jasmineg) 使用函数，或者在你的编辑器中用 Visual Studio 或者 Visual Studio 代码使用函数。函数的本地工具不需要 Azure，所以在发布到 Azure 之前，你可以在你的机器上构建一个完整的无服务器应用。

* * *

![How to build a Serverless app using Go and Azure Functions](img/d27779a5ebbf16a3f320fef4a61fc4bf.png)

*With the arrival of Azure Functions Custom Handlers, you can use Go for serverless functions on Azure. Read our [how-to guide on using Custom Handlers](https://acloudguru.com/blog/engineering/how-to-build-a-serverless-app-using-go-and-azure-functions).*

* * *

### 3.Azure SQL & Azure SQL 托管实例

如果你对 SQL Server 的新功能感到好奇，可以考虑探索一下 [Azure SQL 数据库](https://docs.microsoft.com/en-us/azure/azure-sql/database/sql-database-paas-overview?WT.mc_id=dotnet-13637-jasmineg)。Azure SQL 基于 SQL Server 数据库引擎的最新稳定版本，SQL Server 的新特性首先应用于 Azure SQL。

考虑迁移？ [Azure SQL 托管实例](https://docs.microsoft.com/en-us/azure/azure-sql/managed-instance/sql-managed-instance-paas-overview?WT.mc_id=dotnet-13637-jasmineg)除了利用 [Azure 混合优势](https://azure.microsoft.com/en-us/pricing/hybrid-benefit/?WT.mc_id=dotnet-13637-jasmineg)之外，还设计用于将 SQL Server 和任何额外的本地应用和服务迁移到 Azure。如果你在 SQL Server 上使用 Entity Framework，Azure SQL 的体验实际上是相同的。

Azure SQL 和 SQL 托管实例配备了大量自动化任务和监控关键事件的功能。他们的完全托管架构可自动进行修补、更新和备份，因此您可以专注于产品的开发，而像[自动调优](https://docs.microsoft.com/en-us/azure/azure-sql/database/automatic-tuning-overview?WT.mc_id=dotnet-13637-jasmineg)和[智能洞察](https://docs.microsoft.com/en-us/azure/azure-sql/database/intelligent-insights-overview?WT.mc_id=dotnet-13637-jasmineg)这样的功能可帮助您的数据库保持最佳性能。

### 4.蓝色钥匙保险库

[Azure Key Vault](https://docs.microsoft.com/en-us/azure/key-vault/general/overview?WT.mc_id=dotnet-13637-jasmineg) 提供了一种集中应用程序机密、密钥和证书的方式，并提供了监控和控制用户和应用程序访问的能力。它消除了在代码中包含关键信息的需要，从而减少了泄漏关键信息的机会。相反，应用程序可以通过 URI 检索机密，并且在检索之前必须通过身份验证和授权。

如果你是一个 Visual Studio 用户，使用[Visual Studio Connected Services](https://docs.microsoft.com/en-us/azure/key-vault/general/vs-key-vault-add-connected-service)可以简化向你的 ASP.NET 应用程序添加密钥库。Connected Services 添加所需的 NuGet 包，并配置您与 Azure 和密钥库的连接。如果您在 Visual Studio 中构建桌面应用程序，则可以使用密钥库为 UWP 和桌面应用程序的包签名。

* * *

![Which Azure service should I use for my web app?](img/576bcf8ae463e11a4a8bf0f20eb9d7d5.png)

*New to developing cloud-based web apps? See which [Azure service you should use to host your web app](https://acloudguru.com/blog/engineering/which-azure-service-should-i-use-to-host-my-web-app).*

* * *

### 5.Azure Monitor 和应用洞察

Azure Monitor 主要用于遥测，可以针对云和内部环境进行配置。它是一个中心位置，用于收集指标和日志、观察性能以及识别应用程序和基础架构中的问题及其依赖关系。

Application Insights 是 Azure Monitor 中的一项功能，用于监控实时应用程序及其附带的指标和日志。Application Insights 中的一项独特功能，专属于。NET development environments 的[快照调试器](https://docs.microsoft.com/en-us/azure/azure-monitor/app/snapshot-debugger)，它捕捉异常发生时源代码的状态。这些捕获称为快照，可以在 Azure 门户或 Visual Studio 中进行深入检查。

如果您正在探索或评估 Azure，如果您有兴趣以最少的设置使用云，Application Insights 是一个完美的起点。[入门](https://docs.microsoft.com/en-us/azure/azure-monitor/app/asp-net-core)包括创建云服务来收集工具密钥，安装 NuGet 包，并将密钥添加到您的项目中。

![](img/0e7888f7d139449d900565426ff560ad.png)

*Snapshot debugger inspecting the snapshot of a live application hosted in Azure*

### 后续步骤

对今天的有极好的支持。NET 开发者使用 Azure——因为它是用。NET 开发人员的想法。只需添加其中一项服务，即可通过广泛且记录完善的 API、详细的监控以及与您已经熟悉并喜欢的工具和工作流的无缝集成，增强您的云开发体验。

有兴趣开始使用 Azure 吗？[注册一个帐户](https://azure.microsoft.com/free/?WT.mc_id=dotnet-13637-jasmineg)和[阅读这个文档](https://docs.microsoft.com/en-us/dotnet/azure/intro?WT.mc_id=dotnet-13637-jasmineg#application-development-scenarios-on-azure)关于如何将它集成到您的环境中——以及关于的[关键 Azure 服务。NET 开发者](https://docs.microsoft.com/en-us/dotnet/azure/key-azure-services?WT.mc_id=dotnet-13637-jasmineg)。如果你对 Azure 有经验，并准备好计划你的迁移，浏览 Azure 架构文档。

* * *

## **提升你的 Azure 技能**

这是学习微软 Azure 技能的最佳时机。到二月底，ACG 将提供一系列免费的云课程，包括非常受欢迎的 T2 AZ-900 Azure 基础课程 T3。

* * *

#### 关于作者

贾斯敏·格林纳威 *是一名纽约的开发人员，也是微软的云倡导者。通过文字和代码，她用 Azure 展示了开发人员可以利用云做的了不起的事情。她多年的开发经验使她经历了不同的开发环境和行业，如西尔斯的零售，Rockstar Games 的游戏，以及之前的微软。NET 开发工具，在 GitHub 担任软件工程师。她还在纽约市担任兼职讲师，教授 web 开发的基础知识。*