# AWS Lambda 的重大改变

> 原文：<https://acloudguru.com/blog/engineering/big-changes-to-aws-lambda>

本周我们将带着另一批 [AWS 回来，在这里我们将筛选来自亚马逊网络服务世界的所有新闻和更新，这样你就不必担心了！本周，我们用基于属性的访问控制(ABAC)来定义对 Lambda 函数的访问，AWS Lambda power tools for TypeScript 现已上市，AWS AppConfig extensions 有了新版本，AWS Glue Streaming ETL with Auto Scaling 现已上市。准备好所有的细节了吗？继续读下去。](https://acloudguru.com/videos/aws-this-week)

* * *

**通往更好职业的钥匙**

[立即开始 ACG](https://acloudguru.com/pricing) 通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室来改变你的职业生涯。

* * *

## AWS Lambda 支持基于属性的访问控制(ABAC)

我们不想过于戏剧化，但是你为 AWS Lambda 定义权限的方式可能已经改变了。永远。怎么会？通过为您的 Lambda 函数利用[基于属性的访问控制(ABAC)](https://aws.amazon.com/blogs/compute/scaling-aws-lambda-permissions-with-attribute-based-access-control-abac/)。

现在，如果你是第一次接触 [ABAC](https://docs.aws.amazon.com/lambda/latest/dg/attribute-based-access-control.html) ，它提供了使用元数据(比如 AWS 资源上的标签)来定义权限的能力。这有可能为您节省大量*时间，因为您现在可以根据您以这种方式定义的特定标签，允许服务团队调用、删除或更新 Lambda 函数。*

您可以确保团队需要使用的任何新服务在创建时都包含该标签。这意味着更多的 IAM 策略将保持不变，并且您不必不断地提交票证来让安全部门的 Steve 和 Sharon 不断地向策略中添加新的 ARNs。您现在就可以试用这项功能。

说到 Lambda，这里有一个面向所有 TypeScript 开发人员的声明——[Lambda Powertools for TypeScript library 现已正式发布](https://aws.amazon.com/about-aws/whats-new/2022/07/aws-lambda-powertools-typescript-available/)。点击这里查看[。](https://awslabs.github.io/aws-lambda-powertools-typescript/latest/)

## AWS 发布 AppConfig 扩展

许多开发团队已经将功能标志作为现代应用程序开发的一个基本元素，AWS 早在 2019 年就宣布将 [AppConfig 作为 AWS 系统管理器](https://docs.aws.amazon.com/systems-manager/latest/userguide/appconfig.html)的一个功能。该服务使您能够为运行在 AWS 上的应用程序定义和使用运行时配置。本周，AWS 通过 [AppConfig 扩展](https://docs.aws.amazon.com/appconfig/latest/userguide/working-with-appconfig-extensions.html)将它推向了一个新的高度。

AppConfig 的这一功能使您能够在创建或部署应用程序配置时创建事件驱动的操作。它将服务集成到 AWS 服务中，如 SNS、EventBridge 和 SQS。它甚至让您能够利用 Lambda 创建定制的 AppConfig 扩展，来自动化您能想到的几乎任何事情。

这个版本的另一个有趣的特性是它还包括对吉拉的支持。我意识到憎恨吉拉是开发人员最喜欢的消遣，但它仍然是同类工具中最受欢迎的，所以看到 AWS 在这种支持下推出这一功能非常酷。您可以基于 AppConfig 配置部署中的操作创建或更新吉拉问题。这一功能在所有地区都可用，猜猜会发生什么？这是免费的，为什么不去看看呢？

## 具有自动缩放功能的 AWS 胶流 ETL 现在已经普遍推出

如果您正在利用 [AWS Glue](https://aws.amazon.com/glue/) 进行流数据 ETL，那么自动伸缩功能现在已经普遍可用。有了这个功能，您不再需要手动管理您为数据管道中的胶水提供的资源。嘿，我很乐意把一些手动任务从我的盘子里拿出来交给 AWS——这听起来像是双赢！随着它的普及，你现在可以将它集成到你的生产流
数据管道中。

* * *

*想跟上 AWS 的一切？* [*在 YouTube 上订阅一位云大师*](https://www.youtube.com/c/AcloudGuru) *，获取每周亚马逊新闻和 AWS 公告。你也可以像 ACG 上的*[](https://www.facebook.com/acloudguru)**一样，关注我们上的* [*推特*](https://twitter.com/acloudguru) *，或者加入* [*不和谐*](https://discord.com/invite/pluralsight) *的对话！**