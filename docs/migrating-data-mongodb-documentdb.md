# 将数据从 MongoDB 迁移到 DocumentDB 的 5 个技巧

> 原文：<https://acloudguru.com/blog/engineering/migrating-data-mongodb-documentdb>

试图将数据从您现有的 MongoDB 实例迁移到一个 [Amazon DocumentDB](https://aws.amazon.com/documentdb/) 集群中？这可能是一个非常复杂的过程，但不需要如此。在本帖中，我们分享了如何简化这一过程，并减少对现有生产应用程序的影响的五个技巧。

## **1。确定你的消息来源**

在开始任何迁移之前，收集关于将要迁移到 Amazon DocumentDB 集群的信息源的信息是很重要的。

确保对关于源代码的特定信息进行编目，比如应用程序所有者和 MongoDB 的版本。如果您有适用于该应用程序的服务级别协议(SLA ),也要捕获它。

掌握所有这些信息将确保您为迁移的后续步骤做好准备。

## **2。使用 VPN 或 AWS 直接连接**

在最简单的情况下，MongoDB 服务使用与 DocumentDB 集群相同的[虚拟私有云](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html) (VPC)运行。如果不是这样，您需要使用虚拟专用网络(VPN)或 [AWS Direct Connect](https://docs.aws.amazon.com/directconnect/latest/UserGuide/Welcome.html) 服务将数据从您的内部 MongoDB 集群迁移到 Amazon DocumentDB 集群。

由于这种限制，在识别源时注意源数据库的位置是很重要的。确保包括访问源所需的任何凭证。

## **3。使用 mongodump 和 mongorestore 进行简单的迁移**

使用 [mongodump](https://www.mongodb.com/docs/database-tools/mongodump/) 和 [mongorestore](https://www.mongodb.com/docs/database-tools/mongorestore/) 工具可以完成较小集合的简单迁移。这些工具使用二进制格式，在保留所有数据的同时确保文件尽可能小。它们可用于迁移正常运行时间服务级别协议更宽松的开发和 QA 环境，或者用于概念验证迁移，以允许在新环境中进行应用程序测试。

您也可以使用 mongoexport 和 mongoimport 工具，但是这些命令使用基于文本的 JSON 或 CSV 格式，比 mongodump 和 mongorestore 使用的二进制格式要慢。

## **4。创建隐藏的副本集成员**

为了提高迁移性能并减少对生产数据库的影响，请确保使用[隐藏副本集成员](https://www.mongodb.com/docs/v5.0/core/replica-set-hidden-member/)。这些成员仍然接收操作日志更新，并将在初选中投票，但他们不处理来自客户端的请求。这为迁移过程释放了资源，并确保它不会干扰生产流量。

如果可能，在与 Amazon DocumentDB 集群相同的 VPC 中创建隐藏成员。

## **5。使用 DMS 进行在线迁移以减少停机时间**

没人喜欢停工。为了最小化对可用性的影响，使用[数据库迁移服务](https://docs.aws.amazon.com/dms/latest/userguide/Welcome.html) (DMS)来迁移数据。

DMS 允许您在源数据库和目标数据库之间持续迁移更新，使它们保持同步。这允许现有应用程序在迁移过程中继续更新 MongoDB 数据库。

一旦两个数据库都是最新的，您就可以在维护窗口期间将应用程序切换到 DocumentDB 集群。这最大限度地减少了迁移导致的停机时间。

## **总结**

让我们面对现实吧，将生产应用程序迁移到新的数据库是一项艰巨的任务。但是，通过花时间确定你的消息来源——并确保你与这些消息来源有正确的联系——你可以减少你抓狂的几率。

使用 mongodump 和 mongorestore 工具执行概念验证迁移可以让您执行应用程序测试，从而更快地发现问题。当您准备好进行最终迁移时，请确保使用数据库迁移服务从隐藏的副本集成员中提取数据。这有助于将对现有生产环境的影响降至最低

## **在你迁移之前，温习一下 DocumentDB & AWS**

在您移动数据之前，确保您尽可能了解有关 Amazon DocumentDB 的所有信息会很有帮助。最好的方法之一是在真实的、无风险的现场环境中获得一些实践经验。

一位云专家提供了一门[掌握 Amazon DocumentDB](https://acloudguru.com/course/hands-on-with-amazon-documentdb) 课程，该课程深入介绍了如何设置、保护和扩展与 MongoDB 兼容的数据库。该课程提供专家视频建议、数十个[动手实验](https://acloudguru.com/platform/labs)，以及测试你知识的考试。

完成本课程后，您不仅可以成功完成数据迁移，还可以在未来与 DocumentDB 合作。