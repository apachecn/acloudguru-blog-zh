# AWS 首次推出 EC2 X2iezn 实例；EFS 支持复制

> 原文：<https://acloudguru.com/blog/engineering/aws-debuts-ec2-x2iezn-instances-efs-supports-replication>

本周 AWS 有什么新消息？亚马逊 EFS 现在支持复制，有一个新的 EC2 实例类型可用，GuardDuty 现在可以检测您的 EC2 实例凭据是否被泄露并被另一个 AWS 帐户使用。想要了解 AWS 最新新闻的完整内容吗？请继续阅读了解更多信息！

* * *

**加速你的职业生涯**

无论你是新手还是认证专家，云专家都能让你轻松(也很棒)地提升自己的职业生涯。查看 [ACG 的免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)或[现在就开始](https://acloudguru.com/pricing)免费试用。

* * *

## 亚马逊 EFS 现在支持复制

上周，亚马逊宣布 [EFS 现在支持复制](https://aws.amazon.com/blogs/aws/new-replication-for-amazon-elastic-file-system-efs/)。

EFS 是什么？EFS 是一个完全托管的共享文件系统，使您能够使用 NFS 协议在数千个 EC2 实例之间安全地共享文件系统。

(说到 EFS，你可以观看我们的常驻美洲驼语者和 Azure 超级粉丝 Lars Klint 在这个视频挑战中尝试与 EFS 进行实验，看看如果你知道 Azure 是否容易学习 AWS。)

EFS 现在支持复制到同一区域或不同区域，这对于灾难恢复和业务连续性规划非常有用。

*   复制流量保留在 AWS 全球网络上
*   大多数更改应在 1 分钟内复制完成
*   EFS 复制旨在满足 15 分钟的恢复点目标(RPO)

因此，副本文件系统中的数据永远不会过期超过 15 分钟。

## 专为 EDA 工作负载设计的灵活的新 X2iezn EC2 实例类型

AWS[宣布](https://aws.amazon.com/blogs/aws/new-amazon-ec2-x2iezn-instances-powered-by-the-fastest-intel-xeon-scalable-cpu-for-memory-intensive-workloads/)有一个新的 EC2 实例类型可用，它被称为 [X2iezn](https://aws.amazon.com/about-aws/whats-new/2022/01/amazon-ec2-x2iezn/) 。(好拗口！)

X2iezn 实例采用英特尔至强处理器，支持高达 4.5 GHz 的速度，AWS 声称这是云中最快的处理器。

这种新的实例类型支持多达 48 个这样的处理器，以及巨大的 1500 Gigs 内存。

X2iezn 实例非常适合高性能计算，尤其适合电子设计自动化(EDA)工作负载，即用于设计电路和微电子的自动化工具。

## 警卫加强了对泄密凭证的检测

本月早些时候，AWS [宣布](https://aws.amazon.com/blogs/aws/amazon-guardduty-enhances-detection-of-ec2-instance-credential-exfiltration/) Amazon GuardDuty 现在能够检测你的 EC2 实例凭据是否被泄露，以及是否被另一个 AWS 帐户使用。

如果你以前没有使用过 Guard Duty，这是一种机器学习驱动的威胁检测服务，可以监控你的帐户是否有恶意活动。它甚至可以检测您的 EC2 实例是否被用于比特币挖掘。

如果您的 EC2 实例附加了 IAM 角色，则在该实例上运行的工作负载能够从您的实例元数据中访问临时安全凭证，从而允许它们与 AWS 服务进行交互，假设该角色允许的权限。

如果您的 EC2 实例遭到破坏，并且恶意参与者设法从实例元数据中访问这些凭证，那么您可能希望得到警告。守卫职责总是能做到这一点。。。*如果*请求来自 AWS 之外的 IP 地址。但这一新声明意味着，即使攻击来自另一个 AWS 账户——在 AWS 网络内部——警卫职责也应该能检测到。

更多信息请点击查看[。](https://aws.amazon.com/about-aws/whats-new/2022/01/amazon-guardduty-ec2-instance-credentials-aws-account/)

## 跟上 AWS

想要跟上 AWS 的所有事情？在推特[上关注 ACG](https://twitter.com/acloudguru)和[脸书](https://www.facebook.com/acloudguru)，[在 YouTube 上订阅云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每周 AWS 更新，并在 [Discord](http://discord.gg/acloudguru) 上加入对话。

希望了解更多关于云和 AWS 的信息，或者在 2022 年开始您的云职业生涯？查看我们每月更新的[免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)的轮换阵容。(不需要信用卡！)