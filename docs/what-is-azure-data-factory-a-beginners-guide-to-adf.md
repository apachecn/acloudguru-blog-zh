# 什么是 Azure 数据工厂？ADF 初学者指南

> 原文：<https://acloudguru.com/blog/engineering/what-is-azure-data-factory-a-beginners-guide-to-adf>

微软 Build 2021 目前正在进行中，这是一个初学者友好地深入了解 Azure Data Factory 的最佳时机。在这篇文章中，我们将讨论什么是 Azure Data Factory，如何开始使用它，以及你可能会用它来做什么。

*跟上 ACG 原创系列[蔚蓝本周](https://acloud.guru/series/azure-this-week)* 一切蔚蓝！

## 什么是 Azure 数据工厂？

Azure Data Factory (ADF)是一个完全托管的、无服务器的数据集成解决方案，用于接收、准备和大规模转换所有数据。它使每个行业的每个组织都可以将它用于各种各样的用例:数据工程、将他们的内部 SSIS 包迁移到 Azure、运营数据集成、分析、将数据接收到数据仓库等等。

*图 1 Azure 数据工厂——行业领先的企业数据集成*

如果您有许多用于内部数据集成的 SQL Server Integration Services(SSIS)包，这些 SSIS 包在 Azure Data Factory 中按原样运行(包括自定义 SSIS 组件)。这使得任何开发人员都可以使用 Azure Data Factory 来满足企业数据集成需求。

* * *

*查看 Azure Data Factory 的[视觉指南，了解 ADF 的整体情况。](https://acloudguru.com/blog/engineering/a-visual-guide-to-azure-data-factory)*

* * *

**任何数据存储的企业连接器**–Azure Data Factory 使组织能够从各种数据源获取数据。无论数据源是内部的、多云的，还是由软件即服务(SaaS)提供商提供的，Azure Data Factory 都可以连接到所有这些数据源，而无需额外的许可成本。使用[复制活动](https://docs.microsoft.com/en-us/azure/data-factory/copy-activity-overview)，您可以在不同的数据存储之间复制数据。

Azure Data Factory 使您能够轻松连接到许多业务数据源，大规模转换它们，并将处理后的数据写入选择的数据存储中，从而缩短洞察时间。例如，您可以使用 Azure Data Factory 连接到 Microsoft Dynamics 365 提供的以下业务应用程序–Dynamics 365 用于营销销售、客户服务、现场服务等。这使得 Azure Data Factory 能够[从 Microsoft Dynamics 365](https://docs.microsoft.com/en-us/azure/data-factory/connector-dynamics-crm-office-365) 复制数据，并以正确的形式将数据复制到最需要支持关键业务报告的地方。除了连接到 Microsoft Dynamics 365，Azure Data Factory 还支持各种各样的广告和营销数据源:Salesforce、Marketo、Google AdWords 等等。

* * *

[![Complete guide to the Cloud and Dictionary ](img/93ebf63b88ab7fbd48705a01952ba688.png)](https://get.acloudguru.com/cloud-dictionary-of-pain)

[**获得痛苦的云词典**](https://get.acloudguru.com/cloud-dictionary-of-pain)
说云不一定要努力。我们分析了数百万份回复，找出了最容易让学生出错的术语和概念。在这个[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)中，你会发现一些最令人头疼的云术语的简洁定义。

* * *

**内部数据访问**–对于许多组织来说，内部都有企业数据源。Azure Data Factory 使组织能够使用[自托管集成运行时](https://docs.microsoft.com/en-us/azure/data-factory/create-self-hosted-integration-runtime#command-flow-and-data-flow)连接到这些本地数据源(我们将在下一节介绍集成运行时的概念)。自托管集成运行时使组织能够在内部和云数据源之间移动数据，而不需要您打开任何传入网络端口。这使得任何人都可以轻松地安装运行时并实现混合云数据集成。

**无代码数据流**–Azure Data Factory 使任何开发人员都能够通过无代码数据流加速数据转换[的开发。通过使用 ADF Studio，任何开发人员都可以设计数据转换，而无需编写任何代码。要在 Azure Data Factory 中设计数据流，首先要指定要从中获取数据的数据源，然后在将数据写入数据存储之前，可以对数据应用一组丰富的转换。在底层，Azure Data Factory 使用 Spark 集群为您大规模运行这些数据流。无论是处理兆字节数据(MB)还是万亿字节数据(TB)，Azure Data Factory 都可以在 spark 级别运行数据转换，而无需您设置 Spark 集群或对其进行调整。从许多方面来说，数据转换是可行的！](https://docs.microsoft.com/en-us/azure/data-factory/data-flow-create)

**安全数据集成**–Azure Data Factory 通过连接到各种 Azure 数据存储支持的私有端点来支持[安全数据集成](https://docs.microsoft.com/en-us/azure/data-factory/managed-virtual-network-private-endpoint)。为了减轻管理自己的虚拟网络的负担，Azure Data Factory 在幕后管理虚拟网络。这使您可以轻松建立数据工厂，并确保所有数据集成都在虚拟网络中安全进行。

**CI/CD 支持**–Azure Data Factory 支持任何开发人员将其作为持续集成和交付(CI/CD)流程的一部分。带有 Azure Data Factory 的 CI/CD 使开发人员能够将数据工厂资产(管道、数据流、链接服务等)从一个环境(开发、测试、生产)移动到另一个环境。开箱即用，Azure Data Factory 提供了与 Azure DevOps 和 GitHub 的原生集成。

* * *

* * *

## 数据集成和治理

将数据集成和数据治理结合在一起，使组织能够获得对沿袭、策略管理等的深刻见解。Azure Data Factory 与[Azure without](https://azure.microsoft.com/services/purview/)进行了本机集成，以提供对 ETL 血统的强大洞察力，以及数据如何从各种数据存储在组织中移动的整体视图，等等。

例如，一个数据工程师可能想要调查一个数据问题，其中由于上游问题而插入了不正确的数据。通过使用 Azure 数据工厂与 Azure 权限的集成，数据工程师现在可以很容易地发现问题。

[了解更多关于如何将 Azure 数据工厂血统集成并提供给 Azure without 的信息](https://docs.microsoft.com/en-us/azure/data-factory/turorial-push-lineage-to-purview)。

*图 2–Azure 数据工厂和 Azure 权限一起*

## Azure 数据工厂的基本要素

图 2 提供了 Azure 数据工厂概念的快速概述，可以帮助您入门。

*   [**触发**](https://docs.microsoft.com/en-us/azure/data-factory/concepts-pipeline-execution-triggers#trigger-execution)–指定数据管道运行的时间。Azure 数据工厂支持不同类型的触发器。计划触发器使您能够指定数据管道在一天中的特定时间(包括时区)运行。

    您还可以使用数据窗口触发器，指定基于一系列固定大小、不重叠、连续的时间间隔触发触发器。数据窗口触发器也可以依赖于其他数据窗口触发器。

    当数据被创建/插入 Azure 存储时，存储事件触发器使您能够运行数据管道。自定义事件触发器将存储事件的丰富性扩展到所有推入 Azure 事件网格的自定义事件。

*   [**管道和活动**](https://docs.microsoft.com/en-us/azure/data-factory/concepts-pipelines-activities)–管道由一组不同的活动组成。Azure Data Factory 中的活动可以帮助您复制数据，使用数据流执行数据转换，以及 Azure 上的各种其他计算。您还可以在管道中指定迭代和逻辑构造。

*   **[集成运行时](https://docs.microsoft.com/en-us/azure/data-factory/concepts-integration-runtime)**–集成运行时(IR)是 Azure Data Factory 用于执行各种数据集成任务(例如，数据移动、数据流、运行 SSIS 包、在 Azure 上的各种计算上运行代码)的计算基础设施

*图 3–Azure 数据工厂概念*

*图 4 Azure 数据工厂学习路径*

## Azure 数据工厂入门

在 [Azure Docs](https://docs.microsoft.com/en-us/azure/data-factory/) 和 [Azure Data Factory YouTube 频道](https://aka.ms/adfvideos)上有许多资源可以帮助技术社区开始使用 Azure Data Factory。此外，您可以通过使用 [Azure 数据工厂学习路径](http://aka.ms/adf/azurelearn)(Azure Learn 的一部分)开始学习。或者看看 ACG 的[在 Azure Data Factory 动手实验室开发管道](https://acloudguru.com/hands-on-labs/developing-a-pipeline-in-azure-data-factory)。

我们迫不及待地想看看你能用 Azure Data Factory 构建什么！

提升你的 Azure 技能。

* * *

## 掌握现代技术技能，获得认证，并与 ACG 一起推进您的云计算职业生涯。查看我们当前的[免费 Azure 课程](https://acloudguru.com/blog/news/whats-free-at-acg-may-2021)或[获得 7 天免费试用](https://acloudguru.com/pricing)。

Master modern tech skills, get certified, and advance your career in cloud with ACG. Check out our current [free Azure courses](https://acloudguru.com/blog/news/whats-free-at-acg-may-2021) or [get a 7-day free trial](https://acloudguru.com/pricing).