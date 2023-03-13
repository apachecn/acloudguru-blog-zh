# 实时分析:你应该知道的 5 件事

> 原文：<https://acloudguru.com/blog/engineering/5-things-you-should-know-about-real-time-analytics>

对实时数据进行分析是当今许多数据工程师面临的挑战。但并不是所有的分析都能实时完成！许多取决于数据量和处理要求。甚至逻辑条件也成了瓶颈。例如，考虑一下每个表上有超过 1 亿行的大型表的连接操作。连接操作是可能的，但它可能不会实时发生；我们可以称之为…近实时。

**实时**:当你需要即时处理的信息时(比如电子商务上的信用卡交易)。

**接近实时**:您不需要立即获得数据(例如机器的日志仪表板)。你可以忍受 2-15 分钟的延迟。

## 什么是实时分析？

实时分析允许用户在数据到达系统时查看、分析和理解数据。实时或接近实时地接收到系统中的数据。操作、逻辑和数学应用于数据，为用户提供洞察，以便对新的新鲜数据做出实时决策。

为了实现实时分析，系统中的所有组件都应该实时运行。系统中摄取的数据应该以实时的方式进行处理，或者逐个事件地处理，或者使用带有微批处理流处理方法的滑动窗口。

微批处理流处理通常与 Apache Spark 结构化流相关联。Apache Spark 结构化流使我们能够以更接近实时的微批处理方式处理数据，这是实时处理与批处理的比较。[点击此处阅读更多关于 Spark streaming 的信息](https://spark.apache.org/docs/latest/streaming-programming-guide.html)。

当今实时数据分析平台的一些最大挑战是需要支持的各种数据流/管道，以及多种类型的资源。通过[批处理](https://www.investopedia.com/terms/b/batch-processing.asp#:~:text=Batch%20processing%20is%20the%20processing,time%20and%20requires%20user%20interaction.)，我们可以收集离线所需的所有数据，并提取、转换和加载到中央数据仓库中——通常使用全局模式。

## 我需要一个全局模式吗？

定义一个全局模式本身就是一个挑战。我们经常以一个全局模式结束，其中一些列定义良好，而其他列具有可疑/模糊的名称，如 colX、colY、other……很多时候,‘other’列用于依赖于来源的数据。

为了理解传统仓库的全球模式挑战，请考虑如何设计一个全球模式来表示社交媒体渠道——在一个模式中包括 Twitter 和抖音。您最终可能会得到无穷无尽的列，其中一半的行将是空的或者是不一定会用到的默认值。

还记得经典的[数据库规范化技术](https://en.wikipedia.org/wiki/Database_normalization)吗？它帮助我们删除冗余数据，更好地构建我们的模式。1NF、2NF、3NF 等变得极具挑战性，因为数据的种类、数量和速度随着各种组织系统中数据的复杂性和需求而增长。

这就是为什么在现代数据仓库中，**不需要全局模式**；它通过管理对来自各种数据库的结构化和非结构化数据的访问，为我们提供了更大的灵活性，并允许我们在需要时将不同的数据库表连接到一个仪表板。

## 如何连接多个数据源？

另一个你应该知道的术语是**EAI——企业应用集成**。当我们考虑数据时，这通常是通过共享服务总线架构实现的，该架构将消息从一个部分传输到另一个部分。

大多数时候，我们会从各种资源中收集数据。现代数据仓库使我们能够流式传输数据，并直接在其计算池中处理来自各种资源的数据。例如，现代数据仓库平台提供的 Apache Spark pools 可以极大地帮助我们处理和连接来自 Kafka 等多个流发布/订阅工具或 RabbitMQ 等消息系统的数据。

## 什么时候应该使用无服务器 SQL？

让我们想一想:谁使用收集的数据？我们有希望对他们的数据创建实时查询的业务分析师、数据科学家和希望在应用 ML 算法解决问题之前探索数据的 ML 研究人员。数据工程师持续关注数据；然后我们有销售人员、客户支持和更多的角色。并不是所有的系统都需要一个全天候运行的专用分布式计算系统。他们中的许多人更喜欢在需要时按需使用工具来满足他们的确切需求。

这就是[可伸缩的无服务器 SQL](https://docs.microsoft.com/en-us/azure/azure-sql/database/serverless-tier-overview) 可以帮助削减成本的地方。对于许多数据科学家和业务分析师来说，按需运行查询、快速了解查询大数据([大数据基础](https://acloudguru.com/course/big-data-fundamentals))并继续工作是至关重要的，如果不能实现，就会成为团队的实际瓶颈和挫折。

## 我需要**实时 MapReduce 还是事件驱动的微服务**？

最后，我想谈谈一个令许多人困惑的话题。对于实时 MapReduce，也许你熟悉 [Storm](https://docs.microsoft.com/en-us/azure/hdinsight/storm/apache-storm-overview?WT.mc_id=data-11022-adpolak) 、 [Spark Streaming](https://docs.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-integrate-azure-stream-analytics?WT.mc_id=data-11022-adpolak) 和 [Flink](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-kafka-flink-tutorial?WT.mc_id=data-11022-adpolak) 开源解决方案，它们使我们能够对实时数据进行大规模分析。事件驱动的微服务通常是独立的小型/微服务，使我们能够在每台机器上单独运行流处理，这意味着机器之间的状态通常是不共享的；因此，它不太适合分析工作负载。这两者可以在共享架构中结合起来支持一个产品。尽管如此，这通常意味着将有一条消息总线，来自不同机器的数据将被保存到一个共享的、最常见的分布式数据库中。

### **？好奇想了解更多？**

*加入我们于**12 月 7 日上午 8 点太平洋标准时间|上午 4 点格林尼治标准时间|上午 11 点东部时间**举办的 3 小时[在线免费活动](https://aka.ms/createdata)，了解数据分析、Apache Spark、如何选择合适的分布式数据库、Delta Lake、什么是无服务器 SQL、如何开始使用它以及如何使用数据做好事——主讲人包括著名的社区演讲者 Holden Karau、蒂姆·贝里隆德、亚采克·拉斯科斯基、安娜·霍夫曼等。*

![](img/cb95c50ab0a627812c14ded462d9f875.png)

*活动是免费的，但需要提前注册[这里是](https://aka.ms/createdata)。*