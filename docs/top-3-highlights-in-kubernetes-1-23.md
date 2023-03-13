# Kubernetes 1.23 中的三大亮点|云专家

> 原文：<https://acloudguru.com/blog/engineering/top-3-highlights-in-kubernetes-1-23>

在新的一年里，Kubernetes 有什么新内容？在本帖中，我们将看看最近发布的 Kubernetes 1.23 中最显著的三个特性。此外，我们将讨论 2022 年 K8s 可能会出现历史上最大的贬值，以及如何为此做准备。另外，看看包容性命名倡议。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## Kubernetes 1.23 中的 3 大增强功能

这个月围绕 Kubernetes 的最大新闻是 Kubernetes 1.23 的 T2 发布。

这是 2021 年的第三个也是最后一个版本，代号为“下一个前沿”——因为我们都喜欢《星际迷航》的主题，也因为增强的数量。

总共有 47 项增强，其中 11 项升级到稳定版，17 项升级到测试版。以下是我最喜欢的三个增强选项。

### 1.水平 Pod 自动缩放器的 v2

首先，水平吊舱自动定标器的 v2 进入 GA。这是迈向更成熟、更全面的自动扩展的真正一步。

我不了解你，但我总觉得最初的 v1 实现有点。。。好吧，笨笨。这也是非常基本的。比如主要根据 CPU 和内存使用情况进行扩展。

嗯，v2 API 对自定义指标有适当的支持，所以也许您的应用程序关心队列大小或者队列的响应时间？没问题！自定义指标的帮助。

此外，它可以评估和扩展多个指标，您可以更好地控制放大和缩小行为，甚至可以获得稳定窗口，以防止在湍流期间发生翻转。都是好东西。

### 2.豆荚安全测试

我们也看到 Pod 安全升级到测试版。现在，这是人们期待已久的笨重的旧 PodSecurityPolicies 对象的替代品。我猜它还没有完全在这里，因为这只是测试版，但我已经喜欢上了我从清晰和简单的角度看到的东西。

它被实现为一个内置的准入控制器，根据一组 Pod 安全标准来评估新的 Pod。然后，它决定是允许还是拒绝它们加入集群。

幕后有很多细节，我们可能会在稳定之前看到调整。但是，这是一个开箱即用的解决方案，使得根据最佳实践评估新的 pod 变得更加容易。这在很大程度上是朝着正确方向迈出的一步。

### 3.双栈 IPv4/IPv6 网络

最后但同样重要的是，在我的选择中，双栈网络正式上市。

这意味着一个 Kubernetes 集群，包括 Pods 和服务，可以同时运行 IPv4 和 IPv6。而且是生产级的。

现在有几个先决条件:

*   您的节点需要可路由的 IPv4 和 IPv6 地址

*   你的 CNI 插件需要支持双栈

但是如果您勾选了这些框，Kubernetes 可以同时在同一个集群上使用 IPv4 和 IPv6！

对于任何迁移到 IPv6 的人来说，这显然是个好消息。然而，这对物联网来说是一件大事，成千上万的设备需要自己的 IP。

## Kubernetes 的大降价即将来临

好了，这是对 2022 年的一点预测——或者可能是对即将到来的事情以及如何解决它们的一个提醒。

随着 Kubernetes 的成熟，一些功能得到了调整和改进，最终旧版本需要删除。

Kubernetes 有一个折旧政策，基本上是在将来某个东西要被删除时给我们一个提醒。我们通常会知道它会在哪个版本中消失。另外，我们还会收到命令行警告之类的东西。

嗯，2022 年可能会看到 Kubernetes 历史上迄今为止最大的功能或技术移除。

之前， [Docker 在 1.20 版本中作为运行时被弃用](https://acloudguru.com/blog/engineering/kubernetes-is-deprecating-docker-what-you-need-to-know)。当我写这篇文章时，[将在 1.24 中被移除。](https://kubernetes.io/blog/2021/11/12/are-you-ready-for-dockershim-removal/)

现在考虑到我们已经在 1.23 上了，那就不远了。它不是唯一被移除的东西。FlexVolumes 将在 1.25 中消失。

我认为，在 2022 年及以后，我们将会看到越来越多的这种情况。

我认为我们需要在宣布反对意见后立即着手解决。就像我有一个稳定的涓涓细流的人告诉我，担心被否决的功能会停止工作。每次我都在想，“为什么你要等到最后一分钟？”

Kubernetes 是许多企业核心的重要基础设施。我们真的想掩盖反对意见，并希望它们永远不会发生吗？

如果我们这样做，我们会受到伤害。

所以，把它作为你的新年决心，当它们一宣布就解决它们！我想你会因此过得更好。

* * *

### *免费 Kubernetes 培训*

*查看一月份[ACG](https://acloudguru.com/blog/news/whats-free-at-acg)的免费课程，其中包括我们[为 Kubernetes](https://acloudguru.com/course/designing-applications-for-kubernetes)课程设计申请。只有这个月免费。不需要信用卡，不开玩笑！*

* * *

## 包容性命名倡议

坚持 2022 年的主题，我真的希望[包容性命名倡议](https://inclusivenaming.org/)能够扩大并产生影响。

包容性命名倡议旨在从技术世界中移除潜在的有害词汇和术语。

举个例子，我正在出版 2022 版的快速入门 Kubernetes 和 Kubernetes 书，部分更新涉及删除对 masters、白名单和反向列表的引用，以及中止。所有这些都有可能让一些人感到不安的含义。我明白。

虽然更新句子和图表花了一些时间，但老实说，我非常乐意这样做，我也很高兴我这样做了。这是一个简单而有价值的事业，我希望它在 2022 年获得牵引力。我知道，举个例子，官方的 Kubernetes 文档已经到处都是了。

* * *

**[观看:自动化 Kubernetes 安全](https://go.acloudguru.com/automating-kubernetes-security-webinar)** [](https://get.acloudguru.com/aws-cloud-formation-power-user-webinar) 在[这个免费的点播网络研讨会](https://go.acloudguru.com/automating-kubernetes-security-webinar)中，学习如何用 Pod 安全策略来增强您的 K8s 安全。我们将向您展示它们是如何工作的，以及在一个真实的 Kubernetes 集群中实现它们的样子。

* * *

## 跟上 K8s

本月 [Kubernetes 本月](https://acloudguru.com/videos/kubernetes-this-month)到此为止。注意安全，我们下个月再见——同一时间，同一地点。

*想要了解 Kubernetes 的所有信息？在推特[上关注奈杰尔](https://twitter.com/nigelpoulton)或者在这里关注他[。在 YouTube 上订阅一位云计算专家](https://nigelpoulton.com/),获取定期更新、分析和各种精彩内容。你也可以在[脸书](https://www.facebook.com/acloudguru)上喜欢 ACG，在[推特](https://twitter.com/acloudguru)上关注我们，或者在[不和谐](http://discord.gg/acloudguru)上加入对话！*