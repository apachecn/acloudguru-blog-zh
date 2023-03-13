# 面向 AWS Systems Manager |云专家的出站 webhooks

> 原文：<https://acloudguru.com/blog/engineering/aws-systems-manager-gets-outbound-webhooks>

你好，大师们！斯科特·普莱彻带来了本周的另一个 AWS 下载好消息。本周，Kendra 获得了一种查询语言，在 AWS 上扩展 SAP 工作负载变得更加容易，System Manager 获得了出站 webhooks。我们开始吧！

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## 亚马逊肯德拉学习语言

通过对查询语言的新支持，Amazon Kendra 最近变得更容易使用了。[亚马逊 Kendra](https://aws.amazon.com/kendra/) 是一个支持机器学习的托管搜索服务。你可以将它指向像 S3 水桶、ServiceNow、Salesforce 和 Sharepoint 这样的资源，它会将这些资源编入索引，以便快速方便地进行搜索。

有了这个查询语言声明，您现在可以使用 AND、OR 和 NOT 以及字段级搜索和范围运算符，如大于或小于。

Kendra pro 提示:您可以使用 Kendra 来索引几乎任何 URL，这可能是让 Kendra 抓取您自己的面向公众的网站的好时机。你可能会对你的发现感到惊讶，这可能会让你的公司远离新闻，如果你明白我的意思。

在你对抓取你自己网站以外的网站有任何好主意之前，一定要知道这违反了 AWS 的可接受使用政策。

## 系统经理获得出站网络挂钩

AWS 最近为[系统管理器](https://aws.amazon.com/about-aws/whats-new/2022/01/aws-systems-manager-automation-third-party-applications-webhooks/)宣布了一个漂亮的新功能——出站 webhooks！

Webhooks 是为基于事件的活动集成各种应用程序和平台的常用方法。像 Slack、吉拉和 ServiceNow 这样的流行应用程序提供了触发事件或采取某些行动的 webhooks。

现在，从 Systems Manager 中，我们可以在其他应用程序中进行操作。例如，我们可以在 Systems Manager 中构建一个 runbook，用于自动故障转移测试。在测试开始之前，我们可以自动地在我们的内部网站点上添加一个通知，然后随着测试的进行，在一个团队 Slack 频道上发布更新。我已经可以看到所有那些自动化极客都在关注可能性。

## 在 AWS 上扩展 SAP 工作负载变得更加容易

在进入云领域之前，我在 SAP 生态系统中呆了很多年。SAP 是一家大型软件公司，拥有广泛的应用程序和服务组合，帮助许多组织高效地运营其业务。不久前，SAP 全力以赴开发了一款名为 HANA 的内存数据库。HANA 开启了许多其他创新的大门，例如打破了交易和分析系统必须分离的传统观念。借助 HANA，同一个数据库可以同时用于事务和分析，这意味着更高的实时灵活性和更少的数据重复。

HANA 作为企业数据存储的警告是，你需要足够的内存来保存你的数据——这可能是 TB 级的。现在，回到过去，对于除了最大的组织之外的所有人来说，购买一个具有足够 RAM 的系统可能成本过高，但是云使竞争环境变得公平。现收现付模式使许多公司能够试验 HANA，展示业务价值，然后在没有巨额资本投资的情况下快速投入生产。

多年来，所有主要的云提供商都在讨好 SAP，认证他们的平台来运行 SAP 生产工作负载，甚至创建特定于 SAP 的技能认证，例如新的 SAP on AWS 专业考试。

最近，AWS [宣布对其基于 HANA 的 SAP 部署的 AWS 启动向导进行增强。只需点击几下鼠标，启动向导就可以帮助您调整、配置和部署 SAP HANA 环境。新的启动向导增强功能允许您直接在启动向导中向部署添加额外的节点，而无需手动配置。相信我，任何手动维护过 SAP 环境的人都会真正体会到这种奇迹中的奇迹。](https://aws.amazon.com/about-aws/whats-new/2022/01/aws-launch-wizard-scaling-sap-deployments-increased-performance/)

### 让 2022 年成为您提升云计算职业生涯的一年

因为这是我新年的第一篇文章，祝所有人新年快乐，包括那些庆祝农历新年的人。如果你已经有了一些关于学习和认证的新年决心，并且正在寻找一些志同道合的责任伙伴，为什么不去我们的 [Discord](http://discord.gg/acloudguru) 服务器呢？你会发现许多人和你一样，想要提升他们的技能。事实上，我们将在 1 月 26 日星期三东部时间下午 7 点/太平洋时间下午 4 点在 Discord 主持另一次办公时间会议。

《我的朋友们》是 AWS 本周所有适合刊登的新闻。保持安全，互相照顾，保持敬畏，大师们。

*想跟上 AWS 的一切？在推特[上关注 ACG](https://twitter.com/acloudguru)和[脸书](https://www.facebook.com/acloudguru)，[在 YouTube 上订阅云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每周 AWS 更新，并在 [Discord](http://discord.gg/acloudguru) 上加入对话。想了解更多关于云和 AWS 的信息吗？查看我们每月更新的[免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)的轮换阵容。(不需要信用卡！)*

* * *

### 了解如何像 SRE 人一样思考

观看[这个免费点播的网络研讨会](https://get.acloudguru.com/think-like-an-sre-webinar)，了解 Nobl9 工厂可靠性工程总监 Alex Hidalgo 对 SRE 文化和工具的剖析。