# 一月新闻综述:AWS 有什么新功能？

> 原文：<https://acloudguru.com/blog/engineering/january-news-roundup-whats-new-with-aws>

你好，云大师！想知道 AWS 这个月发生了什么变化，但还没有找到时间查看几周的头条新闻？这里是你需要知道的所有信息。

## S3 默认加密

默认情况下，S3 现在会自动加密所有新文件。它对您上传的所有新对象使用 S3 管理的服务器端加密，也称为 SSE-S3，无需额外成本，也不会影响性能。

现在这种类型的加密使用 AES-256 位加密，这是服务器端加密的行业标准。这将适用于所有新的和现有的存储桶。上传的新对象将被加密，但现有对象不会改变。

您仍然可以指定其他类型的加密，例如 SSE-C，它使用客户提供的加密密钥，或者 SSE-KMS，它使用 KMS 管理的加密密钥，但是您不能禁用新对象的自动加密。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## 训练 Sagemaker 画布模型的速度提高了 3 倍

Sagemaker Canvas 现在训练机器学习模型的速度比以前快了 3 倍。

如果你不熟悉 Sagemaker Canvas，它是一种允许业务分析师使用可视化界面生成机器学习预测的服务，不需要任何机器学习专业知识。它提供了一个拖放界面，这意味着您可以轻松地生成预测，而不必编写任何代码。

