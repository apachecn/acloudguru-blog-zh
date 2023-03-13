# 2021 年 AWS 存储日:主要亮点

> 原文：<https://acloudguru.com/blog/engineering/the-top-3-highlights-from-aws-storage-day-2021>

AWS 最近举办了第三次年度 [AWS 存储日](https://aws.amazon.com/blogs/aws/welcome-to-aws-storage-day-2021/)，这是一次免费的虚拟活动，在其 Twitch 频道上举办，有许多与 AWS 存储服务相关的公告、见解和内容。以下是一些亮点和标题。

*   适用于 NetApp ONTAP 的 Amazon FSx 现已正式上市
*   亚马逊 S3 推出了一项名为多区域接入点的新功能
*   亚马逊弹性文件系统引入智能分层

想了解更多？详情请继续阅读！

## 1.面向 NetApp ONTAP 的 Amazon FSx 现已正式上市

AWS 宣布面向 NetApp ONTAP 的 Amazon FSx 正式上市。这是一款存储服务器，允许客户首次在云中启动和运行完整、全面管理的 ONTAP 文件系统。

如果您以前从未听说过，ONTAP 是 NetApp 的文件系统技术，传统上用于本地网络连接存储。Amazon FSx for NetApp  ONTAP 提供了 ONTAP 文件系统的所有流行功能、性能和 API，以及完全托管的 AWS 服务的优势。在这里了解更多。

* * *

[![WFH Security](img/330ebea2da731262c053584b3c3c8bff.png)](https://get.acloudguru.com/securing-aws-environment-webinar)

**[保护您的 AWS 环境](https://get.acloudguru.com/securing-aws-environment-webinar)** 在[这个免费的点播网络研讨会](https://get.acloudguru.com/securing-aws-environment-webinar)中，了解如何从零开始保护复杂的 AWS 环境，并学习如何正确[审计和保护 AWS 帐户](https://acloudguru.com/blog/engineering/how-to-audit-and-secure-an-aws-account)。

* * *

## 2.亚马逊 S3 多区域接入点启动

接下来，亚马逊 S3 多区域接入点已经启动。当访问跨多个 AWS 区域复制的 [AWS 数据集](https://acloudguru.com/learning-paths/aws-data)时，这些技术可将性能提升高达 60%。

M 多区域接入点服务基于 AWS 全球加速器，它考虑了网络拥塞和请求应用程序的位置等因素，通过 AWS 网络将您的请求动态路由到最低延迟的数据副本。这自动利用了 AWS 的全球基础设施，同时允许您为您的应用程序维护一个简单的架构。

它还提供了访问数据的单一端点，因此您可以使用用于单区域解决方案的相同架构来构建多区域应用程序。(这挺酷的。)在内部运行的应用程序也可以通过 AWS PrivateLink 访问多区域接入点，同时还有全新的 S3 管理控制台体验。一定要去看看。更多信息请点击这里。

* * *

对升级感兴趣还是从开发和运营开始您的旅程？云专家的 [AWS DevOps](https://acloudguru.com/learning-paths/aws-devops) 学习路径提供适合初学者和高级专家的定制课程！

* * *

## 3.亚马逊弹性文件系统引入智能分层

最后，Amazon Elastic Filesystem 引入了[智能分层](https://aws.amazon.com/about-aws/whats-new/2021/09/amazon-elastic-file-system-intelligent-tiering/)来自动优化存储成本。

智能分层是一项新功能，即使您的访问模式发生变化，也可以轻松地在共享文件存储中节省资金。它使用生命周期管理来监控您的工作负载的访问模式，并且旨在自动将生命周期策略期间未被访问的文件转移到更便宜的存储类别。

这利用了比 EFS 标准定价低 92%的更便宜的层。如果您的模式发生变化，智能分层也可以将文件移回性能优化的存储类别，因此这不仅仅是单向的。这是目前在亚马逊 EFS 可用的所有 AWS 地区。

*想跟上万物云？[在 YouTube 上订阅云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每周亚马逊新闻和 AWS 服务公告。你也可以在[脸书](https://www.facebook.com/acloudguru)上喜欢 ACG，在 [Twitter](https://twitter.com/acloudguru) 上关注我们，或者在 [Discord](http://discord.gg/acloudguru) 上加入对话！*

* * *

## 加速您在云计算领域的职业发展

学得更快。动作快点。[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。