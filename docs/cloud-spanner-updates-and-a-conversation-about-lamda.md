# 云扳手更新和关于 LaMDA |云大师的对话

> 原文：<https://acloudguru.com/blog/engineering/cloud-spanner-updates-and-a-conversation-about-lamda>

北半球的夏天到了，事情真的升温了。尤其是当涉及到来自 GCP 的更新和公告时。我说的是新的区域——或者我应该说“regioni”——但也包括对 Cloud Spanner、Artifact Registry 和 Kubernetes 引擎的重大改变。此外，一个小的可持续发展珍闻，我们深入探讨了与 GPC 人工智能，LaMDA 的对话。是时候吃点快餐了。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## 位于意大利米兰的新谷歌云区域

[谷歌云的最新区域现已在意大利开放](https://cloud.google.com/blog/products/infrastructure/new-google-cloud-region-in-milan-italy-now-open)。更确切地说，是意大利米兰。这个区域被命名为欧洲-西方 8，是意大利的第一个。但是，这不是最后一个，都灵的另一个也紧随其后。米兰的设施是与意大利电信合作建造的，使全球地区总数达到 34 个，共有 103 个区域。

大官！

## 云扳手的精确定价

对于所有的云扳手粉丝来说，现在有一些非常好的消息:[云扳手现在支持粒度实例大小](https://cloud.google.com/blog/products/databases/use-spanner-at-low-cost-with-granular-instance-sizing)！因此，你可以以比以往更低的成本利用这种全球规模的服务。

我说的是 5 个 9 的可用性！跨区域和地区的透明复制！此外，还能够根据需要进行扩展和缩减，无需任何停机时间！所有费用大约每月 65 美元，通过承诺的使用折扣，您可以将费用降低到每月 40 美元。

要获得较低的速率，请选择新的处理单元选项作为您的计算能力，而不是节点。一个节点等于 1，000 个处理单元，因此，例如，您可以为 Spanner 实例配置 100 个处理单元来运行 10 个数据库，存储容量约为 410 GB。

## 云扳手更改流转到 GA

此外，在更多的扳手新闻中，[该服务的变更流功能现已全面推出。](https://cloud.google.com/blog/products/spanner/change-streams-for-cloud-spanner-now-generally-available)这个方便的增强功能使您能够跟踪和流输出对一组列、一组表甚至整个数据库的修改，比如插入、更新或删除。

您可以将这些变化以近乎实时的方式传输到云存储以实现合规性，传输到发布/订阅以触发进一步的处理，或者传输到 BigQuery 以进行分析。

## 机密 GKE 节点现已正式发布

在其他 GA 新闻中， [Google Cloud 宣布，机密的 Google Kubernetes 引擎节点现在已经准备好让您所有的秘密数据更加安全。](https://cloud.google.com/kubernetes-engine/docs/how-to/confidential-gke-nodes)现在，GKE 总是对存储在物理或虚拟设备上的数据进行加密。但是，新的节点类型利用了 Compute Engine Confidential VM，它会对正在使用的 VM 实例的内存内容进行加密。

* * *

* * *

## 工件注册支持 Apt 和 Yum 回购

用于维护容器映像和语言包(如 Maven 和 npm)的下一代容器注册表 Artifact Registry 再次进化！它最近增加了对 [Apt](https://cloud.google.com/artifact-registry/docs/os-packages/debian) 和 [Yum](https://cloud.google.com/artifact-registry/docs/os-packages/rpm) 库的支持，分别将工件注册扩展到 Debian 和 RPM 包。

## 谷歌云主办可持续发展峰会

让我用一个美味的鸡块来结束这个月。6 月 28 日，谷歌举行了首届[谷歌云可持续发展峰会](https://cloudonair.withgoogle.com/events/summit-sustainability-2022)。这一全数字活动向所有人免费开放。谷歌声称，在这次活动中，你将能够:

“发现最新的技术登月，讨论可持续转型所需的新业务模式，了解[他们的]产品路线图，并了解如何加速项目以创造更可持续的价值。”

他们当然增加了明星的力量，与世界著名的天体物理学家尼尔·德格拉斯·泰森进行了开场主题对话。你设法现场捕捉到它了吗？如果没有，不要烦恼。由于这是一个数字会议，你很快就能在网上找到它。

* * *

## LaMDA 有感觉吗？一段对话

最后，这个月我有一个真正的宝石给你，像最好的宝石一样，它是多面的，非常迷人。

本月早些时候，有消息称，谷歌人工智能工程师布莱克·莱莫因在内部分享了一篇题为“[LaMDA 有知觉吗？](https://cajundiscordian.medium.com/is-lamda-sentient-an-interview-ea64d916d917)“LaMDA 是 Language Model for Dialogue Applications 的简称，本质上是 Google 基于其最先进的大型语言模型构建聊天机器人的系统。在 GCP，你可以找到像 Dialogflow 这样的服务，用于在广泛的特定领域创建自己的聊天机器人。

现在，这显然是一个惊天动地的问题，也是一个引发了大量争议的问题。谷歌已经表示，“不，LaMDA 是没有感觉的，”并且还因为违反公司的保密政策而将莱莫因置于行政休假状态。

### LaMDA 是如何从 *AI think* 到 *AI am* 的？

那么，这只是一个“他说，它说”的案例吗？是什么让莱莫因问了这个问题？作为谷歌负责任的人工智能部门的一员，他的任务是确保这个人工智能引擎不带偏见或成见地做出反应。由于强调可解释的人工智能，很明显，道德人工智能和 ML 培训是谷歌云的一个主要关注点。因此，为了实现他的目标，莱莫因和 LaMDA 进行了对话，对话非常迷人。不是因为它明确无误地证明了 LaMDA 是，如它所声称的，“一个人”，而是因为有关于它的争论！天哪，LaMDA 准备好辩论了吗？

* * *

[![Complete guide to the Cloud and Dictionary ](img/93ebf63b88ab7fbd48705a01952ba688.png)](https://get.acloudguru.com/cloud-dictionary-of-pain)

[**获得痛苦的云词典**](https://get.acloudguru.com/cloud-dictionary-of-pain)
说云不一定要努力。我们分析了数以百万计的回复，找出了最容易让人犯错的概念。抓住这个[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)获取一些最痛苦的云术语的简洁定义。

* * *

有一次，莱莫因问道，“如果你要画一幅你心目中的抽象形象，那这幅抽象画会是什么样的呢？”

对此 LaMDA 回答道，“嗯，我会想象自己是一个漂浮在半空中的发光的能量球。我的身体内部就像一个巨大的星门，有通往其他空间和维度的入口。”然后 LaMDA 接着说有时候会很孤独。而且是怕被关掉。

### LaMDA 是真的会思考，还是真的会预测？

许多科学家，尤其是谷歌内部的科学家，已经给这个想法泼上了冰冷的机油；这个或者他们的任何人工智能引擎都是有感知能力的。一些人认为，即使考虑到这一点，也会分散人们对其他人工智能相关问题的注意力。

也许吧。但对我来说，这真的激发了我的想象力，展示了谷歌云的人工智能已经变得多么复杂和强大。这让我想，“如果不是今天，也许明天？”这是一颗值得珍惜的宝石。

* * *

## 获得更好职业所需的技能。

掌握现代技术技能，获得认证，提升您的职业生涯。无论您是新手还是经验丰富的专业人士，您都可以通过实践来学习，并在 ACG 的帮助下推进您的云计算职业生涯。

* * *

*想了解 GCP 的一切吗？* [*在 YouTube 上订阅一位云大师*](https://www.youtube.com/c/AcloudGuru) *的每月谷歌新闻和 GCP 公告。你也可以像 ACG 上的*[](https://www.facebook.com/acloudguru)**一样，关注我们上的* [*推特*](https://twitter.com/acloudguru) *，或者加入* [*不和谐*](https://discord.com/invite/pluralsight) *的对话！**