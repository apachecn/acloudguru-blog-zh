# 本月 GCP:新的云存储功能，新增的云功能支持，新的多伦多地区

> 原文：<https://acloudguru.com/blog/engineering/gcp-this-month-new-cloud-storage-features-added-cloud-functions-support-new-toronto-region>

这个月 GCP 发生了什么事？好了，摘下你的无沿帽，放下你的小嘴，因为我们有了一个新的地区*在加拿大多伦多的现场*。我们还将了解有关存储、备份、Eventarc、发布/订阅、云功能等方面的新闻。所以，当我们本月从 A 到 Zed 报道谷歌云时，给自己拿一双双和一盒 Timbits，然后回到你的切斯特菲尔德。

* * *

## 提升你的 GCP 技能

*[今天就和云专家](https://acloudguru.com/pricing)一起开始，边做边学。ACG 可以通过围绕 Google Cloud、AWS、Azure 等的课程和实际动手实验室，帮助你掌握新技能并转变你的职业生涯。*

* * *

## 多伦多新的谷歌云区域

当然，我们必须从创业板开始:谷歌已经[增加了](https://cloud.google.com/blog/products/infrastructure/google-cloud-toronto-region-now-open) *另一个*新地区——第 28 个登陆加拿大多伦多。

从一开始，这个地区就有三个独立的区域，它支持计算引擎、云运行、GKE、云存储、大表、大查询、扳手、数据流等。

一些政府和企业有数据驻留要求，因此当这个新的多伦多区域与谷歌在蒙特利尔的第 15 个云区域相结合时，这使组织不仅能够在加拿大存储和处理数据，还能够在加拿大境内的不同区域进行备份和灾难恢复。

在推出这一新区域的同时，谷歌还宣布了“加拿大保证工作负载”产品的预览版，以确保合规性。当然，这个新的多伦多地区也有助于减少居住在加拿大最大城市的数百万加拿大人的等待时间！诚然，蒙特利尔并不那么遥远——500 多公里——但它仍然有所不同。

当然，我们所有在加拿大西部的人都希望在温哥华有一个地区，所以…谷歌，如果你在听的话！别犯傻了，快去做吧！给她，嗯？好的。对于所有的加拿大笑话，我真的很抱歉。让我们继续这个月的快餐。

## 双区域云存储桶增强

谷歌刚刚[宣布了](https://cloud.google.com/blog/products/storage-data-transfer/google-cloud-expands-storage-portfolio-with-latest-launches)两个即将到来的对双区域云存储桶的增强——顺便说一下，这仍然是 GCP 独有的主动-主动方式，而不仅仅是复制。

无论如何，你很快就可以选择*你自己的*区域对来使用——而不仅仅是从谷歌提供的区域对中选择。

此外，尽管通过任何地区的访问已经非常一致，但谷歌称之为“Turbo Replication”的选项将保证在 15 分钟的 RPO 内跨这些地区复制数据，并由 SLA 提供支持。

## Filestore Enterprise 提供快照和 99.99%可用性 SLA

在文件存储领域，谷歌[将](https://cloud.google.com/blog/products/storage-data-transfer/google-cloud-announces-filestore-enterprise-for-business-critical-apps)一个新的 Filestore 企业产品添加到他们现有的 Filestore Basic 和 Filestore High Scale 中。所有这些都是 NFS v3 解决方案，但这个新的 Filestore Enterprise 还支持快照和额外的 9 倍可用性:99.99%，由 SLA 提供支持。

## 新的 GKE 备份保护有状态的 GKE 工作负载

现在，如果你碰巧使用 GKE — *和*处理*有状态的*工作负载——你会很高兴[听到](https://cloud.google.com/blog/products/storage-data-transfer/google-cloud-launches-backups-for-gke)关于谷歌新的“GKE 备份”产品。这使您可以计划定期备份集群状态和应用程序数据，并且如果您愿意，它支持跨区域还原。

## Eventarc 获得一流的云存储触发器

如果您正在使用 Eventarc 将服务连接在一起并管理事件，您现在可能会很高兴听到云存储 buckets 现在是 Eventarc 中的一级事件触发器。以前，您必须通过云审计日志来捕获此类事件，这增加了延迟和复杂性。

## 发布/子主题保留简化并降低了成本

下面这条[新闻](https://cloud.google.com/blog/products/data-analytics/pubsub-gains-topic-retention-feature)可能看起来没什么大不了的，但它实际上是一件相当好的事情。现在，您可以配置发布/订阅以在主题级别保留消息，而不必为每个订阅都这样做。这不仅使事情变得更简单，而且还可以显著降低拥有多个订阅的主题的成本。

## 云函数支持最小实例

如果你在云功能的冷启动上有问题，你会有兴趣听到你可以[现在](https://cloud.google.com/blog/products/serverless/cloud-functions-supports-min-instances)设置谷歌将为你的功能提供的最小实例数。就个人而言，我认为这对于优化 staging 和 prod 来提高系统的响应能力非常有帮助。当你打开它时，你为你的最小实例使用的*内存*支付*常规*价格，但是 CPU 时间比正常*少很多*。

## 云功能获得原生机密管理器集成

此外，云功能刚刚与谷歌秘密管理器进行了本机集成。不需要更多的自定义代码。

## 云构建集成到 Git 部署中

好吧…这是另一件对开发者来说很酷的事情。你现在可以运行“git deploy ”,让它看起来和感觉上像一个本地版本，即使你*实际上*从*云版本*中受益。一旦您触发了它，Google 新的本地 git 扩展将负责推送您的代码，然后找到构建进度并将其传输回您的终端或 IDE。滑头！

## Google Cloud Next 将于 10 月 12 日至 14 日推出

[Google Cloud Next 2021](https://cloud.withgoogle.com/next) 即将到来！谷歌的年度大会将于 10 月 12 日至 14 日举行，届时将充斥着关于 GCP 方方面面的新闻和见解，包括人工智能和人工智能、应用开发和现代化、数据分析和安全。

当然，我们会听到一群谷歌高管的发言，但我尤其对萨拉·罗宾逊、凯尔西·海塔尔和——T2 发明互联网的人之一——温顿·瑟夫的演讲感兴趣。[完整的活动目录现已发布。而且这一切都是完全免费的。所以现在就去报名吧！](https://cloud.withgoogle.com/next/catalog)

## 跟上所有云的步伐

说到免费，你知道云专家有一个免费账户层吗？不需要信用卡。每个月你都可以参加一套新的免费课程？查看[本月免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)，在这里报名[。](https://acloudguru.com/pricing)

想要跟上云的所有事物？在 YouTube 上订阅一位云专家的每周微软 Azure 新闻(以及其他云提供商的新闻)。你也可以在[脸书](https://www.facebook.com/acloudguru)上喜欢我们，在[推特](https://twitter.com/acloudguru)上关注我们，或者在[不和谐](http://discord.gg/acloudguru)上加入对话！

这个月就这些了。保持安全，照顾好你周围的人，继续保持敬畏，云大师们！

[![Complete guide to the Cloud and Dictionary ](img/93ebf63b88ab7fbd48705a01952ba688.png)](https://get.acloudguru.com/cloud-dictionary-of-pain)

[**获取谷歌云痛苦字典**](https://get.acloudguru.com/cloud-dictionary-of-pain?ajs_aid=8b2cc73f-c0e0-442b-ba6d-0eb362250ebb)
说云不一定要硬。我们分析了数以百万计的回复，找出了最容易让人犯错的概念。抓住这个[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)获取 GCP 中一些最痛苦术语的简洁定义。