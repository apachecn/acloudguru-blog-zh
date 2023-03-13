# 跨区域 OpenSearch 和新的 Amazon EC2 实例

> 原文：<https://acloudguru.com/blog/engineering/cross-region-opensearch-and-new-amazon-ec2-instances>

本周我们又回来对 [AWS 进行了一次综合报道，我们将处理上周发生的事情，只为您带来 AWS 新闻中最精彩的内容！本周，我们将讨论新的 AWS 成本分配标签 API、Amazon OpenSearch 跨区域搜索、新的 R6id EC2 实例类型以及一些即将到来的 AWS 事件。准备好所有的细节了吗？继续读下去。](https://acloudguru.com/videos/aws-this-week)

* * *

**通往更好职业的钥匙**

[立即开始 ACG](https://acloudguru.com/pricing) 通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室来改变你的职业生涯。

* * *

## 宣布 AWS 成本分配标签 API

成本分配标签是 AWS 中管理成本的一个非常重要的部分，特别是在大型企业中，我们需要将资源成本分配到各个部门，通常规模很大。但是，管理这些成本分配标签并不容易。嗯，也许这即将改变，因为现在可以使用 AWS API 激活和停用 AWS 成本分配标签。

在您决定了要使用的标签之后，到目前为止，您必须登录 AWS 管理控制台并在计费控制台中激活每个标签。对于多个 AWS 帐户，您可能需要多次执行此操作。通过此次发布，AWS 使得通过 AWS API 管理您的成本分配标签成为可能，包括各种 SDK 和命令行。

如果您正在管理一个具有复杂成本分配的大型 AWS 环境，这将为您提供很多机会来更好地管理这些标签，并消除一些令人头疼的问题，该功能现在在所有地区都可用。

## 亚马逊 OpenSearch 跨区域搜索支持

[亚马逊 OpenSearch 现在支持跨区域搜索。](https://aws.amazon.com/about-aws/whats-new/2022/06/support-cross-region-search-amazon-opensearch-service/) OpenSearch 以前支持在同一区域内跨域搜索的能力，但这在实践中有一些限制。许多公司将跨不同区域部署他们的资源，包括 OpenSearch 集群，以满足架构需求，例如数据主权。这项新功能支持 OpenSearch 和 7.10 之后的 ElasticSearch 版本的跨集群搜索。

除了版本限制之外，还有一些限制需要注意。最值得注意的是，你不能混搭运行在 OpenSearch 和 ElasticSearch 上的域，并且由于该功能的运行方式，你不能连接到任何自我管理的集群。还有一些需要注意的限制，但是它们在 AWS 文档中有很好的介绍。

如果你在你的组织中使用 OpenSearch，特别是跨地区的，它可能会让你的生活变得更简单。

## 新 R6id EC2 实例类型

[一个新的 EC2 实例家族已经随着新的内存优化 R6id 实例正式上市](https://aws.amazon.com/about-aws/whats-new/2022/06/introducing-amazon-r6id-instances/)。

新 R6id 运行与 R6i 家族其余产品相同的英特尔至强处理器，还包括大量本地 NVMe SSD 实例存储。与之前的 R5d 系列相比，您需要支付大约 5%的按需费用，但网络接口和 EBS 存储的相对实例存储和性能都有大幅提升。

公平地说，由 AWS 自己的基于 Arm 的 Graviton2 处理器支持的 R6gd 实例家族仍然可用，并且其按需成本比基于英特尔至强处理器的 R6id 低 24%。然而，要做到这一点，您的工作负载需要能够在基于 Arm 的处理器上运行，因此，您可能更好地使用这些新的 R6id 实例及其 x86-64 架构。

因此，如果您正在突破当前配置中实例存储的极限，这可能有助于您更有效地扩展。R6id 目前在北弗吉尼亚(美国东部 1)、俄亥俄(美国东部 2)、俄勒冈(美国西部 2)和爱尔兰(欧盟西部 1)地区提供，更多地区将陆续推出。

即将举行的 AWS 活动

* * *

## AWS 将在接下来的几周举办一系列活动，本周以亚马逊火星为开端。

[re:MARS](https://remars.amazonevents.com/) 是在拉斯维加斯举行的一次会议，汇集了机器学习、自动化、机器人和空间技术领域的许多最有头脑的人(明白吗？米-阿-R-S！).会议涵盖了从将人工智能用于临床医学，管理自动驾驶汽车车队，到使用卫星和机器学习测量碳排放的所有内容，与会者绝对会喜欢。如果你感兴趣，你也可以通过免费直播在线观看主题演讲。

除此之外，AWS 峰会也将于本周在米兰和 T2 拉开帷幕，继续在全球巡回。这些都是联系当地技术社区并花一天时间深入了解 AWS 的绝佳机会。前往 [AWS 活动页面](https://aws.amazon.com/events/summits)查看完整的日期和地点列表。

*想跟上 AWS 的一切？* [*在 YouTube 上订阅一位云大师*](https://www.youtube.com/c/AcloudGuru) *的每周亚马逊新闻和 AWS 公告。你也可以像 ACG 上的*[](https://www.facebook.com/acloudguru)**一样，关注我们上的* [*推特*](https://twitter.com/acloudguru) *，或者加入* [*不和谐*](https://discord.com/invite/pluralsight) *的对话！**

* * *

**Want to keep up with all things AWS?* [*Subscribe to A Cloud Guru*](https://www.youtube.com/c/AcloudGuru) *on YouTube for weekly Amazon news and AWS announcements. You can also like ACG on* [*Facebook*](https://www.facebook.com/acloudguru)*, follow us on* [*Twitter*](https://twitter.com/acloudguru)*, or join the conversation on* [*Discord*](https://discord.com/invite/pluralsight)*!**