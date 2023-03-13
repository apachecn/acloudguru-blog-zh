# 十月新闻综述:Azure 有什么新特性？

> 原文：<https://acloudguru.com/blog/engineering/october-news-roundup-whats-new-with-azure>

你好，云大师！想知道 Azure 在过去的一个月里发生了什么变化，但没有时间查看标题？我们已经写了一篇文章，提供了你需要知道的所有信息。

## 微软 Ignite！

上个月微软 Ignite 2022 最大的变化是。我们被赋予了多种公告，预览，气体和更多。我们采访了[在当地的初步印象](https://youtu.be/639WV-ODh3I)，以及[的事后总结](https://youtu.be/9dEa5kfPCFg)。所以让我们跳到下面最重要的事情。

另外，如果你对基础设施公告更感兴趣，Wayne Hoggett 已经有了一个很棒的博客综述，你可以在这里找到。

## 库伯内特新闻

Azure 不缺 Kubernetes 新闻！这一领域最大的公告之一是宣布使用 Azure Arc 的 [Azure Kubernetes 服务的混合部署选项。现在，采用混合策略的组织既可以部署到云中，也可以部署到他们自己的支持 Azure-Arc 的数据中心，同时使用您当前用来管理 AKS 集群的所有 Azure 工具维护单点管理。](https://techcommunity.microsoft.com/t5/azure-stack-blog/what-s-new-for-azure-stack-hci-at-microsoft-ignite-2022/ba-p/3650949)

在节点限制方面，如果您对 AKS 使用正常运行时间-SLA SKU，您现在可以将 1，000 个节点的旧限制乘以 5 倍。对于那些数学很快的人来说，这确实意味着[您的 AKS 集群](https://azure.microsoft.com/en-us/updates/generally-available-5000-node-scale-in-aks/)中可以有多达 5000 个节点。

新服务 [Kubernetes Fleet Manager](https://azure.microsoft.com/en-us/products/kubernetes-fleet-manager/#overview) 使跨多个地区管理多个 AKS 集群变得更加容易，该服务目前处于预览阶段。有了这个新的工具集，您现在可以集中管理和配置多个集群，同时还增加了跨集群对一些工作负载进行负载平衡的能力。

## Azure 存储新闻

Ignite 发布了两个激动人心的存储产品，而不是一个。首先，我们在预览版中推出了新的存储服务！根据微软的说法， [Azure Elastic SAN](https://techcommunity.microsoft.com/t5/azure-storage-blog/azure-elastic-san-in-preview/ba-p/3643414) 是“业界第一个完全托管的云中存储区域网络产品”。

这项服务承诺，它将从我们自己的数据中心汇集我们喜爱的 SAN 功能，并通过真正的云原生服务实现这一点。除了所有这些，您还能够利用本地冗余或区域冗余配置来实现高可用性。

接下来，如果你在 7 月份发布的预览阶段已经享受到了优质 SSD v2 的好处，你会很高兴地得知[它现在已经正式推出](https://learn.microsoft.com/en-us/azure/virtual-machines/disks-deploy-premium-v2?tabs=azure-cli)。在定义您的确切存储需求(包括大小、IOPS 和吞吐量)时，此产品提供了很大的灵活性。

## Azure 数据库新闻

数据库世界也不是没有在 Ignite 上发布。首先， [Cosmos DB 现在获得了 PostgreSQL 支持](https://devblogs.microsoft.com/cosmosdb/distributed-postgresql-comes-to-azure-cosmos-db/)。这款产品已经上市。这个版本支持分布式表，利用了 Citrus 开源扩展 Postgres。它甚至有一个内置的功能，可以让你通过 PostgreSQL 扩展访问 Azure 存储。

我们将继续关注 Cosmos DB 的另一组公告。虽然 Cosmos DB 已经支持 MongoDB，[自从 Ignite](https://devblogs.microsoft.com/cosmosdb/bigger-and-more-secure-new-features-for-azure-cosmos-db-for-mongodb/) 以来，这种支持已经有了很大的改进。您需要了解两个关键的更新。首先，微软将之前对文档大小的限制从 2MB 增加到 16MB。这意味着您可以在管理的每个文档中放入八倍的数据。此外，您现在可以利用基于角色的访问控制来访问文档中的数据。如果您想在现有数据库上利用这些更新，您需要为您的帐户添加这些功能。

## OpenAI 蓝色

最后，虽然我们意识到微软的 OpenAI 服务仍处于有限的预览阶段，我们大多数人都无法访问，但我们都可以高兴地看到[它现在将包括 DALL-E 2 型号](https://techcrunch.com/2022/10/12/microsoft-expands-azure-openai-service-with-dall-e-2-in-preview/)。据微软称，“精选客户可以生成内容、图像和代码，帮助用户更高效地执行关键业务任务。”

这就是所有的十月点燃 Azure 的头条新闻！

## 想每周了解 Azure 新闻吗？

本周 Azure 是关于 Azure 的每周新闻综述。加入我们的专家主持人，因为他们涵盖了你需要知道的关于过去一周发展的一切，保持简短、有趣和信息丰富。

无论您是刚刚开始您的云之旅，还是您已经了解自己的东西，每个人都有适合自己的东西！