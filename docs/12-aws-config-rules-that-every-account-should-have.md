# 每个客户都应该拥有的 12 条 AWS 配置规则|云专家

> 原文：<https://acloudguru.com/blog/engineering/12-aws-config-rules-that-every-account-should-have>

当涉及到保护您的环境和[减少您的爆炸半径](https://acloudguru.com/blog/engineering/ransomware-and-aws-6-ways-to-reduce-your-blast-radius)时，使用 AWS 附带的开箱即用的工具是一个很好的开始。在本帖中，我们将介绍 12 个 AWS 配置规则，这些规则应该被认为是任何帐户的最低要求。

因为大多数安全部门都在做基本的事情。(不要把你的笔记本电脑“藏”在乘客座位上的连帽衫下，这样就不太可能丢失。)但是，当涉及到保护您的 AWS 环境时，基本的事情可能有点困难。

* * *

你是想开始你的 AWS 职业生涯还是想让你的技能更上一层楼？我们的 AWS 学习路径提供定制的路径，让您的云计算之旅更加精彩！

* * *

## 什么是 AWS 配置？

保护 AWS 环境的一个关键步骤是创建资产清单。

建立资产清单有多种方法。您可以使用第三方工具或 CLI 脚本，但有一种快速简单的方法，那就是使用 AWS Config。

AWS Config 允许您记录和评估 AWS 资源的配置。它有两个基本功能。

1.  它可以记录系统中运行的所有配置数据。
2.  它可以建立规则来帮助我们确保[合规](https://acloudguru.com/blog/business/compliance-is-cumbersome-but-cloud-can-help)。

* * *

#### 保护您的 AWS 环境

在这个[免费点播的网络研讨会](https://get.acloudguru.com/securing-aws-environment-webinar)中，了解如何将复杂的 AWS 环境从零提升到安全。

* * *

### 启用 AWS 配置

要开始，您需要启用 AWS 配置。你可以在这里获得整个过程的细节[。在此过程中，您将执行以下操作:](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-prereq-config.html)

*   创建一个 S3 存储桶来保存配置数据
*   创建一个配置记录器
*   创建交付渠道
*   使用 [AWS CLI](https://acloudguru.com/blog/engineering/configuring-the-aws-command-line-interface) 进行验证:
    *   aws 配置服务描述-交付-渠道
    *   aws 配置服务描述-配置-记录器
    *   aws 配置服务描述-配置-记录器-状态

一旦我们完成，系统将开始收集资产并存储它们。我们可以在 AWS 配置中看到它们，并看到从那时起的变化。

配置清单后，您现在可以:

*   查看整个客户的资源计数
*   使用 SQL 搜索库存
*   查看资产的详细信息
*   启用或创建 AWS 配置规则以确保合规性

如果在许多帐户中这样做，重要的是要注意，可以为您控制下的所有帐户集中收集配置。

## 12 个推荐的 AWS 配置规则

AWS Config 已经为许多资源管理了规则。作为最起码的要求，这里有 12 条推荐的配置规则，这些规则是由云架构师和安全工程师[唐·麦咭](https://twitter.com/DonMagee)以及[斯特迪](https://www.stedi.com/)的云安全主管提供的。

| **AWS 配置规则** | **动作** |
| 云形成-堆积-漂移-探测-检查 | 所有堆叠应无漂移 |
| S3-存储桶级别-公共访问-禁止 | S3 存储桶不应是公共的 |
| ec2-实例-非公共-ip | EC2 实例不应有公共 IP |
| EBS-快照-公共-可恢复-检查 | 您的服务器快照不应公开 |
| iam 根访问密钥检查 | root 用户不应该有访问键 |
| 启用 cloudtrail | 应该始终启用 CloudTrail |
| ec2-EBS-默认加密 | 默认情况下，所有 EBS 卷都应该加密 |
| S3-桶服务器端加密启用 | 默认情况下，S3 应该被加密 |
| VPC-默认-安全-组-关闭 | 默认安全组不应被使用 |
| ACM-证书-过期-检查 | 确保您的证书不会过期 |
| 访问键-旋转 | 确保循环使用 IAM 用户访问密钥 |
| iam-用户-未使用的-凭据-检查 | 查找要禁用的非活动帐户 |

## 成本如何与 AWS 配置一起工作？

从成本角度来看，记录器(存储在 S3)和每条规则*都需要收费。但是对于大多数组织来说，这些成本不应该太高。*

Don 说，他的组织最终放弃了配置，因为它在寻找一个比 AWS 能提供的更好的仪表板，但他们有 30 个帐户和 26 个配置规则，成本在这一点上并不令人望而却步。

* * *

## **锁定您的 AWS 安全技能**。

想了解更多关于云中安全性的信息吗？查看我们的[掌握 AWS 架构良好的框架](https://acloudguru.com/course/mastering-the-aws-well-architected-framework)课程，或者深入我们的大规模实践云学习图书馆。