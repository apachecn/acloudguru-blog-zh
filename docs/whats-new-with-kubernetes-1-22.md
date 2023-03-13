# Kubernetes 1.22:新特性和反对意见|云专家

> 原文：<https://acloudguru.com/blog/engineering/whats-new-with-kubernetes-1-22>

你好，云大师们！我是 Nigel Poulton，这是关于 Kubernetes 最新动态的每月更新。在本帖中，我们将仔细看看 Kubernetes 1.22:达到新的高峰。我们将深入研究 etcd 3.5 采用等新特性，以及在进行转换之前需要注意的不推荐使用的特性。此外，我们还将为您带来五个不容错过的 K8s 相关重要公告。

想了解更多？请继续阅读！

## Kubernetes 1.22:达到新高峰发布

这是 2021 年的第二次发布，也是新的延长发布周期的第一次。2021 年 7 月，发布团队合并了一个 Kubernetes 增强提案，将 Kubernetes 每年的发布数量从四个减少到三个。这是新的更长周期下的第一次。

好吧，发布版本是 1.22，它的代号是“达到新的高峰。”

在数字方面，它总共打包了 53 个增强功能。

*   其中 13 个功能升级到稳定，因此被视为生产就绪。
*   24 个已经转移到测试版。
*   我们欢迎 alpha 版的 16 个新特性。

但是和新东西一样重要的是即将消失的东西。我们有三个功能被弃用，10 个以前被弃用的功能实际上被删除了。

在新功能方面，我认为对我来说最大的变化是切换到 etcd 3.5。

今年早些时候，etcd 3.5 的发布意味着 Kubernetes 的重大改进——尤其是更大、更繁忙的 Kubernetes 集群，在这些集群中，etcd 通常是性能的瓶颈。

当时，我们说尽管 etcd 3.5 已经推出，但我们必须等待 Kubernetes 项目采用它。嗯，他们没有让我们等太久，因为我真的很高兴 Kubernetes 1.22 将与 etcd 3.5 一起发布。当然，这主要是幕后的改进。但是它们涵盖了从安全性和日志记录到急需的性能改进的方方面面。

* * *

**[观看:自动化 Kubernetes 安全](https://go.acloudguru.com/automating-kubernetes-security-webinar)** [](https://get.acloudguru.com/aws-cloud-formation-power-user-webinar) 在[这个免费的点播网络研讨会](https://go.acloudguru.com/automating-kubernetes-security-webinar)中，学习如何用 Pod 安全策略来增强您的 K8s 安全。我们将向您展示它们是如何工作的，以及在一个真实的 Kubernetes 集群中实现它们的样子。

* * *

另外，在 GA 或稳定方面，外部凭证插件在 10 个版本的测试后终于稳定了。Windows 对 CSI 插件的支持也正式发布。

在 alpha 方面，我认为 seccomp 的交换内存支持和默认配置文件在将来会很重要。

在交换内存方面，当然这只是在 alpha 中，但是支持启用交换内存的集群节点的工作正在进行中。

然后在 seccomp 方面:seccomp 显然是一种用于提高安全性的 Linux 技术，创建默认 seccomp 配置文件的工作正在进行中，这将为我们提供比当前大开大门的方法更好的安全性(开箱即用)。再说一次，现在还只是阿尔法。但这绝对是朝着正确方向迈出的一步。

最后但同样重要的是(如果你不做好准备，可能会有严重的影响), 10 个不推荐使用的特性最终被删除了，很明显它们将不再工作。

完整的名单显示在 Kubernetes 网站上。但是对我来说，入口和自定义资源定义是很重要的，因为它们被广泛使用。所以，如果你正在使用其中的任何一个，在你切换到 Kubernetes 1.22 之前，你需要计划，计划，再计划。

## 挂钩毕业 cncf

另一个你不想错过的重大新闻是……Linkerd，一个流行而简单的服务网络，[毕业于 CNCF](https://linkerd.io/2021/07/28/announcing-cncf-graduation/) 。我喜欢他们的一句标语:“在一个因复杂而臭名昭著的空间里，简单的胜利。”随着服务网格越来越成为生产 Kubernetes 部署不可或缺的组成部分，Linkerd 绝对值得一看。尤其是如果你想要简单。

## Istio 发布 1.11 版本

在服务网格领域，Istio [宣布了【1.11 版本，包括即将测试的 CNI 插件在内的特性和改进有助于解决围绕 init 容器的一些安全需求。和外部控制平面的 beta 支持，其中 istio 控制平面可以托管在外部集群中。](https://istio.io/latest/news/releases/1.11.x/announcing-1.11/)

## GKE 负载平衡器正常运行时间检查

在公共云领域，谷歌[宣布](https://cloud.google.com/blog/products/operations/verify-gke-services-are-up-with-dedicated-uptime-checks) GKE 负载平衡器正常运行时间检查。我喜欢这样的东西，因为这对于在生产环境中运行 Kubernetes 至关重要:例如，监控服务的正常运行时间在生产环境中非常重要，因此 Google 为 GKE 环境中的负载平衡器添加专门的正常运行时间检查是朝着积极方向迈出的一大步。

## eBPF 基金会

在网络领域，我们在前几集已经说过，eBPF 真正开始震撼网络世界，一些人正在尝试与 Kubernetes 进行潜在的改变游戏规则的集成。

我们谈论的东西就像一个具有智能的可编程网络，以了解 Kubernetes 并为之优化。

无论如何，一些主要的行业参与者刚刚宣布了 eBPF 基金会来推动这种东西向前发展。该基金会将存在于 Linux 基金会中。它将推动 eBPF 的开发和采用，同时也组织和主办活动。

这就是本月的 Kubernetes。注意安全，我们下个月再见——同一时间，同一地点。

### 相关 K8s 资源

*想要了解 Kubernetes 的所有信息？你可以在推特[上关注奈杰尔](https://twitter.com/nigelpoulton)或者在这里关注他[。在 YouTube 上订阅一位云计算专家](https://nigelpoulton.com/),获取定期新闻更新、分析和各种精彩内容。你也可以在[脸书](https://www.facebook.com/acloudguru)上喜欢 ACG，在[推特](https://twitter.com/acloudguru)上关注 ACG，或者在[不和谐](http://discord.gg/acloudguru)上加入对话！*

* * *

## 在云中开启更好的职业生涯

学得更快。动作快点。[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。