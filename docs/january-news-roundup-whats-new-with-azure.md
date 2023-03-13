# 一月新闻综述:Azure 有什么新特性？

> 原文：<https://acloudguru.com/blog/engineering/january-news-roundup-whats-new-with-azure>

你好，云大师！想知道 Azure 在过去的一个月里发生了什么变化，但没有时间查看标题？我们已经写了一篇文章，提供了你需要知道的所有信息。

## 新的 Windows 核心操作系统平台博客

虽然 Windows Vista 可能受到了不同的欢迎，但其基于服务器的兄弟 Windows Server 2008 包含了有史以来最重要的 Windows Server 功能之一。

那是什么特征？

当然是 Hyper-V！Hyper-V 是微软的虚拟化平台，通常被称为管理程序。对于不熟悉的人来说，虚拟机管理程序允许您在一台物理服务器上运行多个虚拟机。

微软最近在其新的 [Windows 平台操作系统博客](https://techcommunity.microsoft.com/t5/windows-os-platform-blog/bg-p/WindowsOSPlatform)上的一篇博客文章中证实，所有基础设施即服务(IaaS)和平台即服务(Platform as a Service)服务，包括虚拟机、Web 应用、Azure 功能等，都运行在 Hyper-V 上。

在帖子中，他们详细介绍了名为云主机的 [Azure 主机操作系统，该系统基于 Windows 和 Hyper-V，但旨在真正擅长运行虚拟机。这对公共云来说有点重要！](https://techcommunity.microsoft.com/t5/windows-os-platform-blog/azure-host-os-cloud-host/ba-p/3709528)

这是一个有趣的阅读，甚至有一个云主机在一个有 16 个物理处理器的 Azure 主机上运行的截图。想象一下您可以在那个服务器上运行多少无服务器代码！

## Azure 上的扩展安全更新

如果你的公司像许多其他公司一样，仍然有工作负载在旧版本的 Windows Server 上运行，那么知道微软将允许你在 Azure 或 Azure Stack 上运行旧版本的 Windows Server 并免费接收扩展的安全更新可能对你很重要。

对于任何人来说，肯定没有人还在运行 Windows Server 2008…再想想吧！Windows 7 的市场份额估计仍在 11%左右。到处都隐藏着运行旧版本 Windows 的服务器。

对于 Azure 上的 Windows Server 2008、2008 R2 和 Windows 7，扩展安全更新于 1 月 10 日结束。如果您不希望您的公司因为所有错误的原因成为新闻头条，现在是时候将这些工作负载迁移到更现代的东西上了。

有很多选择，你可以迁移到较新版本的 Windows Server，或者有一个软件即服务(SaaS)解决方案可以取代你的老化应用程序。或者，该功能可以在平台即服务产品中复制，如 Azure App Service。

我们知道迁移或升级这些工作负载有多困难，看看您能做些什么，祝您成功迁移或淘汰这些工作负载。您为帮助维护客户数据安全所做的一切都是值得的。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## Azure Automation Visual Studio 代码扩展

微软在预览版中宣布发布 [Azure Automation Visual Studio 代码扩展。](https://azure.microsoft.com/en-au/updates/azure-automation-extension/)

对于任何不知道的人来说，Azure Automation 是一个被低估的 Azure 服务，它让你(除了其他事情之外)通过 Runbooks 自动化你的混合计算灾难。Wayne Hoggett 在最近的一篇 ACG 博客文章中详细解释了他为什么喜欢 Azure Automation。

Azure Automation 的 Visual Studio 代码扩展不仅允许您创建、测试、调试和管理 Azure Automation Runbooks，还允许您管理使 run book 如此有用的所有相关资产，如 Visual Studio 代码中的计划、变量和凭证。

如果你是 ACG 的订户，并且你有兴趣了解更多关于 Azure Automation 的知识，我们有几个全新的动手实验室，在那里你可以学习如何使用 Azure Automation[自动化混合流程](https://learn.acloud.guru/handson/a039d77e-a284-4cf1-bf8f-8b04d330c256)或[配置更新管理](https://learn.acloud.guru/handson/e21c1e8c-61bd-4c34-9108-88fc3932c410)。

## **Azure open ai 服务全面上市**

OpenAI 服务于本周正式发布。[虽然公告](https://azure.microsoft.com/en-us/blog/general-availability-of-azure-openai-service-expands-access-to-large-advanced-ai-models-with-added-enterprise-benefits/)有一些常见的营销术语，但它也声明了人工智能集成正在进入 Azure 的一切，包括安全性、可靠性、合规性、数据隐私和内置的负责任的人工智能功能。是的，人工智能正在 Azure 平台上受到热烈欢迎，微软没有退缩。在不久的将来，人工智能将成为云服务和解决方案的加速器。完美吗？不会，当然不会，但会迅速改善。

## **Azure 机器学习更新**

如果你想看看人工智能 cookie 是如何制作的，那么 Azure 机器学习就是合适的地方。本月，一系列新功能同时进入了预览版和正式版。几个亮点:

*   无需编写任何代码即可构建端到端模型培训管道的能力。这与越来越多的服务需要越来越少的代码是一致的。
*   比较不同的管道以调试失败:现在，您可以通过对特定管道失败原因的新了解来节省调试时间。还有一个特性是识别有问题的节点进行调试。
*   现在，您可以保护受管在线端点的入口和出口，以确保符合企业安全标准。
*   最后，您现在可以在工作区和计算上添加、查看、更新和/或删除自定义标记，以更深入地了解成本模式、支出模式和治理方案。

除此之外，还有更多新功能，所以要查看它们，请访问[正式发布更新](https://azure.microsoft.com/en-us/updates/azure-machine-learning-generally-availability-updates-for-january-2023/)，或[预览公告](https://azure.microsoft.com/en-us/updates/azure-machine-learning-public-preview-announcements-for-january-2023/)。

## 想每周了解 Azure 新闻吗？

本周 Azure 是关于 Azure 的每周新闻综述。加入我们的专家主持人，因为他们涵盖了你需要知道的关于过去一周发展的一切，保持简短、有趣和信息丰富。

无论您是刚刚开始您的云之旅，还是您已经了解自己的东西，每个人都有适合自己的东西！