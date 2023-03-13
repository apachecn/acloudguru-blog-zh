# re:发明 2021: pre:发明新闻综述！

> 原文：<https://acloudguru.com/blog/engineering/reinvent-2021-preinvent-news-round-up>

本周 AWS 怎么了？只是一个名为 [AWS re:Invent 2021](https://acloudguru.com/blog/tag/reinvent2021) 的小型会议。在此之前，我们从上周开始发布了一大堆公告，我们称之为 pre:Invent！在本帖中，我们将讨论:

*   AWS 发布新的弹性灾难恢复服务
*   Amplify 会收到大量更新
*   Graviton2 支持更多服务
*   亚马逊 Linux 2022 已经发布预览版

请继续阅读所有细节！

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## **宣布 AWS 弹性灾难恢复**

AWS 已经宣布了一项新的服务，叫做 AWS 弹性灾难恢复。该服务旨在通过向 AWS 提供自动灾难恢复，最大限度地降低本地或其他云提供商服务的停机成本。

现在，如果这感觉有点熟悉，你可能是对的，AWS 已经在 cloud bearing 灾难恢复的基础上建立了该服务，该服务是他们在 2019 年收购的。事实上，它们每台受保护服务器的成本相同，而且功能似乎非常相似。

Elastic Disaster Recovery 还不支持与 cloud bearing 相同的所有操作系统或 AWS 区域，但它可以原生集成到 AWS 控制台、CloudTrail、IAM 和 CloudWatch 中。

也许这是 AWS 对 cloud bearing DR 的未来打算的一部分？但是现在，它仍然完全可用。

## 放大被放大

好吧，这实际上是一堆更新，AWS Amplify 在过去的一周左右收到了半打值得一提的更新。

我们不能在这里对它们进行公正的评价，但是总结一下这个列表:

*   [将 Amplify 后端导出为 CDK 堆栈](https://aws.amazon.com/about-aws/whats-new/2021/11/aws-amplify-export-amplify-backends-cdk-stacks-integrate-cdk-based-pipelines/)
    您现在可以将 Amplify 后端导出到 CDK 堆栈，这样您就可以将它们嵌入到您现有的 CDK 管道中，使其与您现有的 DevOps 实践更加兼容
*   [后端定制资源](https://aws.amazon.com/about-aws/whats-new/2021/11/aws-amplify-custom-aws-resources-amplify-created-backends-cdk-cloudformation/)
    几周前，值得一提的是，您现在可以将几乎任何其他 AWS 资源添加到您的 Amplify 后端，进一步简化您的部署架构
*   [GraphQL 变压器经过重新设计](https://aws.amazon.com/about-aws/whats-new/2021/11/aws-amplify-redesigned-graphql-transformer-app-backends/)
    graph QL 变压器经过彻底改造，具有更大的灵活性
*   React，Angular，Vue
    的新认证器流行的 Javascript 框架的新认证器不仅有一个新的主题，还增加了社交登录的功能，更大的可扩展性，并让您可以更好地控制自己的登录体验
*   [应用内消息(开发者预览版)](https://aws.amazon.com/about-aws/whats-new/2021/11/aws-amplify-notifications-in-app-messaging/)
    最后，还有一个开发者预览版，可以让 Pinpoint 更好地与 Amplify 集成应用内消息

不用说，有大量的变化，所以检查上面的链接，以获得所有的细节。

* * *

[![2021 re:Invent Pre-Show](img/6994ee477a5fa539a7bf90638d62f67e.png)](https://acloudguru.com/content/reinvent-2021-aws-heroes-on-what-to-know-before-the-show-webinar)

*观看 [re:Invent 2021: AWS Heroes 关于展会前应该知道的事情](https://acloudguru.com/content/reinvent-2021-aws-heroes-on-what-to-know-before-the-show-webinar)——关于我们期待什么和我们最期待的主题演讲的大赌注。*

* * *

## 到处都是引力子 2

AWS 继续加大对 Graviton2 的投资，宣布支持一系列新服务，以利用这些专为满足公共云需求的工作负载而设计的 CPU。

Fargate 让我们能够在不管理底层服务器的情况下运行容器；本质上，一个无服务器的容器平台，很像 Lambda，你只需要为你使用的时间和资源付费。与今年早些时候宣布支持 Graviton2 的 Lambda 非常相似，您的解决方案的性价比可能会提高 40%。

Graviton2 是一项非常有趣的技术，如果你想了解它如何改变你的业务，请查看 AWS 的 [Graviton 挑战赛。](https://aws.amazon.com/blogs/aws/migrate-your-workloads-with-the-graviton-challenge/)

## 亚马逊 Linux 2022 预览版

AWS 发布了亚马逊 Linux 的新版本，亚马逊 Linux 2022 发布了公众预览版。

他们宣布了一项计划，每两年发布一个新的亚马逊 Linux 主要版本，提供五年的长期支持，提供更多的确定性和稳定性。也就是说，亚马逊 Linux 2 将继续得到支持，并在 2023 年年中获得升级，同时还宣布了一个新版本，将其内核更新到 Linux 版本 5.10。

# 跟上 re:发明 2021

这是上周的一些最重要的消息，但当然，我们仍然需要谈论 re:Invent 本身:

*   我们也将出席活动，包括 Ryan Kroonenburg 和 Faye Ellis，他们将在我们的展位#1561 周围，并在本周 AWS 的一期特别节目中现场总结活动的最大公告。顺便过来，告诉他们斯蒂芬派你来的！

*   如果你参加虚拟(或只是想 TL；本周事件的博士版本)，你可以在推特[上关注 ACG](https://twitter.com/acloudguru)和[脸书](https://www.facebook.com/acloudguru)和[在 YouTube 上订阅一位云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每日更新。你也可以加入我们令人敬畏的 [Discord 社区](https://discord.com/invite/acloudguru)，在那里你可以和所有你喜欢的 AWS 培训架构师和志同道合的人一起闲逛。

目前就这些。继续牛逼吧，云大师们！