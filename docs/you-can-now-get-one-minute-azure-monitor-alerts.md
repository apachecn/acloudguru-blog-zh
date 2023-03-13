# 您现在可以获得一分钟的 Azure Monitor 警报|云专家

> 原文：<https://acloudguru.com/blog/engineering/you-can-now-get-one-minute-azure-monitor-alerts>

本周蓝色世界发生了什么？我们将看看 Azure Kubernetes 服务(AKS)的更新，它将使任何运行 Windows 容器的人受益，Azure Monitor 中基于日志的警报的改进，以及 Azure API 管理中证书的改进。

所有这些马上就来。请继续阅读！

* * *

**加速您的 Azure 职业生涯**

无论你是新手还是认证专家，云专家都能让你轻松(也很棒)地提升自己的职业生涯。查看 [ACG 的免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)或[现在就开始](https://acloudguru.com/pricing)免费试用。

* * *

## 微软在 Azure Monitor 中增加了一分钟频率日志提醒

微软[宣布【Azure Monitor 日志提醒的一分钟频率全面可用。](https://azure.microsoft.com/en-au/updates/general-availability-oneminute-frequency-log-alerts/)

为什么这很重要？Azure Monitor 可以基于指标或日志生成警报。

指标是一段时间内记录的数字数据，包括处理器、内存使用情况或访问您服务的用户数量。因为指标非常轻量级，所以您可以相对快速地接收到警报。

日志更加丰富，包括由 Azure 或您的工作负载生成的基于数据的日志事件。有时日志包含非常重要的数据，需要尽快了解，但是在此功能可用之前，您只能每五分钟生成一次警报。一个例子可能是警告应用程序未按预期执行的日志条目。

现在，使用一分钟频率，您可以更快地收到警报，这意味着您可能会有更少的停机时间，这总是一件好事。

## Azure Kubernetes 服务上对 Windows 的容器支持

微软继续为 Azure Kubernetes 服务(AKS)提供更新，我认为我们会看到这种趋势继续下去。

虽然容器诞生于 Linux，但微软决心让 Windows 成为您的容器化工作负载的最佳选择。为了帮助弥合 Linux 和 Windows 在 AKS 上的差距，微软[宣布了](https://azure.microsoft.com/en-au/updates/generally-available-containerd-support-for-windows-in-aks/)对 Windows 的 containerd 运行时支持。Containerd 是一个行业标准的容器运行时，用于所有主要的云供应商。

Containerd 缩短了启动时间，消耗的资源更少。这意味着您将能够在相同数量的工作节点上运行更多的容器实例，并且当您需要扩展您的工作负载以满足需求时，这将会发生得更快。

很漂亮，对吧？

## Azure API 管理中的托管证书支持

我见过很多次由于证书过期而导致的停机。我过去常常提前几周设置日历提醒，在证书到期更新之前提醒我，因为他们经常被错过。甚至微软也因为证书过期而出现了全球性的 Azure 存储中断。

托管证书是解决这一问题的绝佳方案。它的工作原理是自动管理您的证书更新，以确保您在证书过期时不会停机。

微软[宣布](https://azure.microsoft.com/en-au/updates/public-preview-managed-certificate-support-for-azure-api-management/)在 preview 中支持 Azure API 管理上的托管证书。通过此功能，Microsoft 为您的自定义域提供了托管证书，因此您再也不用担心 API 管理证书了。

你想知道最棒的是什么吗？免费的！

请记住，预览功能还不适合生产工作负载，所以现在就测试它，抑制您的热情，等待全面可用后再将其投入生产。

## 跟上所有蓝色的事物

想要跟上云的所有事物？在推特[上关注 ACG](https://twitter.com/acloudguru)和[脸书](https://www.facebook.com/acloudguru)，[在 YouTube 上订阅云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每周 AWS 更新，并在 [Discord](http://discord.gg/acloudguru) 上加入对话。

希望了解更多关于云和 AWS 的信息，或者在 2022 年开始您的云职业生涯？查看我们每月更新的[免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)的轮换阵容。(不需要信用卡！)