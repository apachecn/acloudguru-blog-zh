# azure Cosmos DB breach:chaos DB 怎么了？|云专家

> 原文：<https://acloudguru.com/blog/engineering/azure-cosmos-db-breach-what-happened-with-chaosdb>

在这篇文章中，我们来看看 ChaosDB Azure Cosmos DB 漏洞发生了什么，你现在需要知道什么，以及它对云计算的一般意义。

本周在[微软 Azur](https://acloudguru.com/blog/engineering/what-is-microsoft-azure) e 的 [Cosmos DB](https://acloudguru.com/course/azure-cosmos-db-deep-dive) 部门有很多红脸。研究公司 Wiz [宣布](https://www.wiz.io/blog/chaosdb-how-we-hacked-thousands-of-azure-customers-databases)他们已经能够访问*Azure 上的任何* Cosmos DB 账户，他们称之为 ChaosDB。

## Cosmos DB 漏洞是如何发生的？

虽然这个漏洞是如何工作的细节还没有透露，但我们知道这么多:Wiz 获得了所有客户的 Cosmos DB 主键。*全部*。

这些对网络攻击者来说是天赐之物，因为主键几乎从不改变，而且它们提供了读、写和删除操作的权限。是啊。

这是通过一个名为 [Jupyter Notebook](https://acloudguru.com/course/introduction-to-jupyter-notebooks) 的功能完成的，这是一种用户友好的方式来可视化大量数据等。对于希望直观了解数据内容的客户来说，这非常好

包含，它是如何构造的，等等。

Wiz 找到了一种方法来提升他们在自己的 Jupyter 笔记本实例中的权限，从而允许他们访问任何其他 Cosmos DB 客户的笔记本。

有了这种访问权限，就很容易获得所有的主键，然后使用这些主键登录任何 Cosmos DB 帐户。

## 谁会受到 Cosmos DB 漏洞的影响？

Azure 上的每一个 Cosmos DB 客户都受到了这次违规的影响。这包括许多财富 500 强公司。

Jupyter 笔记本于 2019 年首次推出，但从 2021 年 2 月起，它将自动为所有帐户启用。

虽然新帐户的功能将在三天后被禁用，但仍有大量帐户可能存在风险。

可以认为，即使启用 Jupyter Notebook 三天，也足以让某人获得主密钥。

## 现在该怎么办？

微软表示，他们直接向 30%的 Cosmos DB 客户发送了电子邮件，这些客户在 Wiz 发现漏洞时已经启用了 Jupyter 笔记本。

我仍然建议 Wiz 也是如此——为所有的 Cosmos DB 实例轮换主键，

不管你是否收到了电子邮件。

这个事件无疑是我在云环境中遇到的更加严重和关键的事件之一。

微软做了一件了不起的工作，在接到通知的 48 小时内消除了这个漏洞。他们很快告诉了客户，他们甚至为找到这个 bug 支付了 Wiz 4 万美元。

然而，我有兴趣回答的问题是，这对云计算意味着什么？

* * *

[**获得痛苦的云词典**](https://get.acloudguru.com/cloud-dictionary-of-pain)
说云不一定要努力。我们分析了数以百万计的回复，找出了最容易让人犯错的概念。抓住这个[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)获取一些最痛苦的云术语的简洁定义。

* * *

## **Cosmos DB 漏洞对云意味着什么？**

虽然违规很严重，但我很高兴它发生在云中。没错。

最初的影响是巨大的，因为更多的客户在同一个平台上，但也有更多的人关注它。

Wiz 发现漏洞是因为它在云端。

因为它在云中，所以它被超级快速地插入。

所有客户都知道它，因为它在云中。

在这种情况下，负责任的披露是让用户和客户尽可能快地解决问题的关键。在云环境中。

如果此漏洞是内部设置的一部分，不仅不太可能以任何有意义的方式被发现，而且即使被发现，修复也只会针对一个客户或安装。

此外，Azure 的所有工程师都在关注你，而不仅仅是你公司的一个 IT 部门。

当然，我的一部分不想看到这种违规行为，但我不会天真到认为它们永远不会发生。当它们发生时，我更希望它们发生在云计算平台上

大量的专业知识和资源可以立即扑向他们。

您是否受到 ChaosDB 漏洞的影响？你对此有什么看法？请通过推特(我是 [@LarsKlint](https://twitter.com/larsklint) 或者你可以在这里找到 ACG)或者在 [YouTube](https://youtu.be/q4YPgl0ebp0) 上的相关视频评论中告诉我们。(我很想深入了解这些事件如何影响使用这些服务的实际公司。)

此外，请每周关注 Azure This Week，了解更多重要的更新和见解。

正如我们在“可能大师”团队中所说的，当办公室中出现关于漏洞的恐慌时。。。但是，然后你意识到甚至没有一个办公室，“寻找，你应该云。”下次见，保持冷静，云大师们。

* * *

## Azure 您在云中的成功。

提升你的职业生涯。向云专家了解更多最受欢迎的技术技能。查看[本月的免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)或[获得 7 天免费试用](https://acloudguru.com/pricing)。