[随着此次发布](https://aws.amazon.com/about-aws/whats-new/2023/01/amazon-sagemaker-canvas-3x-faster-ml-model-training-time/)，他们已经进行了一些重大的性能优化，使您能够构建训练速度比以前快 3 倍的机器学习模型。对于那些需要快速试验不同模型、快速创建原型并更快实现业务成果的公司来说，这将是一件好事。

## **两个新的 Kendra 连接器——S3 和谷歌驱动**

Amazon Kendra 现在有两个新的连接器，可以让你轻松地索引和搜索 S3 和 Google Drives 中的文档。

如果你以前没有使用过 Kendra，它是一种智能搜索服务，由机器学习驱动，允许你使用自然语言处理搜索结构化和非结构化数据。因此，这意味着您可以使用普通语言向 it 部门提问，而不必编写复杂的代码或查询。

例如，您可以让 Kendra 搜索您提供的 FAQ 文档，并向它询问类似“我如何配置 VPN？”它会在提供的文档中为您找到该信息。

现在有两个新的连接器，[第一个是用于 S3 的](https://aws.amazon.com/about-aws/whats-new/2023/01/amazon-kendra-s3-connector-vpc-support-enable-customers-index-search-s3/)，它允许您安全地索引和搜索存储在 S3 的文档，包括为每个对象存储的元数据。这个新的连接器使 Kendra 能够使用 VPC 连接到您的 S3 数据源，这意味着您不需要使用公共互联网访问数据。

[第二个新连接器是用于 Google drives](https://aws.amazon.com/about-aws/whats-new/2023/01/amazon-kendra-google-drive-connector-document-indexing-search-google-drive) 的，这允许你索引和搜索存储在你自己的 Google Drive 和与你共享的 Drive 中的文档。这包括 HTML 文件、Powerpoint 演示文稿、pdf、Word 文档和 CSV 文件等结构化文档。

## **预览版中可用的 AWS 洁净室**

去年 re:Invent 发布的众多数据安全公告之一是首次关注一项名为 [AWS Clean Rooms](https://aws.amazon.com/clean-rooms/) 的新服务。本月，AWS 宣布你可以亲自体验洁净室，因为它现在可以在 11 个不同的地区进行预览。

洁净室旨在保护您的业务数据的秘密和安全，同时仍允许分析师从您的集体数据中获得洞察力。邀请合作者并精细控制每个洁净室参与者可以使用的数据和查询。这是一种全新的安全方式，可以在数据洞察方面进行协作，同时确保您的敏感数据在分析过程中保持安全和加密。

这对于市场营销和广告活动分析，或者任何希望在不暴露所有底层数据的情况下协作进行数据分析的情况来说，都是非常棒的。

## **AWS 网络防火墙现在支持 IPv6】**

在其他安全新闻方面，AWS 本月宣布，AWS 网络防火墙现在完全支持 IPv6。

网络防火墙是一种受管理的防火墙服务，允许您过滤进出 VPCs 或内部网络的流量。[您现在可以启用网络防火墙端点来过滤任何双栈子网中的 ipv4 和 ipv6 流量](https://aws.amazon.com/about-aws/whats-new/2023/01/aws-network-firewall-ipv6-support/)。最重要的是，对于那些想使用这个新功能的人来说，这个特性不需要额外的费用。

* * *

[![Complete guide to the Cloud and Dictionary ](img/93ebf63b88ab7fbd48705a01952ba688.png)](https://get.acloudguru.com/cloud-dictionary-of-pain)

[**获得痛苦的云词典**](https://get.acloudguru.com/cloud-dictionary-of-pain)
说云不一定要努力。我们分析了数以百万计的回复，找出了最容易让人犯错的概念。抓住这个[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)获取一些最痛苦的云术语的简洁定义。

* * *

## Lambda & SQS 的新最大并发特性

同样在这个月，AWS 宣布了一个生活质量更新，这对于无服务器开发者来说是一个令人兴奋的秘密。

向外扩展 Lambda 调用以从 SQS 队列中接收事件一直是一种非常强大的无服务器模式。然而，一些客户遇到了最大 Lambda 并发性的问题，当他们扩展到太多并发调用时，达到了他们的帐户限制。这将导致来自 SQS 队列的事件被发送回队列，或者被丢弃到死信队列。您可以为您的 Lambda 设置最大并发限制，但这并不能解决丢弃消息的问题。

[AWS 现在已经宣布了当接收来自 SQS 的消息时，Lambda 函数](https://aws.amazon.com/blogs/compute/introducing-maximum-concurrency-of-aws-lambda-functions-when-using-amazon-sqs-as-an-event-source/)的每个源的最大并发限制。这意味着您可以为给定的 SQS 队列定义一个并发 lambda 调用的限制，多余的消息将被保留在队列中，直到有能力进行更多的并发 lambda 调用。

这意味着不再需要处理返回的消息或死信队列，并且可以更好地控制你的帐户的 Lambda 并发限制。

## 无服务器应用模型与 CloudFormation Linter 集成

我们在今年年初的预测之一是，AWS 将在 2023 年继续投资于无服务器开发者体验。AWS 已经开始交付，宣布了对无服务器应用程序模型命令行界面的更新，这肯定会使开发人员的生活更容易。

无服务器应用程序模型，简称 SAM，是一个基础设施即代码平台，允许您以简单的 JSON/YAML 格式定义和重用 AWS 架构。[本月，AWS 发布了一款新的 lint 工具，该工具将根据一组基于云信息的规则检查您的 SAM 模板，从而加快开发过程](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/validate-cfn-lint.html)。

现在，无论何时运行`sam validate`命令，您都可以根据这组规则选择 lint 您的模板。这将使 SAM 用户在部署之前更容易验证他们的 SAM 模板，节省用户大量的时间和金钱。

OpenSearch 无服务器现已正式上市

亚马逊 OpenSearch Serverless 现已全面上市。如果您以前没有使用过 OpenSearch，它是一种允许您执行交互式日志分析和实时应用程序监控的服务，您还可以使用它来可视化您的应用程序数据并创建仪表板，以真正了解您的应用程序内部正在发生的事情。它是基于弹性搜索的。

## 在发布之前，使用 Amazon OpenSearch 需要创建一个 OpenSearch 集群，由多个运行 worker 节点和 master 节点的 EC2 实例组成。当设计这样的群集时，您需要了解您的容量需求。

[但是随着这次发布](https://aws.amazon.com/about-aws/whats-new/2023/01/amazon-opensearch-serverless-available/)，现在有了一个无服务器选项，这是一个更简单的开始方式。这意味着您不需要考虑基础架构需求。这对于可变且不可预测的工作负载也非常有用，因为无需服务器，它将自动扩展，甚至允许您运行 Pb 级的工作负载。

但是它最好的一点是，由于是无服务器的，您将只为您正在使用的东西付费，而不是为多个大型 EC2 实例付费。

OpenSearch 配置更改的预演

OpenSearch 的另一个很酷的声明是[它现在允许您在继续应用更改之前对 OpenSearch 集群的任何配置更改执行增强的预演](https://aws.amazon.com/about-aws/whats-new/2023/01/amazon-opensearch-enhanced-dry-run-configuration-changes/)。这适用于由多个 EC2 实例组成的 OpenSearch 集群。

## 因此，您现在可以在应用配置更改之前验证它们，OpenSearch 服务将检查验证错误，它还会让您知道更改是否需要蓝/绿部署。因此，它会告诉您是否需要部署新实例来应用新配置，或者是否可以将配置应用到集群中的现有实例。

这个特性对于我们这些不太喜欢冒险的人来说是非常棒的，当涉及到对 OpenSearch 集群的配置进行更改时，它将帮助我们避免应用将会破坏我们的集群的更改。

Graviton 的移植顾问

[Graviton 的 Porting Advisor 现已上市](https://aws.amazon.com/about-aws/whats-new/2023/01/porting-advisor-graviton/)，Graviton 当然是最新的 AWS 处理器的名称，由 AWS 定制，经过优化，可为基于 AWS 的工作负载提供最佳的价格和性能。

## Graviton 处理器有多种不同的 EC2 实例类型，但是，由于这些处理器使用 Arm64 指令集，这是一种用来告诉处理器做什么的语言，因此开发在 x86 处理器上运行的应用程序有时需要额外的步骤，因为 x86 使用不同的指令集。

AWS 承认对一些人来说，还有其他需要考虑的问题，这很好。他们还向[提供了一个逐步过渡的指南](https://github.com/aws/aws-graviton-getting-started/blob/main/transition-guide.md)来帮助那些计划将现有应用移植到基于 Graviton 的实例的客户。

*从这些 [10 个有趣的动手项目开始构建你的云计算技能，学习 AWS](https://acloudguru.com/blog/engineering/10-fun-hands-on-projects-to-learn-aws) 。*

连续的 IPv6 CIDR 块

* * *

最后， [AWS 宣布亚马逊提供的连续 IPv6 CIDR 块全面上市](https://aws.amazon.com/about-aws/whats-new/2023/01/amazon-provided-contiguous-ipv6-cidrs-blocks/)。

* * *

## 但这实际上意味着什么呢？现在，您可以使用 AWS 帐户中的 IP 地址管理器(或 IPAM)来创建可与您的 VPC 相关联的连续 IPv6 CIDR 块。这允许您为您的 VPC 创建连续的 CIDR 范围，以便您可以实施对您的环境有逻辑意义的 CIDR 范围。

如果你不再需要你的 VPC 并删除了它，你仍然拥有 CIDR 街区，你可以把它重新分配给另一个 VPC。

以前，获得像这样的连续 IPv6 CIDR 范围的唯一方法是使用您自己的产品，所以这次新发布的产品将使寻求使用 IPv6 的客户更加方便。

这是 AWS 一月份最大的头条新闻！

想了解每周 AWS 新闻吗？

查看本周 AWS 的每周新闻综述。加入我们的专家主持人，因为他们涵盖了你需要知道的关于过去一周发展的一切，保持简短、有趣和信息丰富。

## 无论您是刚刚开始您的云之旅，还是您已经了解自己的东西，每个人都有适合自己的东西！

Check out [AWS This Week](https://www.youtube.com/playlist?list=PLI1_CQcV71RmeydXo-5K7DAxLsUX6SVhL) for your weekly news roundup for all things AWS. Join our expert hosts as they cover everything you need to know about the past week’s developments, keeping it short, fun and informative. 

Whether you’re just beginning your cloud journey, or you know your stuff, there’s something for everyone!