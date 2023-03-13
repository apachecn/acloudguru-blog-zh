# 使用 K3s |云专家的 5 个理由

> 原文：<https://acloudguru.com/blog/engineering/5-reasons-to-use-k3s>

你可能听说过 K3s，轻量级的 Kubernetes 发行版。听起来挺酷的，而且绝对[容易安装](https://rancher.com/docs/k3s/latest/en/quick-start/)。另一方面，它的简化性质意味着它可能不像普通 K8s 设置那样可定制或功能强大。那么实际上什么时候应该考虑使用 K3s 这样的东西呢？以下是 K3s 用例的一些想法。如果你发现自己处于这些情况中的任何一种，也许可以试试 K3s！

### 1.您想要一个简单、轻量级的 Kubernetes 开发环境。

可用的开发环境既可以帮助也可以伤害软件开发。以重要方式反映生产条件的快速、通用的环境对于开发人员的生产力至关重要。

K3s 是一个让 Kubernetes 快速简单地启动并运行的好方法，不需要开发人员对 Kubernetes 的内部工作原理有详细的了解。K3s 也不会占用太多本地资源，这使得它成为本地 Kubernetes 开发环境的一个很好的选择。

### 2.你想把库伯内特逼入绝境。

物联网设备和手机等边缘设备在未来的计算中有着特殊而突出的地位，这些设备目前大多运行在 ARM 架构上。K3s 经过优化，可在 ARM 架构上运行。它占地面积小且简单，在更小、资源更受限的边缘计算环境中更易于运行和管理。有了 K3s，协调的容器不再局限于数据中心。

### 3.你想让 Kubernetes 成为你 CI 流程的一部分。

持续集成通常是指在较小的规模上复制生产组件和基础设施。您正在将您的应用部署到 Kubernetes 集群吗？为什么不在一个小型的临时集群上测试它，作为您的 CI 流程的一部分呢？

K3s 在这里可以派上用场。当事情快速、简单和轻量级时，CI 自动化通常会受益，K3s 符合要求。你可以用一个命令在几秒钟内安装它。因此，K3s 很容易作为 CI 自动化流程的一部分进行管理。

* * *

**[Watch: Kubernetes + Azure，哈希公司之道](https://get.acloudguru.com/kubernetes-azure-hashicorp-way-webinar)**
你有没有想过创造一种标准化的方式来安全地部署你的应用？在 Azure 上使用 HashiCorp 堆栈是一个很好的起点。查看[这个免费的点播网络研讨会](https://get.acloudguru.com/kubernetes-azure-hashicorp-way-webinar)了解更多信息！

* * *

### 4.您希望在树莓 Pi 集群上运行 Kubernetes。

最近，每个人似乎都痴迷于在树莓 Pi 硬件上运行 Kubernetes。这些小巧廉价的 Linux 机器已经被用于从[机器人](https://www.raspberrypi.org/blog/how-to-build-raspberry-pi-robot/)到[浇花](https://www.hackster.io/ben-eagan/raspberry-pi-automated-plant-watering-with-website-8af2dc)的各种用途。在最近的几次会议上，我看到了一些令人印象深刻、看起来很酷的 Kubernetes 集群在这些小机器上运行。

但是，尽管 Raspbery Pis 惊人地强大，但与您通常用来运行 Kubernetes 的硬件相比，它们的资源仍然有限。幸运的是，K3s 占用的资源很少，非常适合这种情况。理论上，你可以在最低端的 Raspberry Pi 型号提供的内存上运行 K3s 四次。K3s 甚至在 Raspian Linux 发行版上进行了官方测试！

### 5.你只是想要一个快速简单的 Kubernetes 集群。

K3s 是一个很好的工具，任何时候你想要一个快速简单的 Kubernetes 集群，特别是如果你不太关心定制。K3s 包括打包的附加组件和合理的默认设置，使其开箱即可发挥强大功能。

它易于安装和管理，甚至可以投入生产。在任何需要快速简单的容器编排的情况下，为什么不试试 K3s 呢？

### 想进一步了解 K3s？

K3s 是一个很棒的工具，它使 Kubernetes 在比以前更广泛的场景中变得有用。从物联网设备到开发环境再到树莓 Pis，K3s 让 Kubernetes 在各种新领域都能轻松使用。

如果你有兴趣学习 K3s 的基础知识并亲自动手，请查看我的课程，[K3s 简介](https://acloud.guru/learn/introduction-to-k3s)。这个简短的课程将帮助您快速掌握 K3s 的基础知识，并引导您构建一个简单的 K3s 群集来部署和运行应用程序。