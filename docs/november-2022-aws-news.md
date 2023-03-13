# 11 月新闻综述:AWS 有什么新功能？|云专家

> 原文：<https://acloudguru.com/blog/engineering/november-2022-aws-news>

你好，云大师！想知道 AWS 这个月发生了什么变化，但还没有找到时间查看几周的头条新闻？这里是你需要知道的所有信息。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

# 亚马逊 MSK 拥有新的低成本、几乎无限的存储层

亚马逊为 Apache Kafka (MSK)管理流媒体，速度快了五倍！–[现在提供分层存储，几乎可以无限扩展](https://aws.amazon.com/about-aws/whats-new/2022/10/amazon-msk-offers-low-cost-storage-tier-scales-virtually-unlimited-storage/)。MSK 是一个完全托管的服务，它允许您构建和运行使用 Apache Kafka 处理流数据的应用程序。它还允许您创建、更新和删除集群，以及使用 Apache Kafka 的开源版本生成和消费数据。

[随着这种新型分层存储](https://docs.aws.amazon.com/msk/latest/developerguide/msk-tiered-storage.html)的发布，您现在将能够存储和处理数据，同时比现有的 MSK 存储选项降低 50%或更多的成本。它还提供了更长的安全缓冲区，可以处理意外的处理延迟或构建新的流处理应用程序。对于新的或现有的群集，只需点击几下鼠标即可启用这一新的存储选项，客户将为存储和数据检索付费。

# AWS 资源浏览器简介

re:Invent 即将到来，我们预测今年的[主题之一是 AWS 将发布工具来帮助管理跨多个地区和客户的工作负载。](https://youtu.be/mT7UVQTkD28)

对于那些利用复杂的多区域工作负载的人来说，管理可能有点麻烦，AWS 正在努力缓解这种情况。一个新的工具， [AWS Resource Explorer](https://aws.amazon.com/blogs/aws/introducing-aws-resource-explorer-quickly-find-resources-in-your-aws-account/) ，让你有一个统一的位置来查找你在一个帐户中有什么资源，即使它们与你当前使用的资源在不同的区域。想要通过特定的标记在所有地区查找 EC2 实例吗？是的，你可以这样做！您是否有资源的 ID，但不知道它在哪个区域？它也能处理这个问题。

您可以通过各种不同类型的元数据在所有地区进行搜索。您甚至可以创建资源的自定义视图，这样您就可以在一个地方查看所有符合指定条件的资源。启用该服务后，您甚至可以直接在 AWS 控制台的搜索栏中进行搜索。值得庆幸的是，您不必等着使用这个有用的新工具，您可以今天就开始使用。

# EC2 安置组可以在 AWS 客户之间共享

坚持 AWS 帮助多帐户和多地区工作流的主题，这里有另一个例子！

放置组是 EC2 中的一项功能，使您能够在同一个可用性区域中启动实例，同时让它们利用彼此之间的低延迟和高吞吐量连接。根据你对小组的目标，有不同类型的小组。无论您选择哪个选项，这些实例都需要在同一个 AWS 帐户下…或者至少到目前为止是这样。

现在，您可以[利用 AWS 资源访问管理器将来自多个帐户](https://aws.amazon.com/about-aws/whats-new/2022/11/amazon-ec2-placement-groups-shared-across-multiple-aws-accounts/)的实例包含在单个位置组中。这是普遍可用的，因此您现在可以在任何 AWS 商业区域试用它。

# 亚马逊时间同步现已公开

[Amazon Time Sync 现在可以通过互联网](https://aws.amazon.com/about-aws/whats-new/2022/11/amazon-time-sync-internet-public-ntp-service/)作为一项公共 NTP 服务使用——零成本！时间同步是一种高度精确和可靠的时间基准，它使用一组卫星来提供基于协调世界时或 UTC 全球标准的当前时间。此服务还会自动平滑闰秒，这些闰秒会定期添加到 UTC 以适应闰年，这对于某些应用程序来说可能会有问题。

在此次发布之前，时间同步仅适用于 EC2 实例。现在，他们把它作为一种公开可用的 NTP(或网络时间协议)服务提供给任何可以访问互联网的服务器。

# 多 MFA 设备支持

IAM 现在[支持 root 和 IAM 用户使用多个多因素认证(MFA)设备](https://aws.amazon.com/about-aws/whats-new/2022/11/aws-identity-access-management-multi-factor-authentication-devices/)。这意味着您可以为每个用户配置多个身份验证设备，每个用户最多可以配置 8 个，包括硬件和虚拟 MFA 设备。

对于 root 和 IAM 用户来说，使用 MFA 是一种安全最佳实践，为您提供了一层额外的保护，防止未经授权的访问；[这一新发布的产品](https://aws.amazon.com/blogs/security/you-can-now-assign-multiple-mfa-devices-in-iam/)为客户提供了更多的灵活性。例如，假设您为 root 帐户配置了一个 MFA 设备，而该设备丢失或损坏了。通过配置多个 MFA 设备，您可以毫无延迟地继续访问您的帐户。

* * *

[![Complete guide to the Cloud and Dictionary ](img/93ebf63b88ab7fbd48705a01952ba688.png)](https://get.acloudguru.com/cloud-dictionary-of-pain)

[**获得痛苦的云词典**](https://get.acloudguru.com/cloud-dictionary-of-pain)
说云不一定要努力。我们分析了数以百万计的回复，找出了最容易让人犯错的概念。抓住这个[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)获取一些最痛苦的云术语的简洁定义。

* * *

# 检索冰川数据的速度提高了 10 倍

现在，您可以从 Glacier Flexible Retrieval and Glacier Deep Archive[中检索数据，速度比之前的](https://aws.amazon.com/about-aws/whats-new/2022/11/amazon-s3-glacier-restore-throughput-10x-large-volumes-archived-data/)快 10 倍，而且无需额外费用。这种吞吐量的增加适用于所有标准和批量检索，并且 [Glacier 现在可以在 AWS 区域内以每个帐户每秒 1000 个事务的速度支持恢复请求](https://aws.amazon.com/blogs/storage/restoring-archived-objects-at-scale-from-the-amazon-s3-glacier-storage-classes/)。

这对于需要定期恢复由许多小对象组成的数据集的应用程序来说非常好，可以显著减少完成恢复所需的时间。

# 亚马逊 EventBridge 增加了新功能

EventBridge 是无服务器事件总线服务，可用于接收和响应来自各种来源的事件，包括 lambda 函数、API 目的地，甚至其他事件总线。该服务越来越被视为 AWS 上任何事件驱动架构的基石。本月早些时候， [AWS 宣布了新的 EventBridge 调度器](https://aws.amazon.com/about-aws/whats-new/2022/11/amazon-eventbridge-launches-new-scheduler/)，这是一个托管接口，用于调度基于时间的事件，以触发 270 多个 AWS 服务中的操作。

AWS 继续增加新的 EventBridge 功能，宣布了两个新的生活质量更新。您现在可以从现有的 EventBridge 规则中生成 CloudFormation 模板，以及从模式中自动生成模式。模式用于检查传入的事件是否与预期的格式相匹配，在历史上，这些必须手工编写。我很高兴看到 EventBridge 的其他功能将在今年的 re:Invent 2022 上[亮相。](https://acloudguru.com/blog/engineering/aws-reinvent-2022)

# 分步功能增加了简单的跨账户功能

本月， [AWS 宣布扩展并简化了跨账户功能，增加了步骤功能](https://aws.amazon.com/about-aws/whats-new/2022/11/simplify-cross-account-access-aws-services-step-functions/)。Step 函数用于协调跨许多服务甚至跨许多帐户的无服务器工作流。过去，用户利用基于资源的策略来授予 step 函数对外部帐户中的资源的访问权限。但是，并非所有 Step 函数支持的服务都支持基于资源的策略。

用户现在可以利用基于身份的策略，本质上允许 step 函数在外部帐户中承担类似用户的角色。[有了这一新功能](https://aws.amazon.com/blogs/compute/introducing-cross-account-access-capabilities-for-aws-step-functions/)，使用 Step Functions 与跨账户资源的直接集成将比以往任何时候都更容易。

* * *

*从这些 [10 个有趣的动手项目开始构建你的云计算技能，学习 AWS](https://acloudguru.com/blog/engineering/10-fun-hands-on-projects-to-learn-aws) 。*

* * *

# 更新认证解决方案架构师专业考试

截至 11 月 15 日， [AWS 已经正式转向最新版本的认证解决方案架构师专业考试](https://aws.amazon.com/blogs/training-and-certification/aws-certified-solutions-architect-professional-content-outline-updated-to-align-with-latest-trends-and-innovations/)。他们取消了考试的成本控制部分，并将其分布在其他四个领域:

*   为组织复杂性设计解决方案
*   为新解决方案而设计
*   现有解决方案的持续改进
*   加速工作负载迁移和现代化。

组织的复杂性现在占据了考试的很大一部分，从总权重的 12.5%上升到 26%。David Blocher，他最近参加了(并通过了！)这个新的考试，发现这个变化主要表现在更多的关于管理 AWS 组织的多个账户以及授予用户和资源跨账户权限的问题。如果你想重温一下多账户管理，可以看看 David 的课程[如何在 AWS 中组织你的账户](https://learn.acloud.guru/course/how-to-organize-your-accounts-in-aws/overview)！

以上是 AWS 11 月份最大的头条新闻！

## 想了解每周 AWS 新闻吗？

查看本周 AWS 的每周新闻综述。加入我们的专家主持人，因为他们涵盖了你需要知道的关于过去一周发展的一切，保持简短、有趣和信息丰富。

无论您是刚刚开始您的云之旅，还是您已经了解自己的东西，每个人都有适合自己的东西！