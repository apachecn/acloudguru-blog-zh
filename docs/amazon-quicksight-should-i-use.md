# 亚马逊 QuickSight:使用前要问的 3 个重要问题

> 原文：<https://acloudguru.com/blog/engineering/amazon-quicksight-should-i-use>

Amazon QuickSight 是 AWS 的商业智能(BI)服务，旨在提供来自 AWS 上或 AWS 外的数据源的交互式数据可视化。作为一种云原生和无服务器服务，QuickSight 是一种配置强大 BI 解决方案的简单方法，该解决方案可轻松连接到您的云数据源，并可根据用户需求进行扩展或缩减。

在您决定使用 Amazon QuickSight 作为您的 BI 解决方案之前，有一些事情需要考虑，以确保它能够满足您的成本和性能需求。 [QuickSight 定价](https://aws.amazon.com/quicksight/pricing/)和管理可能很难解析，但我在本文中分解了主要组件，以便为您的 QuickSight 之旅提供一个良好的开端。

所以，在你一头扎进 QuickSight 之前，问问你自己这三个问题:

## 1.需要多少用户？

Amazon QuickSight 成本的最大驱动因素通常是为该应用程序提供的用户数量。用户基本分为两种角色:**作者**和**读者**。

**作者**是将从您的数据源创建数据集并创作数据可视化的用户。每个作者用户都有一个固定的月价格，从 12 美元/月到 34 美元/月不等，取决于您选择的功能包。如果您选择按年预付而不是按月支付，您也可以将这个范围减少到 9 美元/月到 28 美元/月。

**读者**按会话付费，而不是按用户付费。读者可以被授予查看和与创作的仪表板交互的权限，但不能编辑或创作它们。一个 reader 会话费用为 0.30 美元/会话，每个 reader 用户有一个月最高费用，通常为 5 美元。因此，即使一个读者一个月内记录了数千个会话，你最多只能为这个读者支付 5 美元。但是如果一个读者根本不用 QuickSight，你就不用付钱了！这是现收现付定价模式的一大优点。

## 2.你的用户和数据在哪里？

当谈到在云中托管应用程序时，这是我们不常考虑的事情；但是，在您调配 QuickSight 之前，从物理意义上考虑您的用户和数据的位置非常重要。

如果您最关心的是成本，请仔细考虑您的数据在哪里，并确保在离您的数据最近的 AWS 区域提供 QuickSight 应用程序。毕竟，如果您的数据托管在 AWS 上，您将为传输到 QuickSight 进行分析的数据付费。因此，您的 QuickSight 应用程序离您的数据越近，这些数据传输的性能和成本效益就越高。例如，如果您使用 us-west-2 区域来托管您希望在 QuickSight 中分析的 RDS 数据库，您应该在 us-west-2 中提供 QuickSight。

如果您最关心的是最终用户的性能，那么考虑您的用户在访问 QuickSight 应用程序时的实际位置也很重要。在更接近最终用户的区域配置 QuickSight 将带来更快、更具性能的用户体验。

## 3.您希望如何分享数据见解？

Amazon QuickSight 中提供的不同功能包价格相差很大，很难判断哪个包适合您的组织。大多数情况下，这个决定取决于您希望如何共享您创建的数据可视化。

标准版是最基本的 QuickSight 软件包，是开始尝试 QuickSight 的好地方。你每月为每个作者支付 12 美元，而且你不能提供读者。这意味着所有可视化只能在 QuickSight 应用程序上访问，并且只能由作者访问。这对于只需要在内部授予对仪表板的访问权限的小型团队来说非常有用。

企业版每位作者的费用为 24 美元，但允许更多的方法来分享你的仪表板和报告。借助企业版，您可以提供阅读器、将仪表板嵌入 web 应用程序、定期发送电子邮件报告等等。对于数据安全性和对数据源的访问，您还可以获得更加健壮和细粒度的特性。如果您有数十或数百名读者，即您希望授予访问权限以查看您的数据可视化的用户，那么 Enterprise edition 非常有用。

QuickSight 还提供了无数的附加功能，包括[阅读器会话容量定价](https://aws.amazon.com/blogs/big-data/new-in-amazon-quicksight-embedding-without-user-provisioning-session-capacity-pricing-and-embedded-developer-portal/)、[分页报告](https://aws.amazon.com/quicksight/paginated-reports/)，以及 [QuickSight Q](https://aws.amazon.com/quicksight/features/) 。我对这些附加功能的一般建议是，尽可能从最基本的可行功能包开始，只有当你发现附加功能物有所值时才升级或附加。升级非常容易，但降级会导致现有仪表板复杂化。

## 结论

现收现付定价是 QuickSight 的最大优势之一，但它也可以创造更多的前期工作来了解您的组织对您的 BI 解决方案的需求。本文应该为您提供了足够的信息来开始使用 QuickSight，但是仍然存在连接数据源、创建数据集、创作可视化以及共享可视化的问题！

要回答您可能对使用亚马逊 QuickSight 有任何疑问，请查看我的课程“[亚马逊 QuickSight 深度探索](https://learn.acloud.guru/course/aws-quicksight-deep-dive/overview)”。本课程面向 AWS 管理员 provisioning QuickSight、使用 QuickSight 的数据分析师或介于两者之间的任何人。

祝你在数据洞察的旅途上好运，互相照顾，保持牛逼！