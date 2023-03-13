# 九月新闻综述:Azure 有什么新特性？|云专家

> 原文：<https://acloudguru.com/blog/engineering/azure-september-news>

你好，云大师！想知道 Azure 在过去的一个月里发生了什么变化，但没有时间查看标题？我们已经写了一篇文章，提供了你需要知道的所有信息。

## Azure 托管的 Grafana 变得可用

Grafana 是一个第三方多平台开源分析解决方案。它可以连接各种各样的数据库，而且由于它是开源的，允许程序员从头开始编写插件，以获得更大的连接灵活性。

就像其他监控平台一样，它允许在一段时间内对数据进行分析和监控。它经常用于跟踪用户行为、搜索错误，以及识别可能影响业务决策的独特数据点。

本月，微软开始全面发布 Azure 托管的 Grafana。有了它，你可以在 Azure 内原生运行 Grafana。这允许你使用 Grafana 将 Azure 服务与 Azure 之外的其他服务连接起来。

## 对 Azure 成本管理的更改

大型组织通常有多个 Azure 目录租户。发生这种情况的原因是公司的合并、收购、安全问题和分离。不管是什么原因，当尝试跨组织管理和优化计费时，多个租户会导致混乱。这个问题实际上是客户在考虑 Azure 成本管理时提出的最多的问题之一。

为了帮助解决这个问题，[微软最近增加了一项新功能](https://azure.microsoft.com/en-us/blog/microsoft-cost-management-updates-august-2022/)，允许您从一个微软客户协议计费帐户管理多个租户。启用后，无需在多个租户之间导航，即可授予访问权限，允许查看和下载发票、监控成本以及创建更多订阅。

这简化了流程，并允许更好地了解整个组织发生的成本。

## Azure Monitor 变更分析功能发布

在 Azure Monitor 中，你现在可以访问[一个新的变化分析特性](https://azure.microsoft.com/en-us/updates/generally-available-enterpriseready-azure-monitor-change-analysis-capability-released/)。度量、日志和跟踪解释了您的数据发生了什么。微软将这一特性描述为提供“为什么”。使用变更分析，您可以跨多个订阅查看资源。

以下是微软列出的一些使用变更分析的常见应用:

*   排除应用程序及其依赖项中的变化
*   调查并确认发生了预期的变化
*   日常监控变化并快速与团队分享
*   与其他 ob 的相关性变化分析
*   使用 Azure 的可服务性数据
*   工作簿
*   调查公制峰值
*   调查谁做出了改变

最好的消息是变更分析是免费提供的。这绝对是您应该花些时间探索的事情，因为它可以很好地减少调查时间，更快地突出问题，并导致更快地解决问题。

## Azure 和 Starlink 联手

Azure Space 于两年前宣布，本月见证了一波新的太空产品，其中包括 Azure Orbital Cloud Access 预览版，以及 Azure Orbital 地面站的普遍可用性。

## 普遍可用:调整对等虚拟网络的大小

如果您使用对等网络，您可能会遇到对等地址不足的情况。你的网络会离线，你必须移除对等，这总是很棘手。

本月,[对等网络的大小调整变得普遍可用](https://azure.microsoft.com/en-au/updates/resizing-of-peered-virtual-networks-is-now-generally-available/),随之而来的是，许多压力离开了大楼。现在，您可以更新地址空间或调整其大小，完全不需要停机，也不需要删除对等关系。

## 高级固态硬盘和标准固态硬盘磁盘存储的更新

在过去，如果您想要增加被管理磁盘的大小，您必须登录，等到您的虚拟机被解除分配，调整磁盘的大小，然后重新启动。在等待的过程中，使用该虚拟机的任何资源都出现了故障，业务功能也受到了影响(或者您确实受到了影响，因为您必须在凌晨两点登录)。

好消息是，微软刚刚宣布[高级和标准固态硬盘现在可以实时调整大小](https://azure.microsoft.com/en-us/updates/generally-available-live-resize-for-premium-ssd-and-standard-ssd-disk-storage/)！通过此更新，您现在可以在不取消分配虚拟机的情况下扩展被管理的磁盘。

因为这是一项新服务，所以有一些限制。它仅适用于 4TB 以下的数据磁盘，不支持 Ultra、共享或 SSD v2 磁盘。您可以使用自己喜欢的方法来访问该功能，无论是 CLI、Powershell、ARM 还是门户。

这就是 Azure 月份的所有头条新闻！

## 想每周了解 Azure 新闻吗？

本周 Azure 是关于 Azure 的每周新闻综述。加入我们的专家主持人，因为他们涵盖了你需要知道的关于过去一周发展的一切，保持简短、有趣和信息丰富。

无论您是刚刚开始您的云之旅，还是您已经了解自己的东西，每个人都有适合自己的东西！