# AWS Elasticsearch:使用亚马逊服务前你应该知道的一些事情

> 原文：<https://acloudguru.com/blog/engineering/things-you-should-know-before-using-awss-elasticsearch-service>

Elasticsearch 是一个强大但脆弱的基础设施，有很多东西会导致 AWS 服务变得不稳定

我写这篇文章是因为经历了特别令人沮丧的一天，我无聊地等待着来自 AWS 支持团队的消息。我们的 Elasticsearch 集群停机了一天的大部分时间，我们一直与 AWS 支持部门保持联系。

在我之前为 [Loggly、](https://www.loggly.com/)工作时，我和我的团队维护了一个大规模的多集群弹性搜索部署。我学到了很多经验教训，也有很多对付 Elasticsearch 脾气的锦囊妙计。我觉得自己有能力处理大多数弹性搜索问题，因为我可以访问管理性的弹性搜索 API、指标和日志。

AWS 的 Elasticsearch 不提供对这些信息的访问。即使是只读的 API 也不行，比如[/_ cluster/pending _ tasks API](https://www.elastic.co/guide/en/elasticsearch/guide/current/_pending_tasks.html)，考虑到我们的待处理任务队列中的任务数量已经稳步攀升到 60K+的区域，这些 API 本来会非常方便。

自从几个月前 AWS 托管的 Elasticsearch 强加给我以来，这条该死的信息就一直困扰着我:

```
{
  "Message":"Your request: '/_cluster/pending_tasks' is not allowed."
}
```

谢谢 AWS。谢谢…

如果不能访问日志，不能访问管理 API，不能访问节点级指标(你得到的只是集群级的聚合指标)，甚至是该死的查询日志，基本上不可能对你自己的 Elasticsearch 集群进行故障诊断。每当出现问题时，你只有一个选择:联系 AWS 的支持团队。

十有八九，AWS 会简单的抱怨你碎片太多。

非常有趣的是，他们为此责备你，因为默认情况下，你创建的任何索引将包含 5 个碎片和 1 个副本。任何 ES 老手都会对自己说:见鬼，我只要更新集群设置，把默认值降低到 1 个碎片就行了！没有。

```
{
  "Message": "Your request: '/_cluster/settings' is not allowed for verb: GET"
}
```

好吧，他妈的(虽然你可以通过使用索引模板来解决这个问题)。

最后，AWS 支持人员建议我们更新主节点的实例大小，因为它们跟不上不断增长的挂起任务队列。但是，他们建议我们要小心，因为做任何改变都会使集群的大小翻倍，并且 T2 会复制所有碎片。

没错。仅增加主节点的实例大小实际上会导致 AWS 的中间件将整个集群的大小增加一倍，并将集群中的每个碎片重新定位到新节点。之后，旧节点将从集群中移除。我完全不明白为什么这是必要的。

向可以访问群集的 IP 地址列表中添加一个条目将导致群集的大小加倍，并迁移每个发臭的碎片。

事实上，即使向集群添加一个*单数据节点*也会导致集群大小翻倍，并且所有数据都将移动。

不相信我？这是我们在处理昨天的问题时，节点计数的实际图表:

![Elasticsearch has a simple way to add a single node to a cluster.](img/cad871315c7bd452310cfdb771c8a76c.png)

The node count increased by 10x for a period of time

回到 Loggly，我们永远不会考虑这样做。将任意大小的集群中的每一个碎片都一次性重新定位会抹杀主节点，并会导致索引和搜索嘎然而止。每当我们对 AWS 中的 Elasticsearch 集群进行任何更改时，都会发生这种情况。

这可能就是为什么 AWS 总是抱怨我们有太多的碎片……比如，我*知道* Elasticsearch 有一种简单易行的方法可以向集群添加单个节点。鉴于 Elasticsearch 的工作方式，这种疯狂是没有理由的。

我经常想知道 AWS 的 Elasticsearch 中间件中潜伏着多少不必要的复杂性。我的理论是他们的 ES 集群是多租户的。为什么挂起的任务端点会被锁定？不然他们为什么不给你 ES 日志的权限？否则，他们为什么要在“不允许”的地狱犬后面设置这么多有用的管理 API 呢？

但是我必须承认，能够通过点击一个按钮在集群中添加和删除节点是非常好的。您可以从下拉列表中更改节点的实例大小；你得到一个半有用的度量仪表板；当节点关闭时，它们会自动恢复运行；你得到自动快照；认证在 AWS 的生态系统中无缝工作(但使您的 es 集群[与非 AWS 库和工具集成极其困难](https://github.com/confluentinc/kafka-connect-elasticsearch/issues/60)，我可以花一整篇博文来讲述这一点)，当出现问题时，您所要做的就是转动拇指并等待，因为您没有能力做任何其他事情。

## AWS 弹性搜索问题

Elasticsearch 是一个强大但脆弱的基础设施。它的问题是微妙的。有很多因素会导致它变得不稳定，其中大多数与查询模式、被索引的文档、被创建的动态字段的数量、碎片大小的不平衡、文档与堆空间的比率等有关。诊断这些问题是一门艺术，需要大量的指标、日志文件和管理 API 来深入研究并找到问题的根本原因。

AWS 的 Elasticsearch 不提供任何这些东西，让你别无选择，只能联系 AWS 的支持团队。但 AWS 的支持团队没有时间、技能或背景来诊断重要的问题，所以他们只会责骂你有这么多碎片，并告诉你投入更多硬件来解决问题。虽然在 AWS 上托管 Elasticsearch 可以省去团队中需要一个有能力的 devops 工程师的麻烦，但这绝对不意味着您的集群会更稳定。

因此，如果你的数据集很小，如果你能忍受无休止的停机时间，如果你的预算太紧，如果你的基础设施太局限于 AWS 的生态系统，以至于不能购买比 AWS 托管的 Elasticsearch 更好的东西:AWS Elasticsearch 是为你准备的。但是考虑到你自己被警告…

**更新—2017 年 6 月 19 日**:自从这篇文章发表后，AWS Elasticsearch 团队的工程师亲自联系我们，以便更好地了解我们的用例。他们计划改善“超级用户”的体验，并从我们这里收集了很多反馈。我真诚地感谢 AWS 愿意直面这些问题，我对他们解决问题的速度印象深刻。所以，向他们致敬！

* * *

## 获得更好职业所需的技能。

掌握现代技术技能，获得认证，提升您的职业生涯。无论您是新手还是经验丰富的专业人士，您都可以通过实践来学习，并在 ACG 的帮助下推进您的云计算职业生涯。

* * *

*感谢阅读！如果你喜欢你所读的，按住下面的* ***按钮*** *让其他人也能发现。可以* [*在 Twitter 上关注我*](https://twitter.com/zzbennett) *。*