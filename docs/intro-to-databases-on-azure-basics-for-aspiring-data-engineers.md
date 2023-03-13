# 面向有抱负的数据工程师的数据库介绍|云专家

> 原文：<https://acloudguru.com/blog/engineering/intro-to-databases-on-azure-basics-for-aspiring-data-engineers>

如何开始使用 Azure 数据库？作为一个数据库新手或微软 Azure 的新手，有太多的选择，很难知道从哪里开始。在你开始成为一名数据工程师的道路上，哪一个适合你？

让我们把问题转过去，从不同的角度研究所有这些产品，试图理解每个选项在数据库技术的大计划中的作用。

为了做到这一点，让我们通过一个例子来讨论如何跟踪顾客在你的商店购买产品时的订单。我们将尽可能少地使用数据库术语，您会发现这些概念比您想象的更加普遍。我们将研究这个问题，并在此过程中提出一些问题，我将为您提供一些可以进一步研究的文档。我们开始吧！

对数据库有了更多的经验？使用微软 [Azure 数据库](https://acloudguru.com/course/using-microsoft-azure-database-services)服务查看一位云专家的中级课程**。这是本月的免费课程之一。**

## 数据的多种形式:关系数据与非关系数据

也许当今数据库的一大区别不是数据库本身，而是它们可以轻松处理的数据类型。即:数据库是否具备处理**关系型 vs 非关系型数据**的能力。是的，您可以让数据库适应不同形式的数据，但这最终可能会损害应用程序的性能。这意味着您需要确定您想要如何建模您的数据，然后决定哪个数据库是这项工作的最佳工具。

考虑以下假设。假设你有*个客户*想要通过下*订单*来购买*的产品*。因此，您需要将它们建模到您的数据库中，就像这样:

```
Customer: Customer ID, Customer Name, Customer Address
Product: Product ID, Product Name, Description
```

在使用这些数据下订单时，您有几种选择。例如，每个*订单*可以为订单中的每一行存储完整的*客户*和*产品*信息，或者您可以为每个产品添加一个唯一的标识符，然后从*订单*表中引用该标识符。大概是这样的:

```
Order: Order ID, Customer ID, Product ID, Quantity
```

问题是:这些选项中哪一个是首选？如果您想跟踪交易并保持数据完整性，那么将*客户*、*产品*和*订单*实体存储在不同的表中可能是您的最佳选择。

在这种情况下，我们所说的正直是什么意思？如果每次将*产品*放入*订单*时，您都要添加完整的产品信息，那么如果产品描述发生变化，您就必须为*订单*表中该产品的每个实例更新信息。这将是非常昂贵的计算和容易出错！另一方面，如果您只跟踪产品的惟一 ID，那么如果您需要更新产品描述，只需在一个地方完成即可。听起来很简单，对吗？没那么快…

如果你想显示数据会发生什么？说生意兴隆，你有成千上万的订单！现在您需要创建一个显示订单列表的报告，这样您的股东就可以看到最新的业务报告。这意味着您对数据库的查询不仅要从*订单*表中获取信息，还要从*产品*表中获取信息。因此，也许把两个实体，*订单*和*产品*，存放在同一个地方并不是一个坏主意？你怎么想呢?

## 数据工程师知道决策伴随着权衡

随着您在数据工程师职业生涯中的进步，您将了解到每一个决定都伴随着取舍。如上所述，您获得了数据完整性，但是显示信息可能最终会更加昂贵。您可以将所有数据插入到同一个表中，但是之后可能需要跨数据库手动复制更新。面对这类问题时，有没有解决方案和最佳实践可以遵循？当然啦！

到目前为止，我一直避免使用特定于数据库的术语，因为我想以一种您可以在没有太多干扰的情况下进行推理的方式来介绍这个问题。是时候揭开那些行话并给你学习资源了，这样你就可以更深入地钻研那些话题了。让我们看看。

## 数据库和数据工程术语解释

我们在上面展示了在数据库中存储业务实体的一种方法是将它们跨表拆分。我们一方面有*产品*表，另一方面有*订单*表。我们称之为*正常化*。

当*订单*表通过只存储其 ID 来跟踪*产品*时，我们称之为关系。在关系数据库术语中，存储在 *Orders* 表中的*产品 id* 是一个*外键*，它引用或关联到存储在 *Products* 表中的 *id* 。您可以在微软学习模块[描述关系数据的概念](https://docs.microsoft.com/learn/modules/describe-concepts-of-relational-data/?WT.mc_id=data-12360-alvidela)中了解更多关于这些想法的信息，特别是在标题为[探索关系数据的特征](https://docs.microsoft.com/learn/modules/describe-concepts-of-relational-data/2-explore-characteristics?WT.mc_id=data-12360-alvidela)的部分。

然后，当我们跨表拆分数据时，我们面临着一个权衡:现在我们有一个问题，当我们想要在一个报告中呈现这些数据时，我们需要从多个表中获取数据。这可能很麻烦，并且会导致性能问题，因为您需要跨包含大量数据的表运行查询。虽然我们可以使用[非关系](https://docs.microsoft.com/learn/modules/explore-core-data-concepts/3-identify-types-storage?WT.mc_id=data-12360-alvidela)数据模型来解决这个问题，就像在[文档数据库](https://docs.microsoft.com/learn/modules/explore-non-relational-data-offerings-azure/5-explore-azure-cosmos-database?WT.mc_id=data-12360-alvidela)中一样，但是没有必要脱离关系数据模型。

当使用关系数据库时，您可以使用*视图*。使用视图，您可以混合两个或多个表的数据，并将其呈现为同一个虚拟表的一部分。在微软学习版块[探索关系数据结构](https://docs.microsoft.com/learn/modules/describe-concepts-of-relational-data/3-explore-structures?WT.mc_id=data-12360-alvidela)中，您可以了解更多关于视图的内容——了解如何创建视图以及如何从视图中检索数据。

我们已经谈了很多关于插入数据、检索数据等等，但是我们忘记了一个至关重要的方面:如何查询数据。

## SQL 入门

在关系数据库中，您通常使用 SQL 语言；无论你使用 MySQL、PostgreSQL 还是 SQL Server，你都需要学习 SQL。(云专家的 [SQL 深度课程](https://acloudguru.com/course/sql-deep-dive)是一个很好的起点。)

在你成为数据工程师的职业生涯中，提高你的 SQL 能力是必不可少的，因为大多数数据库都将使用 SQL——或它的一种形式。

为了让你开始使用 SQL，Microsoft Learn 在 Azure 中提供了模块[查询关系数据。这将指导您学习从关系数据库中查询、插入、更新和删除数据。](https://docs.microsoft.com/learn/modules/query-relational-data/?WT.mc_id=data-12360-alvidela)

最后一个提示:请记住，在您的数据工程师职业生涯的这个阶段，您需要理解什么是基本概念以及您需要学习的关键词，如关系、规范化、视图等。把它们记在你的笔记本上，作为搜索术语，以后再用。通过这种方式，你可以在走自己的数据工程师之路时继续探索。

### 结论

在本文中，您看到了一个问题(比如跟踪产品、订单和客户)是如何以多种方式存储的。我们选择走关系数据的道路，在这里我们最终使用外键、视图、进行数据规范化等等。我们的目标是展示日常问题如何映射到这些概念，所以你知道行话。这将是至关重要的，因为如果你不知道要搜索什么，你就无法开始学习。与此同时，我们为您提供了几个链接，让您可以根据自己的进度深入了解和学习。

想了解更多？有一个名为[Azure Data Fundamentals:Explore core Data concepts](https://docs.microsoft.com/learn/paths/azure-data-fundamentals-explore-core-data-concepts/?WT.mc_id=data-12360-alvidela)的 Microsoft Learn 学习路径可以帮助你开始使用 Azure 上的数据库。你还可以通过云专家的 Azure 培训阵容[深入了解 Azure 所能提供的一切。](https://acloudguru.com/azure-cloud-training)

#### 关于作者

阿尔瓦罗·维德拉是微软的一名开发者拥护者，他组织了 DuraznoConf。他是 RabbitMQ in Action 的合著者，并为计算机器协会撰写文章。你可以在推特上找到他的名字是 [@old_sound](https://twitter.com/old_sound?opt_id=oeu1596472260634r0.19676524222612213) 。

* * *

无论你的经验水平如何——无论你在简历中的技术经验一栏中列出“微软办公”,还是你是一名寻求学习新东西的资深 IT 专业人士，一位云专家都将帮助你掌握 Azure 技能。