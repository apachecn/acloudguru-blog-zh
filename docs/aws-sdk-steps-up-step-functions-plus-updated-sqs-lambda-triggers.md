# 阶跃函数的 SDK 访问，更新的 SQS Lambda 触发器|云专家

> 原文：<https://acloudguru.com/blog/engineering/aws-sdk-steps-up-step-functions-plus-updated-sqs-lambda-triggers>

本周 AWS 怎么了？我们已经收集了一系列 AWS 新闻，包括交叉帐户 SQSλ触发器，云控制 API 向世界发布，以及阶跃函数大幅提升。

想了解更多？详情请继续阅读！

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## 在不同的帐户中从 SQS 触发 Lambda

最近，AWS [宣布](https://aws.amazon.com/about-aws/whats-new/2021/09/aws-lambda-lambda-function-amazon-sqs-queue/)现在客户可以通过其他 AWS 账户中的 SQS 队列触发 Lambda 函数。

以前，我们只能从同一个帐户的 SQS 队列中触发 Lambda 函数，或者您必须执行一些复杂的把戏来将队列消息从帐户 A 发送到帐户 b

这种跨帐户访问是一个受欢迎的特性，因为 AWS 上最重要的组织有许多帐户，可能有数百个帐户。

由于消息队列设计模式对各种集成都非常有用，这个新特性应该会为更高效、无缝的跨帐户信息流打开大门。

当然，您仍然需要为 Lambda 函数授予跨帐户权限以到达外部队列，但是一旦完成，您只需要为远程帐户中的队列提供 ARN。

* * *

[![](img/aa563ce93b787834c7c648eaec24feaa.png)](https://get.acloudguru.com/securing-aws-environment-webinar)

**[保护您的 AWS 环境](https://get.acloudguru.com/securing-aws-environment-webinar)** 在[这个免费的点播网络研讨会](https://get.acloudguru.com/securing-aws-environment-webinar)中，了解如何从零开始保护复杂的 AWS 环境，并学习如何正确[审计和保护 AWS 帐户](https://acloudguru.com/blog/engineering/how-to-audit-and-secure-an-aws-account)。

* * *

## 云计算控制 API 现已正式发布

AWS 云控制 API 现已正式发布。云控制 API 是一组通用的 API，它允许我们以一种通用的方式以编程方式管理 AWS 服务。

我知道你在说什么，“我们已经有了所有这些的 AWS SDK。我们为什么需要这个云控制 API？”

好吧，你说这有点多余是对的，但是随着所有 AWS 服务的成长，SDK 中它们各自部分的一致性似乎从来没有优先考虑过。因此，不同的服务对于基本的 CRUD 操作有不同的语法——创建、读取、更新、删除，有时还有列表。

云控制 API 旨在通过一组通用的动词、输入参数、输出和错误类型来提供更高效的开发人员体验。

此外，云控制 API 还通过相同的统一语法支持一些第三方产品和服务，AWS 承诺新发布的服务将在发布时提供云控制 API 支持。

* * *

*对升级感兴趣，或者从开发和运营开始您的旅程？云专家的 [AWS DevOps](https://acloudguru.com/learning-paths/aws-devops) 学习路径提供适合初学者和高级专家的定制课程！*

* * *

## 步进函数解锁 AWS SDK

AWS Step Functions 开发者[现在](https://aws.amazon.com/about-aws/whats-new/2021/09/aws-step-functions-200-aws-sdk-integration/)可以访问 AWS SDK，将支持的服务数量从 17 个扩展到 200 多个 AWS 服务。

以前，如果你想对一个不支持的服务做些什么，你必须构建一个自定义的 Lambda 函数，并将其整合到你的工作流中。

现在，您可以在 Workflow Studio 中或通过云开发工具包或 Amazon States 语言访问 SDK 支持的几乎所有服务，如果您喜欢这类事情的话。如果你需要的话，你甚至可以访问像地面站、Braket 和机械土耳其人这样的利基服务。这确实创造了一些非常有趣的低代码可能性…

## 使用 ARM 上的 Lambda 节省大量成本

最后，我们[现在](https://aws.amazon.com/about-aws/whats-new/2021/09/better-price-performance-aws-lambda-functions-aws-graviton2-processor/)可以选择在 AWS 基于 ARM 的 Graviton2 处理器上运行 Lambda 函数，而不是传统的 x86 处理器。

如果您的代码使用支持基于 ARM 的处理器的运行时，您可能能够节省高达 34%的计算成本。

### 免费和 ACG 一起学习

说到节省大笔费用，您知道吗，您可以完全免费地访问每月一次的云专家课程集？看看 ACG 有什么免费的。

 [报名参加 ACG 免费计划](https://acloudguru.com/pricing)(无需信用卡)，今天就提升你的学习水平。

在 10 月份，你的免费账户可以让你访问一系列安全相关的课程，包括 [AWS 身份和访问管理(IAM)概念](https://acloudguru.com/course/aws-identity-and-access-management-iam-concepts)、[云安全基础](https://acloudguru.com/course/Cloud-Security-Fundamentals)、 [Kubernetes 安全](https://acloudguru.com/course/kubernetes-security)，以及 Azure 安全介绍(如果你对其他云中的生活感兴趣的话)。

### 跟上 AWS 的所有事情

想跟上 AWS 的一切？[在 YouTube 上订阅云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每周亚马逊新闻和 AWS 公告。你也可以在[脸书](https://www.facebook.com/acloudguru)上喜欢 ACG，在 [Twitter](https://twitter.com/acloudguru) 上关注我们，或者在 [Discord](http://discord.gg/acloudguru) 上加入对话！

朋友们，这就是本周 AWS 的全部新闻。保持安全，互相照顾，并保持令人敬畏，云大师！

* * *