# ACID 和 AWS DynamoDB 交易:全有或全无的来龙去脉

> 原文：<https://acloudguru.com/blog/engineering/acid-aws-dynamodb-transactions>

有智慧的老 人 物种来历不明曾经 [称](https://www.starwars.com/video/do-or-do-not) ，“做。或者不要。没有尝试。”不管你是想让一个 [12，000 磅重的](https://what-if.xkcd.com/3/) X 翼从达戈巴沼泽中浮起，还是想编写要么全有要么全无的数据库云事务，这个明智的建议听起来都是正确的。有时候亲密并不能解决问题。

以网上金融交易为例。假设你欠你朋友昨天的午餐钱。你打开 Venmo，找到你的朋友，键入“10”作为你想寄给他们的 10 美元，加上一个比萨饼表情符号，然后点击支付。但是，奇怪的是，你习惯在几秒钟后收到的通知并没有出现。出事了。那现在怎么办？你的 10 美元在电子以太中丢失了吗？你的朋友还会请你吃午饭吗？

在这种情况下，除非 pizza-payback 操作的所有部分都已完成，否则您不希望写入或更新任何内容。为此，我们可以求助于 AWS DynamoDB 事务。

#### 什么是 DynamoDB 事务？

DynamoDB 是亚马逊的可扩展 NoSQL 数据库服务。如果您曾经使用过 DynamoDB，您可能已经注意到，当您需要在表内和跨表创建多个全有或全无操作时，事情变得复杂了。这也是为什么 2018 年末，亚马逊 [推出](https://aws.amazon.com/blogs/aws/new-amazon-dynamodb-transactions/) DynamoDB 交易。

DynamoDB 事务用于 支持需要全有或全无方法的任务关键型应用程序， 即使系统出现中断 。它们允许云工程师将复杂的业务逻辑实现到单个原子事务中，该事务可以由多个相关任务组成。这意味着它们对于处理订单履行和管理、处理 金融交易，或者 [构建多人游戏](https://aws.amazon.com/blogs/database/amazon-dynamodb-gaming-use-cases-and-design-patterns/) 非常有用。

#### 酸:对人类有害，对交易有益

如果说科幻小说和电子游戏教会了我们什么，那就是酸是有害的。当你从一个平台跳到另一个平台时，你不会想掉进去，如果你正在处理一个异种感染，你需要聪明地进行消灭，以免烧穿你的船或者你自己。但是在交易的世界里，酸是一个非常好的东西。

ACID 事务的概念比 DynamoDB 事务早了几十年。但是 DynamoDB 事务可能是 ACID 事务。ACID 是一个(awesome)缩写词，用于描述数据库事务的四个理想属性。

**原子:** 每笔交易都被视为一个单元，不能部分完成——这是它们全有或全无的关键因素。

**一致:** 交易有效，必须以有效状态离开数据库。这可以防止数据库被破坏或遭受数据完整性问题。

**孤立:** 不同的事务并不相互依赖。即使它们被并行或顺序处理，最终事务的效果是一样的。

**持久:** 已提交的事务将保持提交状态，因为数据被写入磁盘，而不只是保存在内存中。因此，即使系统出现故障，如断电，也不会出现故障。

#### DynamoDB 交易进行中

回到我们之前的 pizza-return 案例，您可以看到为什么 ACID 事务对于成功使用云至关重要。涉及到几乎同时发生的多个步骤。

接收转账请求→验证发起账户有足够资金→借记发起账户→贷记接收账户

这些步骤几乎同时发生，需要全有或全无的执行。这就是为什么 ACID 交易对于成功使用云至关重要——对于偿还你的披萨债务也是如此。

您可以在我们的 [AWS 认证开发者助理课程](https://acloud.guru/learn/aws-certified-developer-associate-june-2018) 中了解更多关于 [DynamoDB 事务](https://acloud.guru/course/aws-certified-developer-associate-june-2018/learn/0bbc19b0-c575-fd62-13a5-5e2297a80a6b/6054533a-e01e-0d47-e6ba-c8d2c52a05c2/watch) 。