# 冷却 Azure Cosmos DB 中的热分区

> 原文：<https://acloudguru.com/blog/engineering/cooling-hot-partitions-azure-cosmos-db>

当使用 Azure Cosmos DB 时，您将承担的主要设计活动之一是适当的分区设计。分区允许您将数据分块到各个容器中，创建称为逻辑分区的不同子集。以这种方式使用分区使 Cosmos DB 能够兑现其“无限水平可伸缩性”的承诺。

因此，让我们深入了解一下是什么让分区变得又冷又热。

**均匀分布很酷**

逻辑分区由数据中的关键属性定义，例如客户标识符、仓库位置或产品类别。这些被恰当地称为*分区键*。然而选择一个好的分区键并不总是容易的！这个想法是选择一个*逻辑*分区键，这自然会导致在底层*物理*分区基础设施上的均匀分布。

例如，如果您在一个地区有成千上万的客户，但其中 90%位于斯普林菲尔德市，那么设置分区键“city”将导致不均匀的分布。这将导致该城市客户的高流量和存储需求，并产生所谓的“热”分区。

**…热分区，不太冷**

现在，有时候“热”也是好的:热玉米粉蒸肉、热狗，还有游泳池边的热天。热分区并不那么有趣。这些通常会超过提供给它们的吞吐量，从而导致限制和连接失败。一些热分区还会给物理资源带来存储压力，虽然这些物理资源在一定程度上是可扩展的，但也有实际限制。

Microsoft 提供了几种方法来设置和调整 Cosmos DB 数据库和容器上的输入。吞吐量配置和谨慎的分区选择通常可以避免热分区，您可以在我的课程 [DP-420:使用 Microsoft Azure Cosmos DB](https://acloudguru.com/course/dp-420-designing-and-implementing-cloud-native-applications-using-microsoft-azure-cosmos-db) 设计和实现云原生应用中了解关于吞吐量、分区键设计和其他*热*主题的所有信息。然而，有时候即使是一个好的分区键，再加上精心的吞吐量配置，也不足以保持凉爽。

**分层分区提供了一些阴影**

幸运的是，微软最近发布了两项新功能，可以提供帮助。第一个是分层分区，它允许您选择多达三个级别的分区。

例如，假设您为一家连锁酒店工作，其中许多特许经营者有不止一个位置。选择 FranchiseID 属性作为键可能是有意义的，但是如果结果仍然导致热分区，那么您现在可以首先按 FranchiseID 分区，然后按 HotelID 分区。如果你还在水深火热中，尝试多一层，比如一个楼号或楼层号。

这类似于 Cosmos DB 中现有的合成键分区功能，但是设计开发和实现的复杂性要低得多。此功能仍在预览中，DP-420 考试不需要，因此，还没有包括在我的认证课程中。但你可以在这里了解更多:[Azure Cosmos DB(预览版)中的分层分区键|微软学习](https://learn.microsoft.com/en-us/azure/cosmos-db/hierarchical-partition-keys?tabs=net-v3%2Cbicep)

**需要消防软管时的目标吞吐量**

我更感兴趣的第二个预览特性是跨物理分区分配吞吐量的能力。

默认情况下，Azure Cosmos DB 在所有物理分区之间平均分配供应的吞吐量。这意味着，当热分区被自己的烟呛到时，低流量分区的数据却坐在空调里，可能希望他们能把它关小一点。

对于这些场景，您现在能够跨物理分区重新分配您所调配的吞吐量，而不必根据最热的分区来增加总体吞吐量。这有点像分区恒温器。假设您调配了 10，000 RU/s。您可以决定将其中的大部分(6000 RU/s)分配给热分区，其余分配给 Cosmos house 中较冷的房间。

要了解更多关于如何注册这个预览功能，以及当前的限制和警告，请访问 Azure Cosmos DB | Microsoft Learn 中的[跨分区重新分配吞吐量(预览)。](https://learn.microsoft.com/en-us/azure/cosmos-db/nosql/distribute-throughput-across-partitions)

与此同时，另一个不相关的生活小贴士:如果泳池派对对你来说只是一个梦，感觉罗马正在四处燃烧，拿出棉花糖，拉把椅子。这一切都会过去。