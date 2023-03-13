# Redshift 的数据交换，新的 AWS 解决方案

> 原文：<https://acloudguru.com/blog/engineering/aws-news-data-exchange-for-redshift-new-aws-solutions-ec2-launch-config-reminder>

本周 AWS 有什么新消息？对于 Redshift，第三方数据访问变得更加容易，我们有一些漂亮的新 AWS 解决方案可以使用，现在终于到了迁移那些 EC2 发布配置的时候了。

我是 Scott Pletcher，幸运的是，AWS 认证流程认为我适合继续担任三年的 AWS 认证解决方案架构师专家！虽然我已经重新认证过几次，但这是我第一次体验远程监考。你可以阅读关于我的 AWS 再认证经历的全部内容，这是一个关于阴谋和恐慌的悲惨故事。

关于我已经说得够多了。请继续阅读新闻！

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## 亚马逊红移的 AWS 数据交换

近日，AWS 公布了亚马逊红移的 [AWS 数据交换公开预览。](https://aws.amazon.com/about-aws/whats-new/2021/10/aws-data-exchange-amazon-redshift/)

AWS 数据交换是一项服务，允许那些拥有有用数据的人通过 AWS 市场共享这些数据，有时是免费的或订阅的。在此版本之前，几乎所有的数据集都可以通过 S3 获得。您可以使用 Athena 或红移光谱来获取这些数据，但从性能角度来看，这并不理想。

或者，您可以使用一些 batch [ETL](https://acloudguru.com/blog/engineering/etl-vs-elt-flowchart-when-to-use-each) 过程将数据导入到您现有的红移仓库中。

RedShift 数据交换的预览版旨在解决性能挑战，并通过允许客户直接查询和发布其他基于 Redshift 的数据集来消除 ETL 步骤。

因为您实际上是在访问数据提供者的红移实例，所以数据总是最新的，并且比基于 S3 的数据集的性能高得多。在其他数据集新闻中，AWS 已经向他们的[开放数据注册中心添加了一些](https://registry.opendata.aws/)[新的公共数据集](https://aws.amazon.com/about-aws/whats-new/2021/10/new-datasets-available-on-the-registry-of-open-data/)。

新的 AWS 解决方案

## 对于那些有抱负的云架构师来说，AWS 解决方案可能是你从未听说过的最棒的资源。

把 AWS Solutions(AWS 解决方案)想象成一个巨大的食谱数据库，但是它们不是帮助你做一顿美味的饭，而是帮助你创建一个同样美味的基于云的应用。它们通常由 CloudFormation 模板和部署指南组成，将多个 AWS 服务缝合成一个完整的解决方案。通常，只需点击一下鼠标就可以部署该解决方案。

这些解决方案由专业的 AWS 架构师审查，因此它们倾向于遵循最佳实践，并且可能是非常有用的学习工具。

最近，AWS 宣布了一些新的和改进的 AWS 解决方案，可能值得一看。有一个[分布式负载测试解决方案](https://aws.amazon.com/solutions/implementations/distributed-load-testing-on-aws/?did=sl_card&trk=sl_card)可以帮助您找到应用程序中的弱点和漏洞。我们现在也有了一个 [Q & A 聊天机器人](https://aws.amazon.com/solutions/implementations/aws-qnabot/?did=sl_card&trk=sl_card)解决方案，以及一个更新版本的[AWS Perspectives](https://aws.amazon.com/solutions/implementations/aws-perspective/?did=sl_card&trk=sl_card)——一个帮助清点和可视化记录您现有的 AWS 环境的解决方案。

如果您还没有探索过 AWS 解决方案，一定要看看！

*对升级感兴趣，或者从开发和运营开始您的旅程？云专家的 [AWS DevOps](https://acloudguru.com/learning-paths/aws-devops) 学习路径提供适合初学者和高级专家的定制课程！*

* * *

是时候迁移那些 EC2 发布配置了

* * *

## 只是一个友好的 EC2 服务提醒，如果您仍在使用 EC2 自动扩展组的启动配置，现在是时候将这些配置迁移到启动模板了。

AWS 最近宣布，他们将不再在发布配置中构建新功能，而是专注于发布模板。现在您确实有一些时间，因为 AWS 预计所有客户将在 2022 年底前完成迁移，但是拜托，发布配置是在*所以* 2010 年。

我的重新认证经历可能会紧张，但你不必如此。请于 10 月 26 日星期三美国东部时间 5:30 在我们的 [Discord 服务器](https://discord.com/invite/acloudguru)上访问我们的认证办公室。Mattias Anderson、Lars Klint 和我会在附近准备回答问题，分享考试策略，或谈论任何你想到的事情。任何时候我们三个人聚在一起，你可以确信愚蠢会接踵而至。

跟上 AWS 的所有事情

### 别忘了我们在 ACG 这里有一个[免费计划](https://acloudguru.com/pricing)(不需要信用卡)。如果你是喜欢先试后买的人，这是完美的选择。我们每个月都会推出一系列新的[免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)。

我的朋友们，这就是本周 AWS 所有适合印刷的新闻。保持安全，互相照顾，并保持令人敬畏，云大师！

*[在 YouTube 上订阅云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每周亚马逊新闻和 AWS 公告，就像 ACG 订阅[脸书](https://www.facebook.com/acloudguru)，在[推特](https://twitter.com/acloudguru)上关注我们。*

**[保护您的 AWS 环境](https://get.acloudguru.com/securing-aws-environment-webinar)** 在[这个免费的点播网络研讨会](https://get.acloudguru.com/securing-aws-environment-webinar)中，了解如何从零开始保护复杂的 AWS 环境，并学习如何正确[审计和保护 AWS 帐户](https://acloudguru.com/blog/engineering/how-to-audit-and-secure-an-aws-account)。

* * *

[![](img/aa563ce93b787834c7c648eaec24feaa.png)](https://get.acloudguru.com/securing-aws-environment-webinar)

**[Securing Your AWS Environment](https://get.acloudguru.com/securing-aws-environment-webinar)** In [this free, on-demand webinar](https://get.acloudguru.com/securing-aws-environment-webinar), see how to take complex AWS environments from zero to secure and learn how to properly [audit and secure an AWS account](https://acloudguru.com/blog/engineering/how-to-audit-and-secure-an-aws-account).