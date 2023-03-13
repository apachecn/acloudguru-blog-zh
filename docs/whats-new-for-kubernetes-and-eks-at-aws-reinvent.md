# Kubernetes 发行版:哪个适合你？|云专家

> 原文：<https://acloudguru.com/blog/engineering/whats-new-for-kubernetes-and-eks-at-aws-reinvent>

所以你的组织决定采用 Kubernetes？恭喜你！您将能够利用各种特性来增加系统的开发、部署、测试、弹性和可观察性的价值。您所需要做的就是启动并运行您的 Kubernetes 集群，对吗？

哦。你还没决定在哪里建立 Kubernetes？也许只要快速谷歌搜索一下。。。你感到不知所措了吗？

似乎每个人都有一个新的 Kubernetes 产品，他们声称会简化你的生活，解决你所有的问题，并在它的时候洗碗。

哪个 Kubernetes 发行版最适合你？让我们快速浏览一下你可能遇到过的一些名人，并试着解开一些谜团。

## Kubernetes 云管理选项

三大云提供商都有自己托管和管理的 Kubernetes 解决方案。

亚马逊有[弹性 Kubernetes 服务](https://acloudguru.com/course/eks-basics)，Azure 有 [Azure Kubernetes 服务](https://acloudguru.com/course/aks-basics)，Google 有 [Google Kubernetes 引擎](https://acloudguru.com/course/gke-basics)。(如果你需要复习基础知识，你现在可以免费查看我们的 [EKS 基础知识](https://acloudguru.com/course/eks-basics)和 [GKE 基础知识](https://acloudguru.com/course/gke-basics)课程，作为我们每月[免费课程](https://acloudguru.com/blog/news/whats-free-at-acg-june-2021)的一部分。只需[注册一个自由层账户](https://acloudguru.com/pricing)。)

这里有更多关于 AWS、Azure 和 GCP 的托管 Kubernetes 服务的比较。

* * *

Kubernetes 已经被部署在一些最大的云计算项目中。开始学习谷歌 Kubernetes 引擎( [GKE](https://acloudguru.com/course/google-kubernetes-engine-gke-beginner-to-pro) )的完整基础知识，成为一名专家！

* * *

具体细节因云而异，但如果您的团队刚刚开始使用 Kubernetes，并且可能没有管理 Kubernetes 基础架构所有复杂性的经验，这些选项可能是一个不错的选择。请注意:如果你不小心的话，这些服务可能会很贵。

*考虑 Kubernetes 认证？以下是如何[选择适合你的 Kubernetes 认证途径](https://acloudguru.com/blog/engineering/which-kubernetes-certification-path-should-i-take)。*

## Kubernetes 企业选项

还有其他的 Kubernetes 发行版和容器管理平台——像 Redhat 的 [Openshift](https://acloudguru.com/course/introduction-to-openshift) 、 [Docker Swarm](https://acloudguru.com/hands-on-labs/setting-up-docker-swarm) 和 [Cloud Foundry](https://acloudguru.com/course/cloud-foundry-certified-developer) 的 kube cf——已经在大型企业中找到了牵引力。这些服务有强大的企业支持，来自广泛信任的公司，并具有对大型企业有吸引力的许可选项。

这些解决方案可能非常有效，尤其是如果您的组织已经在使用某个提供商的工具。将集群连接到现有服务通常很简单。然而，他们可能会远离传统的 Kubernetes，这可能会带来知识和培训方面的挑战。

## Kubernetes 开源管理选项

随着我们进入越来越少管理的 Kubernetes 选项，我们发现自己处于受管理的开源层。像 RKE 这样的发行版和像 Kops T1 和 kube ADM T3 这样的工具允许你在你管理的基础设施上运行 Kubernetes，但是他们的目标是让这个过程变得更简单。

如果您不想使用托管或托管解决方案，这些解决方案是理想之选，这通常是出于安全或成本原因。这些工具允许您管理 Kubernetes 的安全配置文件，而不是信任云提供商或供应商。因为它们都是开源的，你可以节省许可费用。当你还没有处于云环境中时，这些对 Kubernetes 来说也是很好的解决方案。

请记住:当你负责基础设施时，*你负责基础设施。请关注那些补丁和更新。*

* * *

**[观看:Kubernetes + Azure，HashiCorp way](https://get.acloudguru.com/kubernetes-azure-hashicorp-way-webinar)**
*在这个[免费点播的 webina](https://get.acloudguru.com/kubernetes-azure-hashicorp-way-webinar) r 中，HashiCorp 开发者倡导者 Taylor Dolezal 展示了使用 Terraform、Vault 和 Waypoint 来增强您的 Kubernetes 集群的潜力！*

* * *

## DIY 选项

你也可以选择来硬的[Kubernetes](https://acloudguru.com/course/kubernetes-the-hard-way)。这是给不依赖任何人的坚强的生存主义者的！

虽然手动引导和管理 Kubernetes 集群，不需要任何脚本，是了解 Kubernetes 如何工作的一个很好的方式，但手动做这种可以通过脚本编写的工作与 vOps 的精神背道而驰。所以这是一个很好的学习挑战。但是如果你打算手工支持生产级的 Kubernetes，要知道:你的才能有更好的用途。

## 外围选项

最后，有几个小小的例外:K3s 和 Minikube。我说的小，是指*小*。

*   K3s 设计用于在资源受限的环境中运行生产级 Kubernetes。使用 K3s，您可以在树莓 Pi 上运行 Kubernetes。(想多了解一点？以下是[使用 K3s](https://acloudguru.com/blog/engineering/5-reasons-to-use-k3s) 的 5 个理由。)

*   另一方面，Minikube 是为在本地运行 Kubernetes 而设计的，因此对于 Kubernetes 的学习和开发来说非常好。

这些对于运行您的企业集群可能不太好，但是它们都很好地支持了利基用例。

## 集群，到处都是集群

希望现在你对进入 Kubernetes 之旅的第一步有了更好的准备——做好准备。

虽然我们谈到了一些流行的选择，但这份清单绝不是详尽无遗的。根据您的组织，也有可能您不会使用单一的 Kubernetes 发行版。您可能会发现您正在为不同的用例管理几个 Kubernetes 设置——如果您愿意的话，是一个集群。

幸运的是，这也有一个工具。Rancher 是一个开源工具，可以帮助管理多个 Kubernetes 集群——安全挑战、操作难题和部署复杂性。要了解 Rancher 如何帮助您的组织实现多集群，请查看 ACG 的[Rancher 简介](https://acloudguru.com/course/introduction-to-rancher)。

* * *

## 掌握最受欢迎的技能

无论您是云新手还是经验丰富的专家，云专家都可以让您轻松(而且非常棒)地提升您的云职业生涯。查看 [ACG 的免费课程](https://acloudguru.com/blog/news/whats-free-at-acg-june-2021)或立即开始免费试用。