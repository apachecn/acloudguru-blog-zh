# AWS 认证解决方案架构师-专业认证更新|云专家

> 原文：<https://acloudguru.com/blog/engineering/aws-certified-solutions-architect-professional-certification-updates>

亚马逊网络服务世界有什么新的东西？AWS 认证解决方案架构师会有一些变化——专业认证，Redshift 推出了新的可序列化和快照隔离级别支持，Resilience Hub 也有一些新的更新。让我们开始吧！

* * *

**通往更好职业的钥匙**

[立即开始 ACG](https://acloudguru.com/pricing) 通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室，改变你的职业生涯..

* * *

## AWS 认证解决方案架构师-专业考试更新

你准备好迎接这个大新闻了吗？AWS 解决方案架构师专业认证正在更新。cert 正在更新，以确保它与设计良好的框架保持一致。可以在考点考，也可以网上考。您将有 180 分钟的时间完成 75 道问题，包括多项选择和多项回答问题。

以下是一些需要记住的重要日期:

*   2022 年 10 月 18 日:新考试开始报名
*   2022 年 11 月 14 日:可以参加当前考试的最后一天
*   2022 年 11 月 15 日:可以参加更新考试的第一天

请记住，一旦您获得或重新认证了 Solutions Architect Pro，像 Solutions Architect Associate 这样的证书将会自动更新(假设您已经拥有它)。

先说一下[亚马逊红移](https://aws.amazon.com/redshift/)，亚马逊的数据仓库解决方案。它使用 SQL 来分析跨数据仓库、运营数据库和数据湖的结构化和半结构化数据，使用 AWS 设计的硬件和机器学习。这个解决方案现在有[两个选项来序列化事务](https://aws.amazon.com/about-aws/whats-new/2022/05/amazon-redshift-snapshot-isolation-level-support-concurrent-transactions/):可序列化和快照隔离。

Serializable 选项可用于实现严格的可序列化性，在这种情况下，如果结果不能映射到并发或重叠运行的事务的串行顺序，事务可能会失败。快照隔离将允许高并发性，对同一表中不同行的并发修改将成功完成。

这两个选项都允许事务继续在最新提交的数据库版本上操作。Serializable 是已配置集群的默认选项，无服务器数据仓库将使用快照隔离作为默认选项。这在有红移的 AWS 地区是可以的。

## AWS 弹性中心更新

AWS 弹性中心有很多新的更新。弹性是指应用程序在特定时间和时间点(RTO 和 RPO)内保持可用性和从中断中恢复的能力。

Resilience Hub 提供了一个中心位置来定义、验证和跟踪您的应用程序的弹性，以防止由软件、基础架构或运营中断导致的任何停机。它现在还支持亚马逊的[弹性容器服务](https://aws.amazon.com/ecs/)(亚马逊 ECS)[亚马逊 Route 53、](https://aws.amazon.com/route53/) [弹性灾难恢复](https://aws.amazon.com/disaster-recovery/)(AWS DRS)[AWS 备份](https://aws.amazon.com/backup)，并且现在可以使用 [Terraform](https://acloudguru.com/blog/engineering/5-things-we-love-about-terraform) 作为上传应用的来源。这意味着更多的应用程序将受到保护，不会出现中断。

[弹性枢纽弹性得分](https://docs.aws.amazon.com/resilience-hub/latest/userguide/resil-score.html)也已更新。现在将计算分数，以反映操作建议和策略合规性的组合。如果这还不够，Resilience Hub 现在还可以自动对新应用程序进行日常评估。在任何现有的应用程序上手动激活此功能，并随时停用它。这些更新在每个提供弹性中心的地区都可用。

### **跟上 AWS 的一切**

在 YouTube 上订阅一位云专家的每周 AWS 新闻(以及其他云提供商的新闻)。你也可以在[脸书](https://www.facebook.com/acloudguru)上喜欢我们，在[推特](https://twitter.com/acloudguru)上关注我们，或者在[不和谐](http://discord.gg/acloudguru)上加入对话！