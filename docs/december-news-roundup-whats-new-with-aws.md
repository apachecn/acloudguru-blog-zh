# 12 月新闻综述:AWS 有什么新功能？

> 原文：<https://acloudguru.com/blog/engineering/december-news-roundup-whats-new-with-aws>

你好，云大师！想知道 AWS 这个月发生了什么变化，但还没有找到时间查看几周的头条新闻？这里是你需要知道的所有信息。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

AWS 回复:发明

* * *

# 本月初的一切都是关于 AWS re:Invent！我们很幸运有许多你最喜欢的专家在现场，提供最新信息和见解，我们甚至有一个特别的 AWS 本周事件，你可以在下面查看。

活动上有如此多的公告，但你可以在我们的综述文章中[查看一些最大的公告，我们将在下面列出其中一些，你可以阅读以了解更多信息！](https://acloudguru.com/blog/engineering/aws-reinvent-2022-biggest-announcements)

Amazon Inspector 对 AWS Lambda 函数的支持

# 现在为一些后 re:发明新闻！

Amazon Inspector 服务扫描云部署中的漏洞。现在，随着扫描 EC2 实例和容器注册表图像， [Amazon Inspector 支持 Lambda 函数](https://aws.amazon.com/about-aws/whats-new/2022/11/aws-amazon-inspector-support-aws-lambda-functions/)。它的工作原理是持续监控 Lambda 函数、服务器和容器映像中的 CVE，也称为常见漏洞和暴露。

一旦你打开 Amazon Inspector for Lambda，当一个函数被重新部署时，相应区域的所有函数都会被立即扫描。如果发布了一个新的 CVE，所有的函数都会被扫描一遍，而你不需要做任何事情。

检查人员发现的任何漏洞都会在一个中央仪表板中报告，还可以使用 EventBridge 或简单通知服务将其发送到其他位置。

**AWS KMS 推出外部密钥库**

# AWS 密钥管理服务(KMS)是一个创建和管理加密密钥的优秀解决方案。一旦这些密钥就位，KMS 就允许其他 AWS 服务保护静态数据，加密和解密传输中的敏感数据，还可以创建和验证数字签名。

但是一些工作负载需要在 AWS 之外管理加密密钥。例如，某项法规可能要求加密密钥存储在本地或由无法访问您的 AWS 帐户的第三方独立审计。在这些情况下，用户可以受益于使用 KMS 作为代理，同时将密钥保持在自己的控制之下。

AWS KMS 现在支持外部密钥存储库，对用于加密和解密云中数据的密钥给予更多控制。

**AWS 验证访问**预览

# 如果您远程工作并连接到公司网络上的资源，您的 VPN 客户端可能是您求助的主要应用程序。没有 VPN，直接连接到私有资源不是很好吗？

随着 AWS Verified Access 的预览，这种未来已经成为可能，这是一种为企业应用程序提供安全、免 VPN 访问的服务。

验证访问通过使用多个输入来确定是否允许访问。这些输入可以包括用户的身份和角色以及正在使用的设备。与使用策略和网络控制来允许访问的传统 VPN 不同，验证访问检查发送到应用程序的每个请求，以确保该请求应该被允许。如果有任何变化，访问权将立即被取消。

**亚马逊 Lex 开始支持更多语言**

# Amazon Lex 允许开发人员使用语音和文本创建具有对话界面的应用程序，现在该服务支持 27 种语言。

在这次最新的更新中，Amazon Lex 增加了对阿拉伯语、广东话、挪威语、瑞典语、波兰语和芬兰语的支持。这使得聊天机器人、虚拟代理和基于语音的系统能够适应来自世界各地更多国家的用户。

如果您还没有体验过 AWS Lex 服务，现在是开始体验的最佳时机。免费层的 AWS 帐户每月收到一万条文本请求和五千条语音请求。

[**获得痛苦的云词典**](https://get.acloudguru.com/cloud-dictionary-of-pain)
说云不一定要努力。我们分析了数以百万计的回复，找出了最容易让人犯错的概念。抓住这个[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)获取一些最痛苦的云术语的简洁定义。

* * *

[![Complete guide to the Cloud and Dictionary ](img/93ebf63b88ab7fbd48705a01952ba688.png)](https://get.acloudguru.com/cloud-dictionary-of-pain)

AWS 成本异常检测通知现在包括重要的详细信息

* * *

# AWS 成本异常检测是一项财务管理服务，允许您自动检测和分析成本异常的根本原因。您可以定义阈值并设置通知，通过电子邮件、Slack、Chime 等向您发出警报。这就是重大新闻的来源。[这些通知中发送的详细信息正在增加](https://aws.amazon.com/about-aws/whats-new/2022/12/aws-cost-anomaly-detection-account-name-alert-notifications/)。现在，它将包括帐户和监视器名称以及监视器类型。

电子邮件通知也越来越多，有**开始日期**、**最后检测日期**，以及**异常持续时间**。当你追踪任何事情的真正原因时，这些信息是一个巨大的帮助。这个新功能包含在控制台和 API 中，所以这也是个好消息。

Amazon EBS direct APIs 现在支持 IPv6

# 亚马逊 EBS 是亚马逊的块存储解决方案。将 EBS 卷连接到 EC2 实例，以快速开始使用该解决方案。它有一个免费层，非常容易使用。您也可以轻松地创建这些卷的快照，但不要忘记在这些快照上设置生命周期，这样您就不会在任何不再需要的快照上累积成本。

关于快照，您可以使用 EBS direct APIs 访问 EBS 快照的内容。您可能需要访问快照来发现两个快照之间的差异。这些直接 API 现在支持 IPv6 。在你兴奋之前，直接 API 端点目前只在 4 个地区可用:俄亥俄州、北弗吉尼亚州、北加利福尼亚州和俄勒冈州。因此，请确保您的环境正在使用这四个区域中的一个，尽情享受吧！

亚马逊 2023 年 4 月的未来更新

# 亚马逊 S3 或简单存储服务是亚马逊的对象存储解决方案。每个解决方案都有保护它的方法。S3 有几种方法来保证你的对象桶的安全，比如阻塞公共访问，甚至用 ACL 或访问控制列表阻塞对单个对象的访问。

嗯，我们从亚马逊得到消息，亚马逊 S3 安全性的两个变化将于 2023 年 4 月推出。

S3 数据块公共访问将在每个新存储桶上自动启用，ACL 将在新存储桶上自动禁用。这意味着，如果您有任何需要公共访问或使用 ACLS 访问存储桶的应用程序，您将需要有目的地将这些存储桶配置为公共的或使用 ACL。

考虑使用自动化脚本或 CloudFormation 模板来配置这些设置，以便您的环境可以随着它们继续发展。请注意，这些设置将应用于每个地区的每个新存储桶，包括 GovCloud 和中国地区。

*从这些 [10 个有趣的动手项目开始构建你的云计算技能，学习 AWS](https://acloudguru.com/blog/engineering/10-fun-hands-on-projects-to-learn-aws) 。*

* * *

这是 AWS 12 月份最大的头条新闻！

* * *

想了解每周 AWS 新闻吗？

## 查看本周 AWS 的每周新闻综述。加入我们的专家主持人，因为他们涵盖了你需要知道的关于过去一周发展的一切，保持简短、有趣和信息丰富。

无论您是刚刚开始您的云之旅，还是您已经了解自己的东西，每个人都有适合自己的东西！

Whether you’re just beginning your cloud journey, or you know your stuff, there’s something for everyone!