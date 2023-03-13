# 云专家 Azure |上的 Citrix 虚拟应用和桌面

> 原文：<https://acloudguru.com/blog/engineering/citrix-virtual-apps-and-desktops-now-on-azure>

你觉得世界排名第一的超级计算机 Fugaku A64FX 有几个 CPU 核？答案在帖子的最后。但首先，我有一些 Citrix goodness、Web、Pub *和* Sub，以及云中的一些重要计算能力。这是你对本周 [Azure 发生的事情](https://acloudguru.com/videos/azure-this-week)的综述。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过微软 Azure、AWS 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## Citrix 支持 Azure VMware 解决方案上的虚拟应用和桌面服务

数百年来，Citrix 一直用于为大型组织虚拟化桌面环境。好吧，也许不是几个世纪，而是很长时间。它是支持大型、安全和分布式企业基础设施的行业标准之一。

最受欢迎的产品之一是虚拟应用和桌面服务，它允许用户无论在哪个设备上都可以连接到应用和桌面体验。

是的，你猜对了。通过使用一个 [VMware 解决方案](https://docs.microsoft.com/en-us/azure/azure-vmware/azure-vmware-solution-citrix)，这项服务现在[在 Azure](https://azure.microsoft.com/en-au/updates/citrix-supports-virtual-apps-and-desktop-service-on-azure-vmware-solution/) 上可用。正如微软市场部喜欢说的，您可以“将基于 vSphere 的 Citrix 工作负载提升并转移到 Azure VMware 解决方案，并继续利用现有的 VMware 和 Citrix 工具和专业知识来实现运营一致性。”(哇，这听起来像是正常的营销用语。)

该服务现已全面上市，并且——结合最近发布的 Azure Stack HCI 的 Azure 虚拟桌面——Azure 现在拥有大量桌面即服务。是的，那是一件事。

* * *

*想了解更多关于使用 Azure 进行云开发的信息吗？查看[本月的免费 ACG 课程阵容](https://acloudguru.com/blog/news/whats-free-at-acg)，包括我们闪亮的新 [AZ-400 DevOps 认证考试课程](https://acloudguru.com/course/az-400-designing-and-implementing-microsoft-devops-solutions)。只需[创建一个免费账户](https://acloudguru.com/pricing)并升级。不需要信用卡！*

* * *

## 使用 Azure web PubSub 构建实时 Web 应用

Azure Web publibsub 终于全面上市了。这是一个完全托管的基于 WebSocket 的服务，可以让您轻松构建“实时 web 应用程序，如实时监控仪表板、跨平台实时聊天、地图上的实时位置等等。”

迁移到 GA 非常棒，原因有三:

1.  可用性的 SLA 现在是 99.9%，因此您可以依赖它进行生产。
2.  现在有更多的 Azure 区域支持这项服务。
3.  安全性大大提高。

首先是 Azure Active Directory 支持使用单点登录等等。也可以使用私有端点，现在有更多的 API 端点，还有 Azure CLI。。。嗯，管用。

此外，Azure 发布了一系列触发器和绑定，可以更容易地使用 Azure 函数，你知道我喜欢一个奇妙的函数特性。但也有与其他 Azure 服务的集成，如 Azure 静态 Web 应用程序、Azure API 管理、Azure 应用程序网关和 Azure Monitor。

那是 PubSub。今天就尝试一下。

* * *

[![Complete guide to the Cloud and Dictionary ](img/93ebf63b88ab7fbd48705a01952ba688.png)](https://get.acloudguru.com/cloud-dictionary-of-pain)

[**得到蔚蓝云痛苦辞典**](https://get.acloudguru.com/cloud-dictionary-of-pain)
说云不一定要辛苦。我们分析了数以百万计的回复，找出了最容易让人犯错的概念。抓住这个[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)获取 Azure 中一些最痛苦术语的简洁定义。

* * *

## 随着最新的 80GB NVIDIA A100 GPUs 在 Azure 的全面上市，微软扩大了其人工智能超级计算机阵容

终于有另一个虚拟机让马克·鲁西诺维奇在 T1 上玩俄罗斯方块了！

Azure 全新的虚拟机系列， [NDm A100 v4 系列，搭载 NVIDIA A100 Tensor Core 80gb GPU 的](https://azure.microsoft.com/en-au/blog/microsoft-expands-its-aisupercomputer-lineup-with-general-availability-of-the-latest-80gb-nvidia-a100-gpus-in-azure-claims/)来了！

是的，你没听错:80GB GPU。我们真的可以开始开采一些比特币——等等。哦，它们不是用来采矿的。哎呦！

我们现在可以通过使用一个或多个新的虚拟机来训练高度复杂的机器学习模型。是的，你可以连接多达八个，获得巨大的计算能力。每个虚拟机可用的 RAM 也增加到了 1，900 GB。这应该能够在打开四个标签页的情况下运行 Chrome。毕竟，它现在是这类工程成就 500 强名单中的四个超级计算机的一部分，占据第 26 至 29 位。

如果你想尝试新的 VM，Azure 上有；然而，定价可能是一个问题。虽然我找不到它的任何成本明细，但 6 月份的 40 GB 版本大约是每月 25，000 美元。所以不要随便编一个。

你没有读完整本，是吗？你只想要问题开始时的答案。是 7，630，848 个核心。这已经很多了！这也是排名第二的三倍多。

正如我们在云专家团队中所说的，当我们不得不询问团队本周最好的新闻故事是什么，因为有人没有仔细阅读 Citrix 产品:“寻找，你将会云。”继续牛逼吧，云大师们！

*想跟上万物云？* [*在 YouTube 上订阅一位云专家*](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1) *的每周微软 Azure 新闻(以及其他云提供商的新闻)。你也可以像我们一样关注*[](https://www.facebook.com/acloudguru)**，关注我们的* [*推特*](https://twitter.com/acloudguru) *，或者加入* [*不和谐*](http://discord.gg/acloudguru) *的对话！**