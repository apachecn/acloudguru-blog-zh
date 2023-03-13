# 11 月新闻综述:Azure 有什么新特性？|云专家

> 原文：<https://acloudguru.com/blog/engineering/november-news-roundup-whats-new-with-azure>

你好，云大师！想知道 Azure 在过去的一个月里发生了什么变化，但没有时间查看标题？我们已经写了一篇文章，提供了你需要知道的所有信息。

## Kubecon 2022 & AKS

Kubecon 2022 在 11 月初举行，随之而来的是一系列 Azure Kubernetes 服务更新。

从性能角度来看，最大的宣布是一个名为 [Azure CNI 的新网络框架，由 Cilium](https://techcommunity.microsoft.com/t5/azure-networking-blog/azure-cni-powered-by-cilium-for-azure-kubernetes-service-aks/ba-p/3662341) 提供支持，它提供了显著的优势，如更高效的数据路径，以提供对您的 pod 的更快直接访问，以及内置对 Kubernetes 网络策略的支持，而无需单独安装解决方案。

那么，用简单的英语来说，这意味着什么呢？简而言之，它使您的大规模 Kubernetes 工作负载更快、更安全，这总是一件好事。

我们还为 AKS 做了一些新的安全增强。

第一个叫做[图像清洁器](https://learn.microsoft.com/en-us/azure/aks/image-cleaner?tabs=azure-cli)，现在可以在预览版中看到。当您维护持续的 AKS 工作负载时，随着时间的推移，节点可能会收集旧的映像，这可能存在安全漏洞。图像清洁器有效地通过您的节点，并自动清除那些旧的，陈旧的图像，消除它作为一个可能的安全风险。

它在 AKS 中充当一个托管的附加组件，它将从 AKS 中生成一个过时图像的列表。它不包括附加到运行窗格的图像，客户也可以手动排除某些图像。从那里，Image Cleaner 将对“陈旧”列表中的任何剩余映像运行清除作业，从而产生一个更新鲜、更干净、更安全的 Kubernetes 节点。

第二个安全公告是 AKS 集群的 [Mariner OS 映像的可用性。](https://microsoft.github.io/CBL-Mariner/docs/#key-capabilities-of-cbl-mariner-linux)

Mariner OS 是微软为安全容器设计的轻量级 linux 发行版。它已经在微软的几个产品中使用，如 Xbox、《我的世界》和 100 多个 Azure 服务。公众也可以在他们自己的容器化工作负载中使用它。因此，如果您一直想在与《我的世界》相同的操作系统结构上构建您的集群……现在您可以了！

## 计算节约计划

如果你在 Azure 上有长期运行的计算作业，你可能已经熟悉 Azure reservations，它允许你以大幅降低的价格购买 1 或 3 年的承诺量的计算能力。然而，Azure reservations 有许多限制，例如绑定到特定区域进行预订，限于特定的虚拟机系列或 SKU，或者绑定到特定的计算服务，如虚拟机或应用服务。总的来说，如果您需要进行重大的更改，灵活性会受到一点限制。

考虑到这一点，称为计算的[节省计划的新功能类似于 Azure 预订，但是它在如何使用预订的计算方面提供了更大的灵活性。借助计算节省计划，您还可以预留一定量的计算容量。然而，保留的容量可以用于几乎任何计算类型，例如虚拟机或 AKS 容器，并且可以在**任何**地区使用。这为您**在何处以及如何运行计算工作负载方面提供了更大的灵活性，同时还能节省大量资金。**](https://azure.microsoft.com/en-us/pricing/offers/savings-plan-compute/#how-it-works)

## **Vision Studio 简介**

处理大量图像和视频变得越来越普遍。人工智能的新发展在这一领域开辟了令人兴奋的可能性，Azure 创造了一个伟大的新工具来帮助你入门。 [Vision Studio](https://azure.microsoft.com/en-au/blog/introducing-vision-studio-a-uibased-demo-interface-for-computer-vision/) 让您在一个简洁的用户界面中访问处理媒体和返回信息的高级算法。

你所需要做的就是给你的媒体资产提供这个计算机视觉工具，你可以使用简单的 UI 工具来查看你的数据如何响应新的人工智能分析工具。其中包括空间分析、人脸识别、图像分析等。

## **Azure Communication Services 短信短码功能**

使用 SMS(短消息服务)联系您的客户变得非常流行。短信技术真正有助于数字营销的一个方面是“短码”:你可以用 5 或 6 位数字来跟踪个人短信活动。随着 Azure Communication Services 短代码功能的[全面上市，您可以将此功能添加到您的数字通信工作中，或者从另一家提供商迁移您的短代码基础架构。](https://azure.microsoft.com/en-au/updates/generally-available-azure-communication-services-short-code-functionality-for-sms/)

您还可以轻松地将 SMS 短代码工作负载集成到其他 Azure 服务中，例如，您可以使用 Azure 的逻辑应用连接器将基于 SMS 的工作流添加到您的应用中，或者使用集成的 Azure 事件网格触发您的短代码 SMS 消息。

## 静态 Web 应用程序更新

这个月静态网络应用的更新不是一两个，而是六个。所以让我们快速浏览一下它们！

首先，我们有了新的平台支持，预览版中的和[支持](https://azure.microsoft.com/en-us/updates/generally-available-azure-static-web-apps-now-fully-supports-net-7/)[节点 18。NET 7 全面上市](https://azure.microsoft.com/en-us/updates/public-preview-azure-static-web-apps-now-supports-node-18/)。现在，如果你有一个 Blazor WebAssembly 应用程序，它会自动构建和部署。

接下来，我们知道你们中有很多人使用 GitHub，但许多组织也使用其他库，如 Gitlab 和 BitBucket。好吧，你会很高兴地知道对这两者的[支持现在已经普遍可用](https://azure.microsoft.com/en-us/updates/generally-available-static-web-apps-support-for-gitlab-and-bitbucket/)。现在，您可以将它们用作静态 Web 应用程序的 CI/CD 提供者。

接下来，让我们讨论一下预览环境。当您的存储库上有一个为其生成的临时 URL 的 pull 请求时，这些使您能够启动一个全新的环境。现在[你可以在 Azure DevOps](https://azure.microsoft.com/en-us/updates/generally-available-static-web-apps-support-for-preview-environments-in-azure-devops/) 上使用这些预览环境，因为该特性已经普遍可用。此外，您现在可以[创建绑定到特定分支的命名环境](https://azure.microsoft.com/en-us/updates/generally-available-static-web-apps-support-for-stable-urls-for-preview-environments/)，这将为分支预览环境产生相同的 URL。该功能现在也普遍可用。

最后，您现在可以为您的应用程序指定一个设置，如果您的应用程序中不需要这个设置，您可以[跳过 API 的构建。这一个现在也是 GA。](https://learn.microsoft.com/en-us/azure/static-web-apps/build-configuration?tabs=github-actions#skip-building-the-api)

## 宇宙数据库更新

接下来，我们有两个关于 Cosmos DB 的公告。首先，当使用 MongoDB for Cosmos DB 时，您现在可以[重试您的写操作。您总是能够用自己的重试逻辑来处理这个问题，但是现在您可以在驱动程序级别利用这个优势，而不需要任何自定义代码。好消息是，这通常是可用的，但是在利用它之前，您需要启用这个功能。](https://learn.microsoft.com/en-us/azure/cosmos-db/mongodb/feature-support-42#retryable-writes)

此外，你现在可以[在你的账户中复制一个 Cosmos DB 容器，而不需要借助任何额外的工具](https://learn.microsoft.com/en-us/azure/cosmos-db/intra-account-container-copy)来实现。如果您正在尝试测试一些迁移、调试一些特定于数据的问题，或者即使您希望在不消耗任何生产容量的情况下运行分析工作负载，这一点也非常重要。这里有一些注意事项，所以在利用这个公开预览之前，请阅读文档。

## 成为 Azure Orbital Space SDK 的空间开发者

本月[微软发布了他们的 Azure Orbital Space SDK](https://azure.microsoft.com/en-us/blog/any-developer-can-be-a-space-developer-with-the-new-azure-orbital-space-sdk/) 的预览版，这不仅是一个伟大的名字，也是开发者将云带到太空的一种方式。这不是某种可能与太空中的事物对话的服务，Azure Orbital Space SDK 被设计成与航天器无关。

然而这对我们人类来说到底意味着什么呢？通过新的 SDK 云，开发人员可以制作更复杂的软件，这些软件可以在航天器上运行，并对传输回地球的内容进行优先排序，从而提高数据质量，同时节省非常昂贵的带宽。把它想象成边缘计算的边缘。终极优势？

例如，你可以对有用的图像进行优先排序，甚至将洞察力而不是原始数据发送到地面。卫星可能会利用它来优化与地球偏远地区的通信，使连接在任何地方都更容易实现。或者我们可以用更好的数据更好地模拟和应对气候变化。有很多可能性。微软正在为一个传统上没有任何实际航天器应用程序开发的行业带来一个标准。

如果你想试用 SDK，现在你必须为 Azure Space 合作伙伴社区成员之一工作，但这只是为了预览。期待公版 SDK 很快推出！

## Azure 函数的 Azure SQL 触发器

对于开发者来说，Azure Functions 是 Azure 上最重要和最有用的服务之一，但是仍然有改进和增加功能的空间。其中一个功能在本周公开预览版中发布。Azure 函数的 Azure SQL 触发器意味着当 SQL 数据库中的一行被创建、更新或删除时，你可以触发 Azure 函数。这对于许多场景都非常有用，例如，当插入新的客户记录时，您可以触发一个功能来发送欢迎电子邮件、插入另一条记录、从社交媒体获取他们的个人资料图像等等。

Azure 函数的 Azure SQL 绑定还启用了对 Java、PowerShell、Python、JavaScript 和 C#函数的输入和输出绑定支持，因此每个人都可以加入进来。我能看到的一个场景是，数据库行中的数据操作可以“外包”给 Azure 函数，这创造了更多的灵活性。试一试。

这就是 Azure 月的所有头条新闻！

## 想每周了解 Azure 新闻吗？

本周 Azure 是关于 Azure 的每周新闻综述。加入我们的专家主持人，因为他们涵盖了你需要知道的关于过去一周发展的一切，保持简短、有趣和信息丰富。

无论您是刚刚开始您的云之旅，还是您已经了解自己的东西，每个人都有适合自己的东西！

## 云快乐免费证书准备

在今年年底之前，作为“云快乐”活动的一部分，你可以[注册免费的认证准备](https://www.pluralsight.com/offer/cloud-certification)和 Pluralsight 技能或云专家。你可以在 AWS、Azure、GCP、Kubernetes 和 Terraform 上免费学习课程——当我们说免费时，我们指的是真正的免费。

有如此多的选择，我们写了一篇关于如何为你选择正确课程的文章。你唯一可能犯的错误就是根本不做选择！