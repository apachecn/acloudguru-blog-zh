# 学习 AWS 安全基础知识的动手实验室

> 原文：<https://acloudguru.com/blog/engineering/hands-on-labs-for-learning-aws-security-essentials>

*这篇文章重点介绍了动手实验，这些实验将帮助你获得建立 AWS 安全技能的实际经验。*

把你的手放在一起。从打响指和拍手，到假装滑动拇指的动作让孩子兴奋不已，手确实派上了用场。手也是学习云技能的最佳途径，比如 [AWS security](https://acloudguru.com/course/aws-security-essentials) 。

在这篇博文中，我们将分享五个 ACG 动手实验室，它们非常适合希望通过所有云专家都需要知道的一些基本知识来提升其 AWS 安全技能的 AWS 学徒和从业者。

这些引导式实验将让您在安全的云环境中完成真实目标的同时，也能轻松上手。

这五个动手实验大约需要三个小时，旨在教您如何应用 AWS 身份和访问管理，以及其他几个 AWS 服务，以解决现实世界中的应用和服务安全管理问题。

准备好了吗？让我们开始学习吧！

* * *

### 查看我们的其他动手实验播放列表

你还要果酱吗？查看 [*瑞恩的云播放列表:学习 AWS 要领的动手实验室*](https://acloudguru.com/blog/engineering/ryans-cloud-playlist-hands-on-labs-for-learning-aws-essentials) *。*
*全押在 Azure 上？调到* [*Lars 的云播放列表:Azure 基础知识动手实验*](https://acloudguru.com/blog/engineering/lars-cloud-playlist-hands-on-labs-for-azure-fundamentals) *。*
*你打倒 GCP 了？点击播放我们的* [*动手实验播放列表，学习 GCP 要领*](https://acloudguru.com/blog/engineering/hands-on-labs-playlist-for-learning-gcp-essentials) *。*

* * *

## AWS 安全要素播放列表

**技能等级:修炼者**
**5 个实验室| 3 个小时**

#### 建议的音乐配对

*注意:要开始下面的动手实验，您需要一个 ACG 帐户。没有户口？不要烦恼！[开始免费试用](https://acloudguru.com/pricing)。或者注册一个免费帐户，开始学习[本月的一批免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)，包括我们的 [AWS 安全基础课程](https://acloudguru.com/course/aws-security-essentials)和其他 AWS-一些 AWS 内容，如 [Amazon DynamoDB Deep Dive](https://acloudguru.com/course/amazon-dynamodb-deep-dive) 和[如何正确保护一个 S3 桶](https://acloudguru.com/course/how-to-properly-secure-an-s3-bucket)。*

* * *

**[保护您的 AWS 环境](https://get.acloudguru.com/securing-aws-environment-webinar)** 在[这个免费的点播式网络研讨会](https://get.acloudguru.com/securing-aws-environment-webinar)中，您将了解如何从零开始保护复杂的 AWS 环境，并了解如何审计和保护 AWS 帐户。

* * *

**1。**[**AWS 身份与访问管理(IAM)简介**](https://acloudguru.com/hands-on-labs/introduction-to-aws-identity-and-access-management-iam-vkgm)

**时长** : 45 分钟

**目标**:

*   将用户添加到适当的组中
*   使用 IAM 登录链接以用户身份登录

**概述** : AWS 身份和访问管理(IAM)允许 AWS 客户管理其帐户和 AWS 内可用 APIs 服务的用户访问和权限。IAM 可以管理用户和安全凭证，并允许用户访问 AWS 资源。

在[这个动手实验](https://acloudguru.com/hands-on-labs/introduction-to-aws-identity-and-access-management-iam-vkgm)中，您将了解 IAM 的基础。我们将重点讨论用户和组管理，以及如何使用 IAM 管理的策略分配对特定资源的访问。我们将学习如何找到登录 URL，AWS 用户可以在那里登录到他们的帐户，并从现实世界的用例角度对此进行探索。

已经是 ACG 会员了？试试这个实验室[这里](https://learn.acloud.guru/handson/4b620748-f44f-408a-a42b-f727a208e952)。

* * *

**2。** [**使用组和策略管理 AWS IAM 用户权限**](https://acloudguru.com/hands-on-labs/managing-aws-iam-user-permissions-using-groups-and-policies)

**持续时间** : 30 分钟

**目标**:

*   创建客户管理的策略
*   创建通过客户管理的策略控制的组
*   将用户分配到一个组

**概述**:在[这个动手实验](https://acloudguru.com/hands-on-labs/managing-aws-iam-user-permissions-using-groups-and-policies)中，我们做了一点角色扮演。你是一名安全工程师，为一家新成立的公司工作，该公司开设了一家网上书店，出售稀有和古董书籍。创始人需要您的帮助，为她的开发团队设置适当的访问权限。为了提供访问并确保适当的安全措施到位，您将使用 AWS 身份&访问管理(IAM)。您将使用策略对用户进行分组并为开发人员组分配权限。

*ACG 已经是会员了？在这里开始这个实验室[。](https://learn.acloud.guru/handson/4b52d9c3-b09d-4dd5-8117-42c67bc26354)*

* * *

**3。** [**在 AWS**](https://acloudguru.com/hands-on-labs/create-and-configure-basic-vpc-components-in-aws) 中创建和配置基本 VPC 组件

**持续时间** : 30 分钟

**目标:**

*   创造一个 VPC
*   创建互联网网关
*   编辑主路由表
*   创建网络访问控制列表(NACL)并关联它。
*   创建两个公共子网

**概述** : AWS 网络由许多不同的组件组成。理解这些组件之间的关系是理解 AWS 整体功能和能力的重要部分。在[这个动手实验](https://acloudguru.com/hands-on-labs/create-and-configure-basic-vpc-components-in-aws)中，您将创建一个 VPC，其中包含一个互联网网关和跨多个可用性区域的子网。

*签约进 ACG？在这里启动这个实验室[。](https://learn.acloud.guru/handson/344672a2-6d75-449f-98c3-6d682b481565)*

* * *

[![](img/aa563ce93b787834c7c648eaec24feaa.png)](https://go.acloudguru.com/Leaders-Cloud-Security-Webinar)

**[看点:领导需要了解哪些关于云安全的知识](https://go.acloudguru.com/Leaders-Cloud-Security-Webinar?ajs_aid=8b2cc73f-c0e0-442b-ba6d-0eb362250ebb)**
你的业务在云端安全吗？答案很大程度上取决于你。观看 Mark Nunnikhoven 的[免费点播网络研讨会](https://go.acloudguru.com/Leaders-Cloud-Security-Webinar)，他将解决云安全的关键问题。

* * *

**4。** [**AWS 安全精要——网络分段实验室**](https://acloudguru.com/hands-on-labs/aws-security-essentials-network-segmentation-lab)

**持续时间** : 90 分钟

**目标**:

*   配置安全组
*   配置网络访问控制列表(NACLs)

**概述**:在[这个动手实验](https://acloudguru.com/hands-on-labs/aws-security-essentials-network-segmentation-lab)中，您将使用安全组和网络访问控制列表对网络进行分段，以便只有必要的流量可用。您将获得使用安全组和网络访问控制列表来保护多层应用程序的不同层的经验。

*ACG 会员？封锁这个实验室[这里](https://learn.acloud.guru/handson/c8f78dd1-2c83-4058-b480-cf96a4e78e13)。*

* * *

**5。** [**AWS 安全要点——VPC 端点和保护 S3**](https://acloudguru.com/hands-on-labs/aws-security-essentials-vpc-endpoints-and-securing-s3)

**持续时间** : 60 分钟

**目标**:

*   保护好 S3 桶
*   SSH 到应用服务器 1
*   创建 VPC 端点

**概述** : AWS S3 和 [DynamoDB](https://acloudguru.com/course/amazon-dynamodb-deep-dive) 是出色的托管服务。(有人甚至说 [S3 是有史以来最伟大的云服务](https://acloudguru.com/blog/engineering/brazeal-in-praise-of-s3-the-greatest-cloud-service-of-all-time)。)这些服务使您可以专注于重要的事情，而 AWS 则专注于后端流程。不幸的是，因为这些服务是由 AWS 管理的，它们需要流量离开您的受保护的 VPC 才能被访问。输入 VPC 端点！

VPC 端点允许您在 VPC 内创建端点，以保持 VPC 资源和这些 AWS 服务之间的专用链路上的流量。使用您自己的 VPC·CIDR 系列产品私下访问 DynamoDB 和 S3，对于维护一个安全的环境，抵御黑客、数据窃贼和其他不受欢迎的人是至关重要的。

在[这个动手实验中，](https://acloudguru.com/hands-on-labs/aws-security-essentials-vpc-endpoints-and-securing-s3)您将配置一个 VPC 端点并利用加密来确保您的数据安全。

*登录您的 ACG 帐户？在这里动手[。](https://learn.acloud.guru/handson/a8e77f8f-d69c-4983-b554-aeb9504de07b)*

* * *

## 学习 AWS 安全性的建议后续步骤

*   一旦你把这些实验归结为一门科学，你就可以把难度提高一个档次。使用我们新的[挑战模式](https://acloudguru.com/blog/news/introducing-challenge-mode-for-a-cloud-gurus-hands-on-labs)选项，可以进行上述许多实验。

*   不确定下一步去哪里？查看我们的 [AWS 安全](https://acloudguru.com/learning-paths/aws-security)学习路径，了解在您从新手到专家的过程中需要学习什么来不断提高您的 AWS 安全技能。

### 与安全相关的资源

* * *

## 锁定您的 AWS 安全技能

学得更快。动作快点。[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。