# 谷歌云发布新的 GCP 开发者备忘单

> 原文：<https://acloudguru.com/blog/engineering/google-cloud-drops-new-gcp-developer-cheat-sheet>

对于谷歌云平台来说，这是一个重要的月份，包括新的云部署和证书管理器产品，Bigtable 的自动扩展，EU 的有保证的工作负载，新一代的云功能，以及更新的谷歌云开发人员备忘单和 GCP 架构图表工具！让我们开始吧！

想要本月所有视频形式的谷歌云新闻吗？看看我们这个月在 [GCP 的最新一集。](https://learn.acloud.guru/series/gcp-this-month/view/402)

* * *

**通往更好职业的钥匙**

[立即开始 ACG](https://acloudguru.com/pricing) 通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室来改变你的职业生涯。

* * *

## 2022 版谷歌云开发者备忘单

谷歌开发者关系团队一直在努力工作，他们对[谷歌云开发者备忘单](https://cloud.google.com/blog/topics/developers-practitioners/back-popular-demand-google-cloud-products-4-words-or-less-2022-edition)进行了大规模更新。如果你参加过我的[谷歌云培训](https://acloudguru.com/training-library/gcp-cloud-training)，那么你可能已经熟悉这个神奇的工具了。如果你没有，那么今天是你的幸运日！

因为这东西太牛逼了！

备忘单也被称为“四个字以内的谷歌云产品”，这是它的魅力之一。这些明智选择的词汇让你对某个特定的 GCP 产品的功能有一个很好的感觉——实际上，是每个产品的功能，因为它很全面！

可打印的海报版本仍然是我最喜欢的，但新的[互动版本](https://googlecloudcheatsheet.withgoogle.com/)的一个关键好处是，每个产品卡都将你直接链接到文档，所以如果你需要的不仅仅是四个词，你可以深入了解。列表视图(可在顶部选择)与海报有着同样舒适的一览式感觉。

我们不仅对这个非常有价值的工具进行了大规模的更新，看起来我们在未来也会得到更快的更新！Priyanka Vergadia 定期发布关于谷歌云的精彩内容，因为她现在已经接管了这个工具的维护工作，它的未来看起来一片光明！

但是等等，还有呢！

他们也刚刚发布了一个新的[GCP 建筑制图工具](https://cloud.google.com/blog/topics/developers-practitioners/introducing-google-cloud-architecture-diagramming-tool)！就其本身而言，这似乎并不令人兴奋。但是酷在集成中！

首先，图表的组件与备忘单相连接，以帮助挑选和理解它们。接下来，您可以从参考架构库中引导您的图！不仅如此，这些架构示例中的一些已经设置好了，因此您可以非常容易地将它们部署到您的项目中，并进行试验！

不错吧。我以为你会喜欢的。这里有一大堆其他 GCP 小吃供你欣赏。

## 用于 Spark GA 的 Dataproc 无服务器；在预览中触发 BigQuery

如果您正在使用 Apache Spark 从您的数据中榨取价值，我敢肯定这不是因为您真的喜欢管理这些 Spark 集群，对吗？好吧，你会很高兴听到谷歌刚刚发布了他们的[data proc Spark](https://cloud.google.com/blog/products/data-analytics/simplify-data-processing-and-data-science-jobs-with-spark-on-google-cloud)无服务器产品，供大众使用！现在你可以让 Google 管理集群和调整基础设施，你可以专注于编码。

作为奖励，现在还有一个通过 BigQuery 的 Spark 的私人预览，这使得更容易获得 Spark-y 的优点，就在你的数据附近。

## Bigtable 的自动缩放现在正式发布

现在，说到管理集群，Bigtable 也得到了提升。[Bigtable](https://cloud.google.com/blog/products/databases/dive-deep-into-bigtable-autoscaling-and-how-it-optimizes-costs)的自动缩放现已全面推出。当您的系统不需要所有容量时，为过度配置的 Bigtable 集群付费是没有意义的，因此这是一个受欢迎的变化，可以更好地将您的成本与您的实际使用相匹配。

尽管谷歌的博客文章中使用了不少于六次相当有趣的词“日间”，但我相信如果你的工作量恰好是“夜间的”，你也可以轻松节省他们提到的 40%。

## 新的计算优化 AMD EPYC 虚拟机

好的……这个公告是关于使用第三代 AMD EPYC 米兰处理器的新的[计算优化 C2D 实例家族](https://cloud.google.com/blog/products/compute/introducing-compute-optimized-vms-on-amd-epyc-milan)。您可以用多达 112 个 vCPUs 和 896 GB 的内存来增强这些功能。当然，即使这些是计算优化的 CPU，您仍然可以像往常一样，在计算引擎中选择最合适的处理器与内存的比率。

## 面向欧盟的有保证的工作负载现已正式上市

如果你对它不熟悉，保证工作负载是谷歌对亚马逊的 GovCloud 的回应——但谷歌不是一个满足合规性的独立云区域，而是一个工作负载系统，以满足世界上该地区任何 GCP 地区的合规性。现在，谷歌为欧盟提供的[保证工作负载](https://cloud.google.com/blog/products/identity-security/meet-data-sovereignty-requirements-with-assured-workloads-for-eu-on-google-cloud)正式上市。

虽然这包括数据驻留、数据加密和谷歌人员，但它们仍处于与云外部密钥管理器集成的主权控制的公共预览中，该管理器允许您将数据加密密钥保存在 GCP 之外。

## 云功能第二代公开预览版

如果你已经关注这个系列有一段时间了——或者，即使你没有——那么你可能知道我喜欢所有无服务器的东西！如果你也是，那么你会很高兴听到谷歌刚刚发布了他们的第二代云功能！

现在，由于这个新版本是基于云运行的，这就模糊了无服务器计算选项之间的界限。因此，我们仍然拥有与第一版云功能相同的按使用付费计算，但现在我们也可以同时处理多个请求/事件，就像 Cloud Run 一样！

当然，在您打开它之前，请确保您的代码能够处理并发请求！但是，如果您的事件处理不总是限制 CPU，这可以为您节省一大笔钱。此外，第二代产品还能让您:

*   在更长的时间和更强的实例上运行您的函数
*   引脚实例减少冷启动
*   在多个版本之间分割流量

这些新的云功能太棒了！

## 公开预览版中全新的完全托管证书管理器

现在，众所周知，所有的网站最好都使用 HTTPS。我的意思是，不仅正常的 HTTP 连接会在 Chrome 地址栏中被标记为“不安全”，而且不安全的网站也会在谷歌搜索中被深埋。因此，这是一个好消息，谷歌现在有一个新的无服务器[证书管理器产品在公开预览](https://cloud.google.com/blog/products/identity-security/simplify-saas-scale-tls-certificate-management)。

Certificate Manager 让任何人都可以非常轻松地在面向其 GCP 工作负载的外部 HTTPS 负载平衡器上获取和使用 TLS 证书。你每个月可以免费使用 100 个证书，之后就是按证书付费了。

因为这些由谷歌的基础设施管理，你的客户可以快速与谷歌的边缘节点协商安全连接。超低延迟！哦，这个产品还支持通配符证书。很狂野，是吧？好吧，我知道那个笑话很糟糕。对不起

## 云部署现已正式上市，可持续交付至 GKE

另一个新产品是[云部署](https://cloud.google.com/blog/products/devops-sre/google-cloud-deploy-now-ga)，现在也正式发布！正如谷歌在公告中指出的，“Kubernetes 持续交付的运营成本可能非常高。”嗯，Cloud Deploy 旨在通过这种受管且固执己见的持续交付服务为 GKE 消除一些痛苦。

如果你使用 GKE，那么你可能会发现除了第一个免费的外，每个月额外的 15 美元是值得的。Cloud Deploy 构建于 Skaffold 之上，既包括与 GCP 管理的轻松集成，也包括许多内置的最佳实践。

## 即将举办的活动:数据云峰会和云计算未来

最后，我想让你知道一些即将到来的事件。接下来的 4 月 6 日是[数据云峰会](https://cloudonair.withgoogle.com/events/summit-data-cloud-2022)。这将是一场关于“人工智能、机器学习、分析、数据库等”的在线活动

更好的是，我们现在已经有了下一个[Google Cloud’22](https://cloud.withgoogle.com/next)的日期！Cloud Next 是谷歌的年度会议，挤满了所有最令人兴奋的 GCP 公告，所以请确保在 10 月 11 日至 13 日举行。如果你像我一样抱着一线希望，希望这可能会成为一场面对面的活动，那么一定要预留一些额外的时间来往返旧金山。祈祷吧，我希望能在那里见到你！

## 关注谷歌云的一切

在 YouTube 上订阅一位云专家的每周新闻和更新。你也可以在[脸书](https://www.facebook.com/acloudguru)上喜欢我们，在[推特](https://twitter.com/acloudguru)上关注我们，或者在[不和谐](http://discord.gg/acloudguru)上加入对话！

保持安全，照顾好你周围的人，继续保持敬畏，云大师们！