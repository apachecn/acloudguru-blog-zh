# 为 AZ-140 考试做准备的 17 个动手实验

> 原文：<https://acloudguru.com/blog/engineering/17-hands-on-labs-to-prepare-you-for-the-az-140-exam>

不言而喻，在过去几年中，对远程工作能力的需求急剧增加。这意味着对能够快速部署可大规模运行的企业级解决方案的 IT 专业人员的需求也在增加。

幸运的是，微软的 Azure 虚拟桌面非常适合虚拟桌面基础架构。

通过成为这种按需云服务的专家，并获得像[微软认证:Azure 虚拟桌面专业](https://docs.microsoft.com/en-us/certifications/azure-virtual-desktop-specialty/)这样的微软 Azure 认证，你将进入职业生涯的高速档。

在本文中，我们探索了从 [AZ-140:配置和操作微软 Azure 虚拟桌面](https://docs.microsoft.com/en-us/certifications/exams/az-140)考试中可以期待什么，这是获得 Azure 虚拟桌面专业证书的要求的一部分。我们还为您提供最佳实践实验室的建议，以帮助您准备考试。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过微软 Azure 认证课程和实际动手实验室改变您的职业生涯。

* * *

## AZ-140 考试是给谁的，考试内容是什么？

如果你是一名桌面管理员，希望设计和管理 Azure 虚拟桌面体验和远程应用，AZ-104 可能是你的正确选择。

我建议在购买 AZ-140 之前，先了解一下 AZ-104:微软 Azure 管理员。这将为您在 Azure cloud 中实现、管理和监控身份和治理打下良好的基础。

[根据微软](https://docs.microsoft.com/en-us/certifications/exams/az-140)的说法，要获得 AZ-140，您需要在虚拟化、网络、身份、存储和弹性方面有一些经验。您还需要能够管理终端用户桌面环境。

考试本身涵盖以下领域:

*   规划和实施 Azure 虚拟桌面基础架构(40–45%)
*   规划和实施身份和安全性(15–20%)
*   规划和实施用户环境和应用程序(20–25%)
*   监控和维护 Azure 虚拟桌面基础架构(10–15%)

查看 [AZ-140 学习指南](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4MFST)了解每个领域涵盖的更详细的分类。

你也可以利用[微软的考试沙箱](https://acloudguru.com/blog/engineering/prep-for-azure-certification-with-microsofts-new-exam-sandbox)来提前熟悉微软考试的外观和感觉。

## 如何准备 AZ-140 考试？

当我们在一个云专家这里为微软 Azure 认证创建课程时，我们喜欢提供大量的实验室来补充我们的课程。但不幸的是，这对于 Azure 虚拟桌面来说是不可能的。

所以记住这一点——随着[基于表现的实验室测试](https://docs.microsoft.com/en-us/learn/certifications/posts/performance-testing-is-coming-to-microsoft-exams)进入所有微软 Azure 认证考试——我想给你带来一种不同类型的考试学习指南。以一张*所有*我建议在考试前练习的实际操作任务的清单的形式。是的，全部 17 个。可以说，这是你的实验学习指南！

有一点需要注意:对于你的考试，微软假设你能够使用几种不同的方法完成这些任务。这包括 Azure 控制台、Powershell、Azure CLI 和 ARM 模板。但是对于基于性能的实验室测试，您可以使用您喜欢的任何方法来完成所需的任务。

好了，去实验室。

### 准备 AZ-140 考试的推荐实验室

1.  部署 Azure 虚拟桌面。尽可能多次这样做。
2.  不要忘记练习部署验证主机池！
3.  不使用 Azure 虚拟桌面向导删除和创建工作区和应用程序组。
4.  部署 Azure Active Directory 域服务，并将其用于 Azure 虚拟桌面。特别提示:微软喜欢在考试场景中使用 Azure AD Domain 服务！
5.  创建一个“黄金”会话主机映像，并将其放在 Azure 存储和 Azure 计算库中。
6.  从存储在 Azure Storage 和 Azure Compute Gallery 中的托管映像部署会话主机。
7.  练习手动安装 Azure 虚拟桌面代理，并向现有主机池添加新的会话主机。
8.  使用不同的应用程序组部署多个 RemoteApps
9.  微软在 FSlogix 上是巨大的，所以确保用各种不同的配置进行测试。别忘了云缓存！
10.  部署条件访问和多因素身份验证，并试验不同的条件访问设置。
11.  使用 Azure 防火墙从 Azure 虚拟桌面管理出站 internet。
12.  为 Azure 虚拟桌面配置基于角色的访问控制(RBAC)。这样做，直到你记住内置的角色和它们的能力。
13.  配置各种远程桌面协议(RDP)属性，并测试结果。
14.  使用 MSIX 应用程序连接打包和部署至少一个应用程序。
15.  在会话主机上部署 Microsoft Defender Antivirus(现在称为 Microsoft Defender for Endpoint)。
16.  练习在 Azure 虚拟桌面会话主机上安装 Microsoft Office、OneDrive 和团队。这包括配置团队 AV 重定向。
17.  练习为 Azure 虚拟桌面配置自动化，包括自动缩放、自动启动/停止、连接时启动虚拟机和排出模式。

如果你能使用你喜欢的方法完成所有这些任务而不用参考文档，你就能顺利通过 AZ-140 考试。即使是基于性能的实验室测试！

要获得更多关于备考的建议，请查看我的 [AZ-140:微软认证 Azure 虚拟桌面专业](https://acloudguru.com/course/az-140-microsoft-certified-azure-virtual-desktop-specialty)课程。如果你想了解更多关于微软 Azure 认证的信息，我们有一个[指南。](https://acloudguru.com/blog/engineering/which-azure-certification-is-right-for-me)

祝你考试成功！