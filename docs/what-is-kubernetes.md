# 什么是 Kubernetes？

> 原文：<https://acloudguru.com/blog/engineering/what-is-kubernetes>

如果您正在使用容器，那么您很可能听说过 Kubernetes，或 K8s。简单地说，Kubernetes 是一个管理容器的开源工具。让我们进一步了解它是什么以及它能做什么。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

容器是构建可移植应用程序的好方法，但是当您有许多运行在复杂基础设施上的容器时，您可能需要一些工具来帮助您管理它们。Kubernetes 是当今领先的容器管理工具。根据云计算原生计算基金会的调查， [83%](https://www.cncf.io/wp-content/uploads/2020/11/CNCF_Survey_Report_2020.pdf) 的受访者在生产中使用 it。

你在做什么？

根据 Kubernetes.io 的说法，Kubernetes 是“一个自动化部署、扩展和管理容器化应用的开源系统。”因此，如果您在容器中运行应用程序，Kubernetes 是一个旨在使您的生活更加轻松的工具。你的应用程序越大越复杂，Kubernetes 就越有用。

## 所以，你有一堆计算资源，可能是服务器或云资源。您想开始部署容器，但是随着应用程序的增长，手动管理会变得困难。把它想象成在你的厨房里做饭。如果你自己做，你必须考虑每一个细节，比如如何和何时混合原料，煮多长时间，以及之后的清理。但是如果你去餐馆，你只需要问你想要什么，餐馆会处理所有的细节。

用 Kubernetes 管理容器有点像去餐馆。不要问自己，“我应该在哪台服务器上运行这个容器？”或者“现在哪台服务器的可用资源最多？”你只需要告诉 Kubernetes 你想运行一个容器，它就能处理所有其他的事情。

什么是 Kubernetes 集群？

Kubernetes 使用一个称为 Kubernetes 集群的概念来处理所有这些问题。Kubernetes 集群是可用计算资源的集合。Kubernetes 知道集群中的所有资源，当您想要运行一个容器时，它会自动为该容器分配资源，并使用这些资源处理运行和管理容器的过程。

## Kubernetes 集群有控制平面和工作节点。控制平面节点用于控制和管理集群本身。工作节点运行实际的应用程序容器。当我想用 Kubernetes 运行一个容器时，我只需告诉一个控制平面节点，“嘿，我想运行一个容器！”Kubernetes 然后将该容器分配给一个节点并运行它。控制平面和工作节点的集合构成了群集。

Kubernetes 还做什么？

这些只是 Kubernetes 功能的基础。Kubernetes 包括许多不同的功能来帮助您解决各种挑战，包括:

## 允许您的容器相互通信的网络

配置管理，使您能够将配置传递到您的容器化应用程序

*   推出新版本代码的部署功能
*   允许您为应用程序分配更多或更少资源的扩展
*   它能做的远不止这些。
*   我希望这能让你对 Kubernetes 有所了解。如果你想接触 Kubernetes 的环境，请访问 Minikube。它可以帮助您快速方便地让 Kubernetes 在本地机器上运行。

如果你想和一位云专家一起深入了解 Kubernetes，我们的[Kubernetes 简介](https://learn.acloud.guru/course/introduction-to-kubernetes/dashboard)课程是一个很好的起点。要了解更多关于 Kubernetes 认证的信息，请查看我们的[集装箱认证指南](https://acloudguru.com/blog/engineering/which-container-development-certification-is-best-for-me)。

I hope that gives you an idea of what Kubernetes is all about. If you want to get your hands on a Kubernetes environment, check out [Minikube](https://minikube.sigs.k8s.io/docs/). It can help you get Kubernetes running on your local machine quickly and easily.

If you want to dive deeper into Kubernetes with A Cloud Guru, our [Introduction to Kubernetes](https://learn.acloud.guru/course/introduction-to-kubernetes/dashboard) course is a great place to start. And to learn more about the world of Kubernetes certifications, check out our [containers certification guide](https://acloudguru.com/blog/engineering/which-container-development-certification-is-best-for-me).