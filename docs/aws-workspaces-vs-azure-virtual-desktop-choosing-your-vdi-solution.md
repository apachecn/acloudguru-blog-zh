# AWS 工作区与 Azure 虚拟桌面:选择您的 VDI 解决方案|云专家

> 原文：<https://acloudguru.com/blog/engineering/aws-workspaces-vs-azure-virtual-desktop-choosing-your-vdi-solution>

没有什么事情比在 IT 部门工作，听经理告诉你的团队，公司将在几周内完全远离，你的团队需要准备好支持这种转变更有压力了！我们中任何一个在 2020 年早期在 IT 界工作的人都会有同感！如果你曾经面临这个挑战，许多事情可能会在你的脑海中闪过。我们将如何提供员工工作所需的硬件和软件？当我们日以继夜地建设基础设施时，如何让咖啡机保持满满的？

使用云提供商为您的员工提供虚拟桌面基础架构(VDI)是解决许多这些[云支持](https://acloudguru.com/platform/accelerator-program)问题的好方法，所以让我们来看看 Azure 虚拟桌面(以前的 Windows 虚拟桌面)和 AWS 工作区，以找到最适合您的解决方案。

## 什么是虚拟桌面？

简而言之，我们可以利用 Azure、AWS 或许多其他选项来为用户提供虚拟桌面，这些用户已经预装了他们需要的应用程序或根据需要提供了这些应用程序。现在，您可以只部署一台虚拟机，称之为虚拟桌面，但如果您想要可扩展性、安全性、易用性等，您会想要使用虚拟桌面基础架构解决方案。

## Azure 虚拟桌面与 AWS 工作区的比较

假设你在 Gnomes 公司工作，这是一家生产花园侏儒和花园侏儒设计的公司。您刚刚得到消息，设计师、呼叫中心员工和财务部门将完全远程化。幸运的是，你一直与云世界保持同步，你知道你可以使用 Azure VDI 或 AWS Workspaces 为你的同事提供虚拟桌面，但你应该选择哪一个呢？来看看，帮帮我们的小侏儒朋友吧！

### 特征

这两款产品都提供了许多相同的功能，例如从任何地方进行远程连接、使用本机应用程序或网络浏览器、持久文件存储、部署定制应用程序，所以让我们来看看它们的不同之处。

通过 AWS 工作区，每个用户都可以获得自己的个人桌面，可以是 Windows 或 Linux 操作系统。下面是 AWS Workspaces 提供的 Linux 桌面截图。

![Linux desktop by Amazon Workspaces.](img/b5bbd37b4c1d81d6e4a8b779ef267dec.png)

在 Azure 虚拟桌面方面，Windows 将是唯一的操作系统选项，用户可以拥有一个个人桌面，或者许多用户可以共享一个虚拟机。许多用户共享一台虚拟机是降低成本和减少虚拟机数量的好方法。

下一个需要考虑的重要事项是，AWS Workspaces Windows 产品实际上是 Server 2016。要在 AWS 工作区上安装 Windows 10，你需要[适当的许可](https://docs.aws.amazon.com/workspaces/latest/adminguide/byol-windows-images.html)和每个地区至少 200 个工作区的*！*

*![Showing Amazon Workspaces Windows Server 2016](img/9bdf9851d3ad22475ed7cf8fb3044910.png)*

### *定价*

*现在我们来看一下每种产品的定价。现在，假设我们计划为 Gnomes Inc .财务部的 10 个用户创建虚拟桌面。对于财务部门，IT 团队已经确定他们需要一台 2 个虚拟 CPU、8gb 内存和 Windows 操作系统的机器。*

#### *AWS 工作区定价方案*

*我们首先来看看 AWS 工作区。考虑到这些要求，并查看 AWS Workspace [定价页面](https://aws.amazon.com/workspaces/pricing)，我们看到一个 2 VCPU 和 8gb RAM 的虚拟机将运行 47 美元/月；这也包括 Windows 许可。完美。因此，对于 10 个用户，我们的账单将为**470 美元/月(T3)。***

* * *

## ***改变职业，改变企业***

*学得更快。动作快点。通过 AWS、Microsoft Azure、Google Cloud 等平台中的课程、动手实验室和[云沙盒环境](https://acloudguru.com/platform/cloud-sandbox-playgrounds)实现转型。*

* * *

#### *Azure 虚拟桌面定价方案*

*接下来，Azure 虚拟桌面。我们可以通过两种方式来看待 Azure 虚拟桌面的定价:每个用户获得自己的虚拟机(称为**个人**)，或者许多用户共享一个虚拟机(称为**池**)。让我们先来看一下个人配置，每个用户都有自己的 VM，以便直接与 AWS 工作区进行比较。*

##### *个人定价*

*首先，我将调出[Azure 定价计算器](https://azure.microsoft.com/en-us/pricing/calculator/)，并插入我们想要的虚拟机的信息。仅一台带有 2 个虚拟 CPU 和 8GB 内存的 D2 v4 虚拟机就要花费 80 美元/用户/月，而且我们还必须考虑许可！让我们假设每个用户都将使用微软 365 高级订阅，这将允许他们使用 Azure 虚拟桌面虚拟机，每月每用户 20 美元。因此，考虑到所有这些因素，10 个用户每月的费用将超过 100 美元，相当于**每月 1000 美元！***

* * *

**需要云计算和 Azure 的介绍？从 [Azure Fundamentals](https://acloudguru.com/course/az-900-microsoft-azure-fundamentals) 开始，这是让你在微软 Azure 平台中导航的最佳切入点。**

* * *

*所以在个人用户桌面的情况下，Azure 虚拟桌面的成本是 AWS 工作区的两倍多。但是如果我们把我们的用户集中起来呢？我们的成本会如何变化？*

##### *混合定价*

*回到定价计算器。这一次，我将选择池化配置，并根据微软的虚拟机指南选择虚拟机。因为我们的用户不到 20 人，并且假设是“重工作负载”类型，所以微软推荐 D8s_v4 (8 个 VCPUs 和 32GB RAM)。现在，如果我们计算虚拟机价格，再加上一点存储成本，以及所有 10 个用户的 Microsoft 365 Premium 订阅，我们得出**每月总计 600 美元。***

*即使使用池化配置，AWS 工作区仍然是最便宜的选择。*

*[![workspaces and vpns](img/e1670b67db6b4a8da8dad268fc93b57b.png)](https://acloudguru.com/blog/engineering/vpn-cloud-desktop-amazon-workspaces)

Read more from ACG: [With VPNs besieged, cloud desktop get their close-up](https://acloudguru.com/blog/engineering/vpn-cloud-desktop-amazon-workspaces)* 

### *性能和可靠性*

*最后，我们来看看性能和可靠性。根据我使用 Azure 虚拟桌面和 AWS 工作区的经验，我认为它们在使用本地远程应用程序时表现非常相似。你可以看出，这两款软件在启动程序和应用程序时都会有一点延迟，但我个人认为 Azure 虚拟桌面的延迟要小一些。*

*在可靠性方面，AWS workspaces 提供了 99.9%的正常运行时间 SLA。另一方面，Azure 虚拟桌面“努力实现至少 99.9%的可用性”，并且“[微软不提供财政支持的服务水平协议。](https://azure.microsoft.com/en-us/support/legal/sla/virtual-desktop/v1_0/)“因此，如果您需要有保证的 SLA，那么 AWS Workspaces 将是您的最佳选择。*

## *AWS Workspaces 和 Azure 虚拟桌面哪个适合我？*

*现在，我们已经了解了这两种产品的功能、定价、性能和可靠性，您应该选择哪一种？嗯，这要取决于你的情况(以及你的公司为高峰花园侏儒季节配备了多少人员)。如果您需要提供 Linux 桌面，或者您的工作负载可以在 Server 2016 上运行，那么我会建议您使用 AWS 工作区。然而，如果你需要不到 200 个用户的 Windows 10，或者想减轻管理大量虚拟机的复杂性，那么 Azure 虚拟桌面是你的好选择。*

*如果你想了解更多关于 Azure 虚拟桌面以及如何使用它为你的终端用户提供一个安全的、可伸缩的、无缝的虚拟桌面的信息，请查看我的课程[Azure 虚拟桌面简介](https://acloudguru.com/course/introduction-to-azure-virtual-desktop)，我在其中讲述了 Azure 虚拟桌面的主题，如术语、定价和许可，并展示了几个实际的演示。*