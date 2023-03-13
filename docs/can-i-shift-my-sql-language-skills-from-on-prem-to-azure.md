# 我可以将我的 SQL 语言技能从本地迁移到 Azure 吗？|云专家

> 原文：<https://acloudguru.com/blog/engineering/can-i-shift-my-sql-language-skills-from-on-prem-to-azure>

*答案是肯定的！我们涵盖了你需要知道的一切。同样，这个关键问题的答案是:每个 Azure 解决方案都是什么品种的狗？*

* * *

**通往更好职业的钥匙**

[立即开始 ACG](https://acloudguru.com/pricing) 通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室来改变你的职业生涯。

* * *

如果您是一名 SQL Server 专业人员，无论有多长时间，您都知道您的大部分工作都是处理坏消息——要么对它做出响应，要么试图阻止它。

所以，就这一次，让我们从一些好消息开始！到目前为止，你设法避免的那些不熟悉的、令人生畏的云数据技术？它们没有你想象的那么难用。事实上，你可以通过 SQL 的某种方言来查询大量 Azure 数据资源中的数据。这意味着如果你想做出改变，你不是从零开始。

现在，*有一些坏消息:如果你已经在性能调优、调整索引、规范化数据和穿越 SQL Server 的秘密隧道和通道方面建立了声誉，你可能需要稍微调整一下你的职业身份。*

不是很多，只是一点点。

为什么？Azure 中的平台即服务(PaaS)产品抽象出了关系数据库的许多复杂性。自动调谐和类似的功能是真实的，这些天；你会发现 Azure SQL 不太可能搬起石头砸自己的脚。对于非关系数据库，许多调整和优化根本不适用。

(‘非亲属’一词通常与 NoSQL 同义，但前者更好些。它更准确地描述了不同于 SQL Server 表的高度结构化的关系行和列的数据格式。)

尽管我声称有好消息，也有坏消息，但您可能对云数据资源产生了错误的印象。可能的原因？可怕的招聘广告读起来像一个词汇测试，而不是一个技术清单。

上次我查看与数据相关的招聘信息时，有这样的要求:

* * *

*“候选人必须在以下技术中的至少 13 个领域拥有实际的专业经验:SSIS、SSRS、SSMS、SSAS、SSMinnow、TSQL、PL/SQL、ANSI SQL、noSQL、MySQL、yourSQL、ourSQL、weAllGotSQL、Mongo DB、HANA、Spark、Hadoop、Azure、Cloudera、MapR、Hortonworks、HortonHearsAWho、Informatica、Tableau、Crystal Reports、SAS、Python、R (S、T、U 和 V 也有帮助*

* * *

好吧，也许我有点夸张。我的主要观点是，要迁移到 Azure，你真的不需要了解所有的，甚至是大部分的语言和技术。

(我指的是真的那些。HortonHearsAWho 不是真正的技术；你知道的，对吧？)

只需一点点培训，您就可以轻松获得云中数据管理、存储和计算的好处。

此外，无论其他人说什么，当涉及到数据技术时，避免定性分配，如“更好”或“更差”。坚持“最合适”事实是，在 21 世纪，SQL Server(本地或云中)有时仍然适用，有时则不适用。

选择是好事！

### 没有坏狗

考虑将狗的个性赋予数据库技术的想法。和我呆在一起！我试图揭开一些更受欢迎的 Azure 数据产品的神秘面纱。

我的第一次数据库体验是一个非常早期的 FoxPro 版本(这次你可能需要使用 Wayback 机器)。它很像我家的第一只狗，松饼。马芬看起来有点像狐狸，但更重要的是，它是一只普通的郊区杂种狗。FoxPro 也很简单。

在 70 年代和 80 年代，我们给我们的宠物喂可怕的、便宜的狗粮或人粮——嗯，这表现在它们每天在后院的堆积上。吉戈最糟糕的时候，但这显然让他活了 17 年。我有什么资格批评？如果不栓上皮带的话，马芬会有点不守规矩，而且像 FoxPro 一样，他很脏，身后会留下泥泞的爪印和头发。

快进十年左右，想想 Obie，黄色实验室。他是我们的 SQL Server 狗:可靠、忠诚、训练有素、可预测。他吃更高质量、更贵的狗粮，是不吃吉戈的完美典范。只要我们给予他爱和关注，这个家庭就会和平和谐。我们可以和奥比交谈，问他问题(如果一个人倾向于扭曲的隐喻，可以说我们*问他*)，我们愿意相信他理解我们。我们也不需要向任何人解释他。大家一看就知道是黄色实验室。

然后，我的第一次云数据体验是 blob 存储。非结构化的大数据，存储安全简单。不像我们的下一只狗，格鲁纳，一只漂亮的大白熊，它大部分时间都在睡觉。

但是当山羊或鸡需要保护时(或者门铃响了)，他真的会立刻行动起来。他有一些令人钦佩的特征，他能跑得像风一样快。就像保存在 blob 存储容器中的图像一样，大白熊是一种视觉媒介。肢体语言比口头交流更重要。

它们都是独一无二的，没有一个一定比另一个更好。

## 不同品种:流行的 Azure 解决方案，简单解释

我不会用我们家狗的额外照片来烦你，但这里有一些 Azure 中更受欢迎的数据资源的快速总结。这不是一个详尽的列表，但应该让您了解一些使它们成为您的云或混合解决方案的一部分所需的技能和语言。

作为一名 SQL Server 专业人员，您会发现，就培训和经验而言，您真的不是那么离谱。

### **拉布拉多猎犬:**虚拟机上的 SQL Server

![](img/b6c26aed5a4381f2d71057656a2ed854.png)

宠物性格:可预测，可靠，可训练。

**类型和用途:**一种关系数据库，最适合用于事务性数据，其中强一致性和强制结构非常重要。因为在虚拟机上安装使其成为 IaaS(基础架构即服务)产品，所以这种 SQL Server 选项可能最适合希望对维护、调整和典型的本地数据库管理员职责保持更多控制的客户。

**替代:** Azure SQL，Azure Database for MySQL，for PostgreSQL，for Maria DB

**SQL(或类似 SQL)支持:**是

****产品信息:**** [点击这里](https://azure.microsoft.com/en-au/services/virtual-machines/sql-server/)

### **拉布拉多:** Azure SQL 家族

![](img/852e364755c3cf3872bbec03d779b0b7.png)

**宠物个性:**与拉布拉多犬相似，但体型较小，需要吸尘的皮毛较少。

**类型和用途:**关系数据库最适合用于事务性数据，其中强一致性和强制结构非常重要。作为一个 PaaS 产品，通过一个完全“无服务器”的选项，该平台是完全托管的。但是，选择托管实例 sku 的客户保留了一些控制权。

**替代:** SQL Server，Azure Database for MySQL，for PostgreSQL，for Maria DB

**SQL(或类似 SQL)支持:**是

**产品信息:** [点击此处](https://azure.microsoft.com/en-au/products/azure-sql/)

### **金毛猎犬:** Azure 数据库用于 MySQL/PostgreSQL/Maria DB

![](img/4bccd2c2340b7269cabda78e5a2cf81a.png)

**宠物性格:**类似于实验室的性格和品质。

**类型和用途:**关系数据库最适合用于事务性数据，其中强一致性和强制结构非常重要。完全管理或大部分管理，取决于 sku。非常适合快速迁移已经采用这三种技术之一的现有数据库。

**替代:** SQL Server，Azure SQL

**SQL(或类似 SQL)支持:**是

**产品信息:** [MySQL](https://azure.microsoft.com/en-au/services/mysql/) [，](https://azure.microsoft.com/en-au/services/mysql/) [PostgreSQL](https://azure.microsoft.com/en-au/services/postgresql/) ， [MariaDB](https://azure.microsoft.com/en-au/services/mariadb/)

### **伯恩山犬:** Azure Synapse Analytics

![](img/16c81790eb5acaad488e2c9df307031c.png)

**宠物个性:**瑞士本土农场的大型、勤劳、多才多艺的狗。他们擅长制图和搬运。

**类型和用途:**MPP(大规模并行处理)分析平台，具有基于 SQL 数据仓库的存储组件和一组其他服务，如 Azure Data Factory。非常适合关系和非关系数据库资源上的分析工作负载。

**替代:** Azure HDInsight，基于 Apache 开源平台，也是 MPP 服务，但捆绑服务较少。Apache 技术在许多大数据应用程序中处于领先地位，这是 SQL Server 专业人员可能不熟悉的许多语言和术语的来源。但是不要让这阻止你开始使用 Azure。到时候你会知道你需要知道的。

**SQL(或类似 SQL)支持:**是

**产品信息:** [点击此处](https://azure.microsoft.com/en-us/services/synapse-analytics/)

### **杰克罗素梗:**蔚蓝数据工厂

![](img/2179535e52ef2477df1284cf020c446d.png)

**宠物性格:**障碍赛上最敏捷的狗之一。

**类型和用途:**一款高度灵活、完全托管的数据集成工具，用于传统和大数据 ETL 工作负载。

**替代:** SSIS，可以托管在 ADF 管道内部。

**SQL(或类 SQL)支持:**不一定适用于所有情况，但在有意义的地方支持。如果您熟悉 SSIS 或其他“工作流”风格的数据集成工具，那么通过一些培训，您可以使用 ADF。

**产品信息:** [点击此处](https://azure.microsoft.com/en-au/services/data-factory/)

### **德国品酒师:**宇宙 DB

![](img/28e0072d4b73478fe0959ba48ffb7c45.png)

**宠物性格:**工作犬的“瑞士军刀”。一个热爱工作并擅长许多不同工作的品种。

**类型和用途:**多模型数据库，弹性规模不限，全球分布。适用于从游戏到电子商务和事务性工作负载的各种使用情形。“多模型”,因为原生格式是 JSON，带有 SQL 查询，但也有用于 Cassandra 宽列、Gremlin 图、PostgreSQL、Mongo DB 和键值对格式的其他 API。

其他文档数据库，但 Azure 中没有类似的。

**SQL(或类 SQL)支持:**对，核心 API 是 SQL over JSON 文档。

**产品信息:** [点击此处](https://azure.microsoft.com/en-au/services/cosmos-db/)

### **大白熊:** Azure Blob 存储和 Azure Data 湖存储第二代

![](img/5c7374ce0140f9e064cd626c750cbbf8.png)

宠物性格:可能睡得很多，这取决于工作分配，但反应很快。拥有短跑运动员的体格和马拉松运动员的耐力。

**类型和用途:** Blob 存储针对存储、服务和流式传输大量非结构化数据(如音频、视频、图像和日志数据)进行了优化。

Azure 中没有类似的东西。

**SQL(或类 SQL)支持:**是的，有点，但我们不去那里。有更好的方法来处理非结构化数据。这将是一个有趣的培训机会！

**产品信息:** [蔚蓝博客存储](https://azure.microsoft.com/en-au/services/storage/blobs/)，[蔚蓝数据湖存储 Gen2](https://docs.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-introduction)

## 你如何带头

那么，你如何温习那些可能仍然存在于你的知识中的小缺口呢？我强烈推荐去看看云专家的图书馆，里面有 Azure 课程和动手实验室。在 Azure 冒险中，无论您身在何处，都可以找到学习资源。

如果你对认证感兴趣(谁不喜欢另一张纸告诉他们他们很棒呢？)我建议阅读 Lars Klint 的这篇精彩文章:“[对我来说，最好的微软 Azure 认证途径是什么？](https://acloudguru.com/blog/engineering/which-azure-certification-is-right-for-me)

*想跟上天蓝色的一切？[在 YouTube 上订阅云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每周亚马逊新闻和 AWS 公告。你也可以在[脸书](https://www.facebook.com/acloudguru)上喜欢 ACG，在 [Twitter](https://twitter.com/acloudguru) 上关注我们，或者在 [Discord](https://discord.gg/NwfDnNj54T) 上加入对话！*