# 微软 Ignite 2022 综述:基础设施

> 原文：<https://acloudguru.com/blog/engineering/microsoft-ignite-2022-roundup-infrastructure>

微软 Ignite 又结束了一年！这一次的活动是面对面和虚拟会议的混合。让我们花点时间来探索微软今年发布的一些最大的 Azure 基础设施公告。

我们将从管理和监控改进开始，然后深入到网络，最后总结一些节省 Azure 计算和许可成本的新方法。

* * *

**通往更好职业的钥匙**

[立即开始 ACG](https://acloudguru.com/pricing) 通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室来改变你的职业生涯。

* * *

## **管理和监控变得更加简单**

### Azure 自动管理

平台即服务(PaaS)和软件即服务(SaaS)产品的巨大优势在于，微软会为您承担更多底层基础设施的管理工作。

但是，有了这种易于管理的特性，您就失去了通过完全管理底层基础设施(包括操作系统)而获得的一些灵活性。

因此，直到最近，您还必须在更简单的管理和更大的灵活性之间做出选择。现在情况不再是这样了。借助 [Azure Automanage](https://techcommunity.microsoft.com/t5/azure-governance-and-management/generally-available-simplify-management-and-operations-with/ba-p/3647522) ，您可以获得基础设施即服务(IaaS)虚拟机的所有灵活性，以及 PaaS 和 SaaS 带来的大量管理细节。

借助 Azure Automanage，您可以自动监控、备份和保护您的虚拟机。Azure Automanage 现已正式推出，并附带了一些值得注意的新功能，包括:

*   支持 Windows 10 虚拟机
*   支持微软反恶意软件
*   能够指定自定义日志分析工作区和备份设置

Azure Automanage 的伟大之处在于，它可以跨您的 Azure 虚拟机以及 Azure 之外的虚拟机工作，包括本地服务器。

### 天蓝色电弧

说到本地服务器，微软还对 Azure Arc 支持的私有云进行了改进，允许您在 preview 中创建、启动和停止 VMware vSphere 和 Azure Stack HCI 上的虚拟机。预览版中还增加了对 System Center Virtual Machine Manager(scv mm)的支持，包括虚拟机启动、停止和删除。

期待微软继续投资 Azure Arc。我的预测是，我们将看到 Azure 成为管理混合云的一站式商店。

### Azure 监视器

对于那些已经使用了 [Azure Monitor](https://techcommunity.microsoft.com/t5/azure-observability-blog/what-s-new-in-azure-monitor-ignite-2022/ba-p/3652570) 和相关日志分析工作区一段时间的人来说，你会知道它已经处于这个过渡阶段，你必须使用旧的日志分析代理或 Azure Monitor 代理。对于某些场景，您需要部署 Azure Monitor 代理(例如 Sentinel)，而对于其他场景，您需要日志分析代理(例如更新管理)。

微软一直忙于将所有现有功能迁移到 Azure Monitor 代理，现在，他们提供了一个代理迁移工具，该工具将帮助指导和自动从旧的日志分析代理迁移到新的 Azure Monitor 代理。因此，当时机成熟时，您可以更轻松地进行迁移。只要确保你在 2024 年 8 月之前转移，那时旧代理将退休。

### Windows 管理中心

最后总结一下管理和监控新闻，从 Azure 门户访问的 Windows 管理中心现在已经普遍可用。

如果您不熟悉此功能，Windows 管理中心允许您直接从 Azure 门户网站轻松管理 Azure 虚拟机的 Windows 操作系统。这包括关键的 Windows 服务器功能，如 Active Directory 域服务和存储副本等。

## 整理网络的松散部分

### Azure 域名系统(DNS)专用解析器

微软也一直在忙于解决网络前沿的一些零星问题。混合 DNS 解析一直很棘手，尤其是当您混合本地 DNS 服务器和 Azure 私有 DNS 区域时。

以前，如果您希望本地服务器解析 Azure 私有 DNS 区域中的 DNS 资源记录，您需要在 Azure 中部署自己的自定义 DNS 服务器。这是因为只有链接到 Azure 专用 DNS 区域的虚拟网络中的虚拟机才能解析该区域中的资源记录。现在普遍可用的 Azure 域名系统(DNS)私有解析器消除了这一要求。您可以简单地部署私有解析器，而不是部署您自己的定制 DNS 服务器虚拟机。如果你在想，“*条件转发怎么样，我仍然需要虚拟机来实现它，不是吗？*“不，私有解析器也支持这个。

### Azure 专用链接

微软还清理了一些围绕私有端点的遗留问题，私有端点是支持 Azure Private Link 的网络接口。

现在，您可以为您的私有端点使用[静态 IP 地址，使您能够在部署时使用保留的 IP 地址，而不是随机的 IP 地址。当您必须处理像 DNS 缓存或安全规则这样的问题时，这很有用。很高兴有。](https://azure.microsoft.com/en-gb/updates/general-availability-static-ip-configurations-of-private-endpoints/)

如果你像我一样，是一个坚持良好命名惯例的人，那么当你创建私有端点时，你总是得到相当随机的名字，这可能会困扰你。我的意思是，我和其他人一样喜欢全球唯一标识符(GUID ),但也许我更喜欢将我的私有端点网络接口命名为 T1。现在你可以了。继续并适当地命名您的网络接口。

### Azure 分布式拒绝服务(DDoS)保护

你知道拥有公共服务的每个人都应该使用的功能，但是因为太贵而没有使用？是的，我指的是 Azure DDoS 保护。

嗯，微软打算解决这个问题，通过推出一个新的 SKU，让各种规模的公司都能获得 DDoS 保护。

你仍然可以免费获得 Azure DDoS 基础设施保护，但如果你想要更高级别的保护，你可以在 DDoS IP 保护(目前在预览版中)和 DDoS 网络保护之间进行选择。DDoS 网络保护是 DDoS 保护标准的延续，有了新的名称。

新的 DDoS IP 保护 SKU 允许您以相同的保护级别保护单个公共 IP 地址，而无需如此大的前期成本。您确实错过了一些附加功能，如成本保护和快速响应支持，但对于各种规模的企业来说，最终能够获得关键工作负载所需的保护级别是件好事。

## ****到处储蓄****

随着全球经济给 IT 预算带来压力，很高兴知道微软正在 Azure 和混合云上实现进一步的节省灵活性。

### Azure 计算节省计划

许多公司一年 365 天，一天 24 小时运行一套标准的计算资源。这些计算资源可能对您的业务至关重要，但由于您的业务性质，它们可能也需要具有灵活性。

例如，您可能有一个 Web 服务器虚拟机，它当前托管着您公司所依赖的一个网站，您计划在未来几年内将它转移到应用服务或容器实例。您决定不购买保留的实例来支付该虚拟机的成本，因为您知道它不会成为一个虚拟机很久。

现在，借助 [Azure 计算节省计划](https://techcommunity.microsoft.com/t5/azure-compute-blog/optimize-and-maximize-cloud-investment-with-azure-savings-plan/ba-p/3636447)，您可以预先确定您计划用于一系列计算服务(如虚拟机、容器实例、Azure 应用服务、专用主机或高级功能)的固定金额，并在这些服务之间转移工作负载，同时仍然实现高达 65%的节省。

您还可以将 Azure savings plan for compute 与保留实例或 Azure Hybrid Use Benefit 相结合，以进一步节省微软软件和操作系统的成本。当应用多个折扣时，会自动应用较大的折扣。

### 混合使用效益

说到混合计算，[微软已经将混合使用优势](https://cloudblogs.microsoft.com/windowsserver/2022/10/12/maximize-your-windows-server-investments-with-new-benefits-and-more-flexibility/)扩展到两个新的场景。

如果您拥有 Windows Server 软件保障，您现在可以在 Windows Server 或 Azure Stack HCI 上运行 Azure Kubernetes 服务，无需额外费用。

该扩展还包括 Windows Server Datacenter 软件保障许可证持有者无需额外费用即可使用 Azure Stack HCI 的能力。这实质上意味着，无论您是在内部还是在 Azure 中进行现代化，您都可以使用虚拟机和容器以及 Azure 管理功能来实现工作负载的现代化，从而充分利用您的投资。

* * *

![why should i get azure](img/3ee87ddb6a81b5631ab6555721b8b023.png)

*想了解更多关于 Azure 认证的信息？*
*查看我们的* *[Azure 认证和学习路径。](https://acloudguru.com/azure-cloud-training)*

* * *

## 跟上所有蓝色的事物

这是我对微软 Ignite 的总结，一如既往地有更多内容要介绍，请查看本周发布的其他一些新闻的更多细节，并查看[微软 Ignite 新闻手册](https://news.microsoft.com/ignite-2022-book-of-news/)以获得所有微软软件和服务的全面发布列表。

想了解更多关于云和 Azure 的信息，或者想在 2022 年开始你的云计算生涯？查看我们每月更新的[免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)的轮换阵容。(不需要信用卡！)