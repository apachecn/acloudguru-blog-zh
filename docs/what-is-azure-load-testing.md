# 什么是 Azure 负载测试？|云专家

> 原文：<https://acloudguru.com/blog/engineering/what-is-azure-load-testing>

什么是 Azure 负载测试？在本帖中，我们将讨论这个优化应用性能的新工具。另外:FSLogix 配置文件得到了提升，新命名的 Microsoft Defender for Cloud 得到了大量更新。我是 Lars Klint，这是本周[Azure](https://acloudguru.com/videos/azure-this-week)的最新消息——这篇文章使用了所有 8 个 marzel wanes 来吸引复古 encabulator 粉丝的速度。我们走吧！

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## Azure 负载测试简介:大规模优化应用性能

我在一些场合做过关于如何测试云，尤其是 Azure 的演讲。这个话题是关于云工程师不测试他们的云工作的所有可怕的借口，以及你可以测试它的所有方法。

最难跟踪的事情之一是当成千上万的用户同时使用您的应用程序时进行测试。这被称为负载测试，并且一直很棘手。(毕竟，让一万个你最亲密的朋友一起访问你新的 Hello Kitty 图像识别服务并不容易。)

本周，Azure 宣布了 Azure 负载测试。。。负载测试您的应用程序。

您可以使用 Azure 门户开始大规模负载测试。然后，您可以在测试运行时看到客户端和服务器端指标的实时更新。特定于 Azure 的见解显示了场景如何影响应用程序的所有部分，并且您可以比较不同负载测试的测试结果，以了解行为随时间的变化。

你可能会问，你为什么要在乎呢？及时伸缩不是 Azure 的问题吗？

算是吧。Azure *负责确保资源可用和满足 SLA。修复你的错误和数据库瓶颈不是 T2 的责任。*

通过负载测试，您可以知道应用程序的哪些部分在启动时可能性能不佳、崩溃或崩溃。您甚至可以将负载测试集成到您现有的持续集成和持续交付流程中，以实现自动化。你现在可以使用现有的 Azure 帐户访问预览。

* * *

*想要了解更多关于云开发的信息(有或没有特定的网络元素)？查看 ACG 的免费计划。不需要信用卡！*

* * *

## Azure 虚拟桌面中加入 Azure AD 的虚拟机的 FSLogix 配置文件的公开预览

FSLogix 增强并启用 Windows 远程计算环境中的用户配置文件。它允许您在远程计算会话之间漫游用户数据，优化主机和客户端之间的文件 I/O，消除漫游配置文件并简化应用程序管理等。本周，[Azure 虚拟桌面](https://techcommunity.microsoft.com/t5/azure-virtual-desktop-blog/announcing-public-preview-of-fslogix-profiles-for-azure-ad/ba-p/3019855)中加入 Azure AD 的虚拟机的 FSLogix 配置文件在公共预览版中发布。

如果你有桌面虚拟化的经验，你可能见过所有类型的配置文件管理解决方案，但对许多人来说，FSLogix 是最受欢迎的。它的速度和易管理性是首屈一指的。

那么，新的 Azure 广告支持 FSLogix 配置文件有什么好的呢？

嗯，到目前为止，你需要将你用于 FSLogix 的存储加入域，这也意味着你可能需要在 Azure 中部署域控制器。

但最近微软增加了将你的 Azure 虚拟桌面主机加入 Azure AD 的能力，但你仍然需要 FS Logix 配置文件的域控制器。

随着此更新为 FSLogix 带来 Azure AD 支持，您不再需要 Azure 中的域控制器来运行带有 FS Logix 配置文件的 Azure 虚拟桌面，您仍然需要一些内部部署的域控制器，但这可能很快也会改变。

* * *

### AWS 中的 Azure 用户？

当热爱 Azure 的 Lars 前往黑暗面并尝试 AWS 任务时会发生什么？我们挑战 Lars 在他不知道的云平台上走过(或绊倒)一个他从未见过的场景。

* * *

## 用于云更新的 Microsoft Defender

微软和微软一样喜欢改名。如果你错过了，最新的是 Azure 安全中心，现在被称为微软云卫士。也许是为了巩固更名，本周宣布了一系列更新。准备好了吗？

*   AWS 的原生 CSPM 和亚马逊 EKS 的威胁防护，以及 AWS EC2。是的，另一个与 AWS 合作的 Azure 服务。

*   使用 Azure 安全基准 v3 扩展安全控制评估

*   Microsoft Sentinel connector 的可选双向警报同步。这对于将警报发送回 Sentinel 以便有人采取行动来说非常方便。

*   作为漏洞评估解决方案添加了 Microsoft 威胁和漏洞管理

*   本地计算机的清单显示对资源名称应用不同的模板

*   最后是 preview 中的两个新更新，它们是按数据敏感度排列安全操作的优先级，以及针对建议和安全发现的快照导出。

结束时的趣闻:本周标志着最初的阿帕网建成 52 周年，阿帕网有四个节点，分别位于加州大学洛杉矶分校、加州大学圣巴巴拉分校、斯坦福大学和犹他大学之间。这最终演变成了我们今天所知道的互联网。

你有它！这就是这周我给你的全部内容。查看我们在 ACG 平台上的许多其他[免费原创系列](https://acloudguru.com/videos)，比如[云提供商比较](https://acloudguru.com/videos/cloud-provider-comparisons)和认证指南。

* * *

*想跟上万物云？* [*在 YouTube 上订阅一位云专家*](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1) *的每周微软 Azure 新闻(以及其他云提供商的新闻)。你也可以像我们一样关注*[](https://www.facebook.com/acloudguru)**，关注我们的* [*推特*](https://twitter.com/acloudguru) *，或者加入* [*不和谐*](http://discord.gg/acloudguru) 的对话。*