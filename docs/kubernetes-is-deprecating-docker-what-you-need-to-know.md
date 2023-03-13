# Kubernetes 不同意 Docker 的观点:你需要知道的

> 原文：<https://acloudguru.com/blog/engineering/kubernetes-is-deprecating-docker-what-you-need-to-know>

#### 忽必烈是掠夺码头吗？！

一段时间以来，似乎当人们想到集装箱时，他们会想到 [Docker](https://acloudguru.com/course/introduction-to-containers-and-docker) 和 [Kubernetes](https://acloudguru.com/course/kubernetes-deep-dive) 。在构建和运行容器方面，Docker 是大名鼎鼎的，而在管理和编排容器方面，Kubernetes 是大名鼎鼎的。听到 Kubernetes 从 Kubernetes 1.20 版开始不再支持 Docker 作为容器运行时，可能有点令人震惊。

* * *

**加速您的云计算职业生涯**

云专家让你轻松(也很棒)提升你的云事业——即使你对技术完全陌生。查看 [ACG 目前的免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)或[立即开始](https://acloudguru.com/pricing)免费试用。

* * *

所以，我想借此机会谈谈这一变化到底意味着什么，以及 Kubernetes 用户需要为此做些什么。

Docker 有什么变化？

Kubernetes 对 Docker 的贬低实际上并没有听起来那么严重，所以我们来谈谈这里到底发生了什么。

## Kubernetes 正在移除对 Docker 作为**容器运行时**的支持。Kubernetes 实际上并不处理在机器上运行容器的过程。相反，它依赖于另一个叫做**容器运行时**的软件。

容器运行时在主机上运行容器，Kubernetes 告诉每个主机上的容器运行时做什么。实际上，在运行 Kubernetes 时，您可以从各种选项中选择想要使用的容器运行时软件。到目前为止，一个相当流行的选择是使用 Docker 作为容器运行时。

然而，这在未来将不再是一个选项。您仍然可以以与 Kubernetes 相关的其他方式使用 Docker(稍后会详细介绍)，但是您将无法使用 Docker 作为 Kubernetes 下的容器运行时。

为什么是库伯勒掠夺码头？

到目前为止，Kubernetes 一直支持使用 Docker a 容器运行时，那么他们为什么选择停止支持它呢？

## Kubernetes 与所有容器运行时一起工作，这些容器运行时实现了一种称为**容器运行时接口(CRI)** 的标准。这本质上是 Kubernetes 和容器运行时之间的一种标准通信方式，任何支持这种标准的运行时都会自动与 Kubernetes 一起工作。

Docker 没有实现容器运行时接口(CRI)。在过去，容器运行时没有太多好的选择，Kubernetes 实现了 Docker shim，这是一个附加层，用作 Kubernetes 和 Docker 之间的接口。然而，现在有大量的运行时可以实现 CRI，Kubernetes 保持对 Docker 的特殊支持不再有意义。

**[Watch: Kubernetes + Azure，哈希公司之道](https://get.acloudguru.com/kubernetes-azure-hashicorp-way-webinar)**
你有没有想过创造一种标准化的方式来安全地部署你的应用？在 Azure 上使用 HashiCorp 堆栈是一个很好的起点。查看[这个免费的点播网络研讨会](https://get.acloudguru.com/kubernetes-azure-hashicorp-way-webinar)了解更多信息！

到底是怎么回事？

* * *

要真正理解 Kubernetes 反对 Docker 的原因，我们需要更深入一点。

* * *

## 我告诉你一个秘密: **Docker 实际上不是一个容器运行时**！它实际上是一个工具集合，位于名为 **containerd** 的容器运行时之上。

没错！Docker 不直接运行容器。它只是在一个独立的底层容器运行时之上创建了一个更容易被人访问、功能更丰富的接口。当它作为 Kubernetes 的容器运行时，Docker 只是介于 Kubernetes 和 containerd 之间的中间人。

然而，Kubernetes 可以直接使用 containerd 作为容器运行时，这意味着在这个中间人角色中不再需要 Docker。即使在一个 Kubernetes 生态系统中，Docker 仍然可以提供很多东西。只是不特别需要它作为容器运行时。

Docker 往前走的作用是什么？

尽管在 Kubernetes 中不需要 Docker 作为容器运行时，但它仍然可以在 Kubernetes 生态系统和您的工作流中发挥作用。

## Docker 作为开发和构建容器映像以及在本地运行它们的工具，仍然很强大。Kubernetes 仍然可以运行使用 Docker 的**开放容器倡议(OCI)** 图像格式构建的容器，这意味着您仍然可以使用 Docker 文件并使用 Docker 构建您的容器图像。

Kubernetes 也将继续能够从 Docker 注册中心(比如 Docker hub)获取数据。这意味着，一旦构建了映像，Docker 在管理映像方面仍将是一个强有力的竞争者。

总而言之，Docker 将继续是您开发工作流和持续集成(CI)系统的有用工具，即使您在生产中不需要它来运行 Kubernetes 下的容器。

*想获得 K8s 认证吗？阅读我们的[Kubernetes 认证之旅](https://acloudguru.com/blog/engineering/which-kubernetes-certification-path-should-i-take)蓝图。*

集装箱和 CRI-O:码头工人的替代品

* * *

如果您目前在 Kubernetes 环境中使用 Docker 作为容器运行时，您将需要做一些更改。接下来，您可以在您的 Kubernetes 环境中简单地消除 Docker 作为中间人的角色。相反，使用另一个容器运行时，如 [containerd](https://containerd.io/) 或 [CRI-O](https://cri-o.io/) 。

* * *

## 在升级到 Kubernetes 版本删除对 Docker(目前估计在 2021 年末发布)的支持之前，您需要修改(或替换)现有的 Kubernetes 节点，以便它们使用受支持的容器运行时而不是 Docker。从现在开始，您可能希望开始构建任何新节点，以便它们也使用非 Docker 容器运行时。

除此之外，没有什么是真正改变的。您可以继续使用 Docker 构建您的映像，也可以出于开发目的在本地运行容器，或者在您的持续集成(CI)堆栈中运行容器。您也可以继续使用 Docker 注册表来存储和管理您的图像。

如果你有兴趣学习如何在 Kubernetes 旁边使用 containerd，请查看我的新课程,[Kubernetes 简介](https://acloud.guru/overview/introduction-to-kubernetes)。它包含的课程将引导您完成在 Kubernetes 集群中安装和使用 containerd 的过程。

掌握最受欢迎的 Kubernetes 技能

无论您是云新手还是经验丰富的专家，云专家都可以让您轻松(而且非常棒)地提升您的云职业生涯。查看 [ACG 的免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)或立即开始免费试用。

* * *

## 想要更多容器优点吗？看看这些:

A Cloud Guru makes it easy (and awesome) to level up your cloud career — whether you’re new to cloud or a seasoned pro. Check out [ACG’s free courses](https://acloudguru.com/blog/news/whats-free-at-acg) or get started now with a free trial.

* * *

#### Want more container goodness? Check these out: