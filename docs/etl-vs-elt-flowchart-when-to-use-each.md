# ETL 与 ELT 流程图:何时使用两者

> 原文：<https://acloudguru.com/blog/engineering/etl-vs-elt-flowchart-when-to-use-each>

在这篇文章中，我们将讨论 ETL 和 ELT 之间的区别，以及什么时候你可以选择 ETL 或 ELT。我们还将包括一个流程图，帮助您完成 ETL 与 ELT 的决策过程。

## ETL 和 ELT 的区别

ETL 和 ELT 有什么区别？简而言之，这完全取决于你何时转型。更长的答案？好吧，继续读下去！

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

ETL 过程

* * *

### ETL(或提取、转换、加载)是将数据收集到中央数据仓库进行分析的过程。

**提取**:传统的 ETL 过程首先提取数据。在这个步骤中，应该检查数据的有效性，任何无效的数据都可以被返回或纠正。

*   **转换**:接下来执行任何必要的转换。转换是业务和技术需求所要求的一系列规则或功能。它们可以是任何东西，从确保数据的正确格式到将数据与其他数据源相结合。

*   **加载**:最后，数据将被加载到最终目标系统中。这可以是任何东西，从简单的平面文件到基于云的数据仓库。

*   英语教学过程

### 这就是 ETL 过程，但是 ELT 过程呢？好吧，记住:这都是关于你什么时候转型。

根据所需的转换和您选择的类型端点，您可能希望在加载数据之后转换数据*。这被称为 ELT 过程(或提取、加载、转换)。当加载到提供足够处理能力来执行任何所需转换的最终目标时，这很有用。*

ETL 与 ELT 流程图

## 这个方便的流程图可以帮助你决定哪个过程适合你。

何时选择 ETL 还是 ELT

## 如果您的端点目标是基于云的数据仓库，比如 Amazon Redshift 或其他关系数据库，那么在加载之后执行转换是轻而易举的事情。加载后，可以使用 SQL 查询语言转换数据。复杂的转换可以根据需要轻松运行和更改。

如果您的端点是像数据湖一样的平面存储，那么任何转换都应该在加载之前*运行，因为这种存储几乎不能执行转换。为了使用更具成本效益的存储，您需要在加载之前执行转换。*

您希望运行的转换的性质也将在您选择的过程中发挥作用。

无论是什么类型，在加载到端点之前都应该执行非常简单的转换。这些转换中的许多也可能属于流程中的数据清理或数据验证步骤。在加载前完成这些操作可确保加载一致的数据集。

在 ETL 和 ELT 之间进行选择时，关键在于何时以及如何进行转换。如果您的转换很简单，并且/或者您的端点不支持复杂的转换，那么您应该明确地选择一个 ETL 过程，并在加载之前执行转换。但是，如果您的转换很复杂，并且经常发生变化，并且您的端点支持处理能力，那么 ELT 流程可以让您在加载数据后灵活地运行任何转换。

了解有关 ETL 和 ELT 的更多信息

## 想了解更多关于 ETL 和 ELT 的知识吗？查看 ACG 的 ETL 和 ELT 基础课程。

本课程将讨论 ETL 过程中每一步所需的步骤，并着眼于一些现实场景的不同解决方案。我们将探索从多种来源和格式中提取数据，对数据执行转换，最后将数据加载到最终位置。

本课程假设您对关系数据库以及标准 Unix 命令行工具(如 sed、grep 和 awk)有一定的经验。

准备开始了吗？[现在就开始免费试用](https://acloudguru.com/pricing)，继续保持出色，云大师们！

[**成年人的 NoSQL:DynamoDB 单表建模**](https://get.acloudguru.com/nosql-for-grownups-dynamodb-webinar) 在[这个免费的点播网络研讨会](https://get.acloudguru.com/nosql-for-grownups-dynamodb-webinar)中，里克·霍利汉，AWS 的高级实践经理和单表 DynamoDB 设计的发明者，展示了他在 dynamo db 中建模复杂数据访问模式的技巧。

* * *

[**NoSQL for Grownups: DynamoDB Single-Table Modeling**](https://get.acloudguru.com/nosql-for-grownups-dynamodb-webinar) In [this free on-demand webinar](https://get.acloudguru.com/nosql-for-grownups-dynamodb-webinar), Rick Houlihan, Sr. Practice Manager at AWS and inventor of single-table DynamoDB design, shows his tricks for modeling complex data access patterns in DynamoDB.