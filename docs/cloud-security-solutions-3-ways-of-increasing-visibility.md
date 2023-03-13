# 云安全解决方案:提高可见性的 3 种方法

> 原文：<https://acloudguru.com/blog/engineering/cloud-security-solutions-3-ways-of-increasing-visibility>

在本帖中，我们探讨了三种洞察云资源的方法。准备好通过可视化、自动化工作流和 CSPM 产品了解云安全解决方案了吗？让我们直接开始吧。

* * *

**通往更好职业的钥匙**

[立即开始 ACG](https://acloudguru.com/pricing) 通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室来改变你的职业生涯。

* * *

## 可见性和云安全

想象一下:你的团队正在同时进行两个项目。他们需要部署新的应用程序，并且需要定制的测试环境来获得最终用户体验。

从前，一个人或一小群人根据一组静态标准部署所需的资源。因此，对于这个场景，您将向数据中心提交一个票证，指定您的团队需要的服务。然后，数据中心团队将根据预先确定的标准验证和部署必要的资源，并将登录和系统信息发送回用户。

如今，更多的人可以根据一组动态的标准，并基于项目和部署的需要来部署资源。云技术通过使用基于角色的访问控制(RBAC)等[身份和访问管理](https://acloudguru.com/blog/engineering/aws-iam-security-best-practices) (IAM)框架来限制部署，从而允许快速部署任意数量用户的资源。

一个很大的好处是，您现在可以在需要的时候部署所需的资源。了解正在部署什么以及挑战在哪里。

在使用单一云提供商的组织中，至少有三种不同的方式来部署资源。这还没有考虑能够使用这些方法的人数。团队必须能够尽快获得他们需要的资源。

回到你的场景。团队已经准备好部署他们需要的资源。数据中心团队推荐他们放在哪里，每个人都有需要的权限。对于那些了解云工作负载环境的人来说，这个过程只是为接下来的事情做好了准备:云安全。

## 三种云安全解决方案

仅仅部署所需的资源和应用程序是不够的。当资源或应用程序被部署到云环境中时，它很容易受到攻击，尤其是当它具有可公开访问的端点时。那么，云安全工程师(或其他关心此事的网民)应该做些什么呢？

以下是获得对您的云资源的可见性和洞察力的三种方式。这里概述的内置方法和定制方法都有好处。第三种选择试图利用尽可能多的好处。

### 1.内置的可视化和报告

每个主要的云提供商都有内置的可视化功能，您可以在部署资源时使用。微软 Azure 提供了关于虚拟机性能的基本信息(AWS 和 GCP 也是如此)。以下是微软 Azure 提供的度量洞察示例。

[Azure 虚拟机](https://azure.microsoft.com/en-us/services/virtual-machines/)

![](img/c0facb877ea2ea214a45d8e5566432ea.png)

[蔚蓝虚拟网络](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview)

![](img/765671acfc74188af58dfa946ede4cf9.png)

像这样一起使用两种可视化效果会很有帮助，但是它缺少一些必要的上下文。性能峰值可能表示合法流量、拒绝服务(DoS)攻击、内部危害或资源或应用程序故障。

基本信息不足以告诉您确定根本原因。这些内置的可视化和报告是一个良好的开端，但它们是以性能为导向的，通常不能提供足够的关于需要采取的安全措施的信息。

### 2.自定义自动化工作流程

另一种深入你的资源并获得你想要的数据的方法是使用编程服务，如 [AWS Lambda](https://aws.amazon.com/lambda/) 、 [Google Cloud Functions](https://cloud.google.com/functions) ，甚至[Azure Automation](https://docs.microsoft.com/en-us/azure/automation/overview)workflows。这种方法允许检索的数据具有更大的粒度。直接通过查询利用日志数据，然后以您想要的方式可视化它，这非常有帮助。

再加上可以通过代码编程的自定义操作，您就拥有了一个强大的工具。但是，启动和运行这些工作流并维护它们需要大量的工程工作。

下面是使用 [Azure Automation runbooks](https://docs.microsoft.com/en-us/azure/automation/automation-runbook-types) 的情况。

![](img/be1e998ac72ab0c2cd242caa4a21d4d7.png)

### 3.云安全态势管理(CSPM)

CSPM 产品旨在提供内置的可视化和报告，其中包含可用于决策的有意义的数据。它们通常预先配置了基于已知安全最佳实践的选项，以便对您的安全状况进行初步评估。从那里，可以通过云工作负载保护平台(CWPP)对信息采取行动。

多年来，微软开发了多种工具来提供类似 CSPM 和 CWPP 的功能，如 Azure 安全中心和 Azure Monitor。

进一步发展这些产品，[Microsoft Defender for Cloud](https://azure.microsoft.com/en-gb/services/defender-for-cloud/#overview)将 CSPM、CWPP 和多云整合到一个产品中，帮助您获得对云资源的可见性和洞察力。

![](img/9bc737e6995151d1ff6cfc048a99ec41.png)

有兴趣了解更多信息吗？查看我的新[Microsoft Defender for Cloud](https://acloudguru.com/course/introduction-to-microsoft-defender-for-cloud)课程简介，帮助您入门。