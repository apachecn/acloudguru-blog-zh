# 来自微软 Build 2022 |云专家的重大更新

> 原文：<https://acloudguru.com/blog/engineering/updates-from-microsoft-build-2022>

我怎么可能在一篇帖子中分享微软 Build 2022 的所有 Azure 精彩呢？这将会很艰难，但我必须为你…为读者做这件事！没错，这一周的 Azure 新闻都是关于微软 Build 的！

虽然我可以轻松地写几千字关于建设，我要给你一个闪电轮的公告，我最兴奋的。会有新的服务，服务变得普遍可用，甚至可能会有一些喜悦的泪水。我将尝试把这些公告分成四个关键领域:容器、DevOps 和开发者工具、AI 和 ML 以及数据。

让我们来看看新闻吧！

* * *

**通往更好职业的钥匙**

[立即开始 ACG](https://acloudguru.com/pricing) 通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室来改变你的职业生涯。

* * *

## 容器

毫不奇怪，容器是 Build 公告的关键部分。在最后一篇 Azure 更新文章中，我们报道了草案 2 的发布，但是 AKS 的声明并没有就此结束。

微软发布了一大堆声明,都是为了让更多的开发者能够将他们的应用部署到 Kubernetes 中，而不必处理太多的样板配置。作为其中的一部分，他们推出了 web 应用程序路由插件，这使得处理所有关于 DNS、证书和入口设置的配置变得更加容易。

他们还为 AKS 推出了 KEDA(或基于 Kubernetes 的事件驱动自动缩放)插件。开发者现在可以通过 KEDA 以一种完全受服务支持的方式配置缩放规则。

还有大量关于 Azure Arc 对利用混合云战略的组织的 AKS 支持的声明。

如果你认为一周的集装箱公告已经足够了，那你就错了。[我们也看到 Azure 容器应用从预览版过渡到普遍可用](https://techcommunity.microsoft.com/t5/apps-on-azure-blog/azure-container-apps-general-availability/ba-p/3416885)。我在最近一期[Cloud Builder Live](https://youtu.be/P1MzptEDmyc)中介绍过这项服务，它为开发人员提供了一条更简单的途径来将他们的容器放入云中。该服务实际上运行在 Kubernetes 上，它提供了一个自以为是的配置，去掉了大部分样板配置，同时仍然支持开源的 Kubernetes 工具，如 KEDA、Dapr 和 Envoy。

既然现在已经正式发布，您可以开始计划让它成为您生产工作负载的一部分。

老实说，各位，这是我可以喜极而泣的地方。[微软宣布了针对门户网站的更新 Azure Service Bus Explorer](https://techcommunity.microsoft.com/t5/messaging-on-azure-blog/announcing-service-bus-explorer-for-azure-portal-public-preview/ba-p/3417168) ，它将包括发送和接收消息在内的所有操作都纳入您的掌控，而无需安装任何第三方应用程序。这是我喜欢的一种更新，因为它通过将所有东西放在一个地方，使开发人员的生活变得更加轻松。它带给我快乐。

我们还看到了 API 管理和应用服务的重大更新。[对 API 管理的 GraphQL 直通支持已经发展到普遍可用](https://techcommunity.microsoft.com/t5/azure-developer-community-blog/protect-augment-and-build-graphql-apis-with-azure-api-management/ba-p/3396388)。另一个重大声明是支持解析器来创建合成的 GraphQL 服务。这一激动人心的新功能在预览版中可用。

[App 服务也增加了很多功能](https://techcommunity.microsoft.com/t5/apps-on-azure-blog/what-s-new-in-azure-app-service-at-build-2022/ba-p/3407584)。其中一个亮点是在 Azure 应用服务上利用 Linux 时对 gRPC 的支持。目前在中支持此功能。NET，但是对 Node 和 Python 的支持有望在不久的将来实现。我们还更新了网络支持和新的登录区，以帮助组织部署生产应用服务应用。

接下来，我们开始看到越来越多的开发体验直接转移到云中。虽然我们已经看到了 GitHub Codespaces 的第一阶段，但我们现在有了下一代的 Azure Dev Box。有了 preview 中的这项新服务，组织可以配置一个完整的开发环境，只需几分钟就可以启动，而不是几天的配置时间。

与 Codespaces 不同，Dev Box 运行在 Windows 上，可以为任何可以在 Windows 上运行的工具进行配置。此外，组织可以使用 Azure AD 有效地管理访问。

* * *

[**后 COVID DevOps:加速未来**](https://get.acloudguru.com/post-covid-devops-accelerating-future-webinar) COVID 如何影响甚至加速了 DevOps 最佳实践？[观看 DevOps 领导者的免费点播网络研讨会](https://get.acloudguru.com/post-covid-devops-accelerating-future-webinarhttps://get.acloudguru.com/post-covid-devops-accelerating-future-webinar)，我们将探索后 COVID 时代的 DevOps。

* * *

## **AI 和 ML**

接下来，我们有 AI 和 ML，可以毫不夸张地说，在构建过程中这里有一个巨大的重点。一个重要的公告是 OpenAI 服务的扩展，该服务自 11 月推出以来一直处于预览阶段。

这项服务是微软和 OpenAI 组织合作推出的，目标是将 OpenAI 的服务，如流行和令人兴奋的 GPT-3 模型，带给任何 Azure 开发者。在 Build 发布之后，组织现在可以申请加入预览版。此外，该服务现在支持来自 OpenAI 的额外托管模型的更多用例。

微软寻求解决的另一个挑战是帮助组织在人工智能方面负责任地创新。这是通过[新的 Azure ML Responsible AI 仪表板](https://docs.microsoft.com/en-us/azure/machine-learning/concept-responsible-ai-dashboard)实现的，该仪表板目前在预览版中可用。这个控制面板包含模型调试和业务决策的指标，以确保组织根据正确的数据采取行动。并不是所有的框架都支持所有的指标，所以请查看文档，看看这个预览版支持什么。

* * *

![why should i get azure](img/3ee87ddb6a81b5631ab6555721b8b023.png)

*想了解更多关于 Azure 认证的信息？*
*查看我们的* *[Azure 认证和学习路径。](https://acloudguru.com/azure-cloud-training)*

* * *

## 数据

最后，我们有数据，我们有很多要通过。在这个类别中，首先我们有 [CosmosDB。](https://devblogs.microsoft.com/cosmosdb/announced-at-microsoft-build-new-features-for-scalable-cost-effective-application-development/)不要担心，这一次只是好消息，在公开预览中有新功能可用。这包括突发容量，即使您暂时超出了吞吐量，您的工作负载仍能正常工作。无服务器容器容量也增加到 1TB。在如何处理包含分层分区键和分区合并的分区方面也有重大升级。

另外， [Azure SQL 让你在自己的机器上构建云应用变得更加容易。](https://techcommunity.microsoft.com/t5/azure-sql-blog/streamline-development-and-accelerate-developer-velocity-on/ba-p/3421726)如何？他们现在发布了 Azure SQL 的本地开发者体验，带有容器化的运行时和 VS 代码扩展。单单这个更新就有新闻价值，但他们也宣布了 Azure SQL ledger 的可用性，它提供了一个类似区块链的验证分类帐，但没有设置区块链环境的复杂性。

我们也不能忘记，我们中的许多人第一次可以接触到 SQL Server 2022 的[公开预览版。这个版本继续模糊 SQL Server 和 Azure 之间的界限，集成我们在以前的版本中根本没有见过。](https://cloudblogs.microsoft.com/sqlserver/2022/05/24/announcing-sql-server-2022-public-preview-azure-enabled-with-continued-performance-and-security-innovation/)

嗯，我想这就是我能塞进一个帖子的全部内容。不要忘记云永远不会变慢，所以[在 YouTube 上订阅云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每周 Azure 更新。你也可以在[脸书](https://www.facebook.com/acloudguru)上喜欢 ACG，在[推特](https://twitter.com/acloudguru)上关注我们，或者在[不和谐](https://discord.com/invite/pluralsight)上加入对话！