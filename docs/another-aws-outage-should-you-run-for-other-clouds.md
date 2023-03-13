# AWS 的又一次中断:你应该运行其他云吗？

> 原文：<https://acloudguru.com/blog/engineering/another-aws-outage-should-you-run-for-other-clouds>

听过 AWS 正常运行时间的笑话吗？你可能已经听说过[亚马逊网络服务(AWS)](https://acloudguru.com/blog/engineering/what-is-amazon-web-services-aws) 在过去几周出现了一些广为人知的问题。

首先，12 月 7 日的 [AWS 中断导致 US-EAST-1 的一些重要服务中断，对许多客户造成重大影响。然后，12 月 15 日，*又一次*停电袭击了美国西部地区，尽管没有那么严重。太平洋时间 12 月 15 日上午 7 点 14 分，一些 AWS 客户开始注意到 US-WEST-1 和 US-WEST-2 的互联网连接问题。在大约 45 分钟内，AWS 工程师确定了根本原因，并开始实施补救措施，到太平洋时间上午 8 点 15 分左右，他们报告一切恢复正常。](https://acloudguru.com/blog/engineering/what-happened-with-the-aws-outage)

发生了什么事？在本帖中，我们将讨论最新的 AWS 故障，以及本周关于 [AWS 的其他新闻。我们走吧！](https://acloudguru.com/videos/aws-this-week)

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## 本月第二次 AWS 停机发生了什么？

官方状态更新称，该问题是由“AWS 主干部分和互联网服务提供商子集之间的网络冲突”引起的。

是什么导致了这种网络拥塞？

好吧，再一次，根据官方状态更新，它是“由 AWS 流量工程触发的，为了应对 AWS 网络外的拥塞而执行的。这使得 AWS 网络上的流量超出预期”，并随后影响了 AWS 主干网络和互联网目的地子集之间的连接。

因此，AWS 真的试图积极主动地为客户做正确的事情，不幸的是，在这种情况下，它适得其反。事实上，AWS 工程师总是在幕后做积极的事情，以保持服务高效运行，我们甚至没有注意到，因为事情就是这样。这次大修在本质上与[12 月 7 日 AWS 大修](https://acloudguru.com/blog/engineering/what-happened-with-the-aws-outage)有很大不同，我敢打赌，如果不是因为那次更早的事件，这次事件相对来说不会被注意到。

## 我们从本月的第二次 AWS 故障中学到了什么？

那么，我们该怎么办？奔向其他的云？让我们的数据中心起死回生？听着，每件事都会失败。不管是在云上、跨多个云还是在我们自己的数据中心。

根据 AWS 的报告，客户可能会受到长达 45 分钟的影响。在全年全天候服务的情况下，45 分钟仍超过 99.99%的正常运行时间。

当然，我仍然可以听到重复的话“但那是停机时间，我们不能承受停机时间。”

当然，然后您应该创建一个主动-主动多区域故障转移体系结构，并支付两倍于现在的费用。

那是什么？你不信任 AWS？那么，创建相同的主动-主动多区域体系结构，跨越多个云提供商，这些云提供商拥有多个供应商关系、多个支持合同和多个支持团队，负责一个现在复杂得多的解决方案。

这 45 分钟到底值多少钱？

* * *

### 了解如何像 SRE 人一样思考

观看[这个免费点播的网络研讨会](https://get.acloudguru.com/think-like-an-sre-webinar)，了解 Nobl9 工厂可靠性工程总监 Alex Hidalgo 对 SRE 文化和工具的剖析。

* * *

## 雅加达的新 APAC 地区

除了所有的中断混乱之外，有一个声明比现有的大量“实例类型 X 现在在 y 区域可用”更有趣。

AWS [最近](https://aws.amazon.com/blogs/aws/now-open-aws-asia-pacific-jakarta-region/)在位于印度尼西亚雅加达的亚太地区开设了一个新的数据中心。新数据中心命名为 ap-southeast-3，是全球亚太和 mainland China 地区的第 10 个 AWS 区域。

除了这个数据中心，AWS 还承诺在未来 15 年内发展其在印度尼西亚的业务，并创造超过 24，000 个就业岗位。这是一个很好的例子，说明 AWS 不只是在某个地方建立数据中心，而是真正投资于当地社区，改变生活，改善经济和社会未来。

### 跟上 AWS 的所有事情

想要跟上 AWS 的所有事情？在推特[上关注 ACG](https://twitter.com/acloudguru)和[脸书](https://www.facebook.com/acloudguru)，[在 YouTube 上订阅云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每周 AWS 更新，并在 [Discord](http://discord.gg/acloudguru) 上加入对话。

想了解更多关于云和 AWS 的信息吗？查看我们每月更新的[免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)的轮换阵容。(不需要信用卡！)