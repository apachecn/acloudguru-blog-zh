# #CloudGuruChallenge:使用 Amazon ElastiCache |云专家提高应用程序性能

> 原文：<https://acloudguru.com/blog/engineering/cloudguruchallenge-improve-application-performance-using-amazon-elasticache>

*什么是#CloudGuruChallenge？点击获取更多信息。*

| **挑战** **话题** | 使用 Amazon ElastiCache 提高应用程序性能 |
| **挑战** **创造者** | [戴维·托马斯](https://www.linkedin.com/in/david-thomas-70ba433/) |
| **挑战** **目标** | 使用 Amazon ElastiCache 实现一个 Redis 集群，在一个简单的 Python 应用程序中缓存数据库查询。 |
| **挑战** **胜负** | 获得使用 Redis 实现数据库缓存所需的 AWS 和 Python 技能。 |
| **挑战** **截止日期** | 2021 年 7 月 31 日 |

## 先决条件

**AWS 自由层账户**

**Python**

**Github (Optional)**

*   [https://github.com/](https://github.com/)
*   应用程序代码将存储在 GitHub 上，但只读访问不需要帐户。

## 挑战步骤

### 数据库ˌ资料库

*   部署 RDS PostgreSQL 数据库实例。空闲层 db.t2.micro 实例应该很多。

*   您还应该创建一个数据库和数据库用户帐户。在配置应用程序时，您将需要这些。

*   如果您使用 CloudFormation 或 Terraform 模板来部署 [Amazon RDS](https://acloudguru.com/blog/engineering/getting-started-with-the-amazon-aurora-serverless-data-api) 实例，将会获得额外的奖励。

### 应用

*   部署一个 EC2 实例。同样，空闲层应该足够了，

*   安装 python3 以及 psycopg2、flask、configparser 和 Redis 模块。

*   按照 README.md 中的说明配置应用程序以连接到您的数据库实例，并对其进行测试。

*   访问页面几次，并记下页面加载时间。

*   请注意，应用程序调用的存储过程被人为地降低了速度，以表示供应不足的数据库服务器。这个挑战的目标是在数据库前面添加一个缓存，而不是优化存储过程。

### 隐藏物

*   部署 ElastiCache Redis 集群。这可以手动完成，也可以使用您选择的工具和模板自动完成。

*   确保 Redis 集群只能从应用程序 EC2 实例访问。

*   更改应用程序，在查询数据库之前检查 Redis 缓存。如果发生缓存未命中，查询数据库并用结果更新缓存。

*   对打了补丁的应用程序进行测试。确保多次访问该页面，并记下运行时间。

### 博客帖子

*   写一篇简短的博文，解释你的收获和应对挑战的方法。一定要包括你为什么接受挑战，你最大的收获是什么，以及缓存前和缓存后的页面加载时间。

*   如果你没有自己的博客， [Hashnode](https://hashnode.com/) 或 [dev.to](https://dev.to/) 都是很好的起点。

## **完成后**

你可以自己或与他人合作完成项目要求。欢迎在 [ACG 不和谐服务器](https://discord.gg/NwfDnNj54T)(有一个专门的挑战频道)或社交媒体上使用#CloudGuruChallenge 标签提问 [](https://acloud.guru/forums/cloud-guru-challenge/recent?p=1&opt_id=oeu1596472190462r0.43263125574439387) ！

当你完成项目的所有步骤后，在指定的 Discord 频道发布你的博客文章的链接。然后，我将能够在 LinkedIn 上为你在这个项目中展示的技能背书:**Amazon elastic cache，Python** 。挑战结束后，您还将有机会赢得一些超酷的奖品，并获得云计算大师 LinkedIn 帐户的特别大喊！

这项挑战将无限期开放，但要在 LinkedIn 上获得支持，赢得奖品，并在 LinkedIn 上大声喊出来，您需要在 2021 年 7 月 30 日**之前 [](https://acloud.guru/forums/cloud-guru-challenge/recent?p=1&opt_id=oeu1596472190462r0.43263125574439387) 提交您的不和谐挑战。**

最重要的是，#CloudGuruChallenge 是免费的，每个人都可以使用！

## **资源**

准备好做一些谷歌搜索，但是如果你是 ACG 会员，这里有一些资源可以帮助你更好地使用 **Python 和 AWS** :

如果你还不是 ACG 会员，我们鼓励你[注册一个免费账户](https://acloudguru.com/pricing)(不需要信用卡)开始学习并探索每月轮换的[免费课程](https://acloudguru.com/blog/news/whats-free-at-acg-june-2021)。

你不需要执行这些额外的步骤来在挑战中“宣布胜利”，但是它们*将*帮助你的项目脱颖而出，并提供令人敬畏的额外学习。

*   在 github 上创建一个公关
    *   用您所做的更改在 GitHub 上创建一个 Pull 请求。
*   RDS 实例作为代码
    *   使用 CloudFormation 或 Terraform 模板部署 RDS 实例，将实例定义为代码。

## **最终收获**

虽然用于这个挑战的应用程序被故意做得很慢，但是完成这个挑战所学到的技能对于现实世界的应用程序也是有用的。

并不总是能够将数据库调优到最佳性能—例如，当使用不允许访问数据库的第三方应用程序时。在这些情况下，能够在外部缓存数据库结果可以大大提高性能，并允许您进行扩展以满足不断增加的工作负载。

当你试图[获得一份云工作](https://acloudguru.com/blog/engineering/the-best-way-to-find-a-cloud-job)时，能够展示这些技术的实际知识将是面试时的真正资产。

* * *

## 获得更好职业所需的技能。

掌握现代技术技能，获得认证，提升您的职业生涯。无论您是新手还是经验丰富的专业人士，您都可以通过实践来学习，并在 ACG 的帮助下推进您的云计算职业生涯。