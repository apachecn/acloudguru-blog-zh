# 9 月新闻综述:AWS 有什么新功能？

> 原文：<https://acloudguru.com/blog/engineering/september-aws-news>

你好，云大师！想知道 AWS 这个月发生了什么变化，但还没有时间查看标题？我们已经写了一篇文章，提供了你需要知道的所有信息。

## VPC 流量日志现在可以传送到 Kinesis 消防软管

流量日志允许您捕获和记录进出 VPC 的网络流量信息。在这个月之前，你可以向 CloudWatch 或 S3 提交流量日志。然而，你现在可以[将它们交付给 Kinesis 消防软管](https://aws.amazon.com/about-aws/whats-new/2022/09/amazon-vpc-flow-logs-delivered-amazon-kinesis-firehose/)。

如果你不熟悉 Firehose，这是一种让你消费实时流数据的服务，然后将其交付给各种不同的目的地进行处理或存储。例子包括其他 AWS 服务，如 RedShift 或 OpenSearch。您甚至可以将您的流日志交付给第三方提供商(如 DataDog、Splunk、MongoDB 和 Sumo Logic)的 HTTP 端点。

这一声明意味着您现在可以将您的流量日志数据交付到一系列新的目的地进行处理、分析和存储。这使您能够从流量日志数据中获得更多的洞察力。

## AWS 为 Kubernetes 添加了支持 Lambda、RDS、阶跃函数等的控制器

在 AWS 世界的一边，你有 Lambda、RDS、阶跃函数和 KMS。另一方面，你有 EKS 的 Kubernetes。直到这个月，如果您想在两个世界中工作，您必须使用单独的工具来部署和管理每一个。谢天谢地，再也不会了！

AWS 已经发布了对 Kubernetes 计划(ACK)的 AWS 控制器下的大量新服务的支持。在这个版本中，您现在可以使用 Kubernetes 来管理 RDS、Lambda、Step 函数、Prometheus 的 Amazon 托管服务及其密钥管理服务(KMS)。

这对你意味着什么？嗯，这意味着您可以使用典型的 Kubernetes yaml 配置文件使用您定义的定义，使用 [kubectl 在 AWS 服务](https://aws.amazon.com/blogs/compute/deploying-aws-lambda-functions-using-aws-controllers-for-kubernetes-ack/)中部署资源。如果您大部分时间都在 Kubernetes 中工作，那么您现在就有能力与比以前更多的 AWS 服务进行交互。

## 新的 AWS 解决方案架构师助理考试现已正式推出

上个月，新的 AWS 解决方案架构师助理考试(SAA-C03)启动，之前的版本(SAA-C03)被弃用。如果你想知道新旧考试之间的区别，我们已经写了一个[方便的指南，详细解释了这些区别](https://acloudguru.com/blog/engineering/new-aws-saa-c03-exam)。

## 亚马逊红移宣布系统日志将保持一贯的持久性

Amazon Redshift 是 Amazon 对数据仓库的回答，它为您的数据提供集群，可以暂停和恢复以实现成本最优。红移客户使用系统表和查看日志或 STL 和 SVL。这些日志视图提供了对查询执行的深入了解，以便根据需要进行性能和审计。它们还提供七天的系统日志数据，这些数据在集群暂停时会暂停，在恢复集群时需要一段时间才能恢复联机。

好了，这里有一个大消息:这些日志现在在集群的暂停和恢复期间都是持久的。这意味着没有日志丢失，没有数据缺口，更顺利的审计和更好的性能帐户！

## DynamoDB 现在支持每个事务 100 个动作

DynamoDB 继续增加新的超能力。以前 DynamoDB 中的事务被限制在 25 个不同的动作。他们现在已经通过增加到 100 个动作打破了之前的限制。

这种变化意味着您可以将所有逻辑上分组的修改组合到一个事务中，而不必将它们分成一系列不同的事务。我们有可能在未来看到这个数字攀升到新的高度。

## Amazon ECS 宣布为扩展提供更快的 CAS 体验

当使用集群自动扩展时，Amazon ECS 过去只能在每个扩展步骤中一次减少 5%的容量。现在[这个限制是 50%](https://aws.amazon.com/about-aws/whats-new/2022/09/amazon-ecs-faster-cluster-auto-scaling-experience-scale-in-events/) ，这意味着更少的放大步骤和更快的放大过程。这仍然保持了那些尖峰流量模式的容量可用性。

## AWS IAM Identity Center 添加了 API 来管理用户和组

9 月，AWS 回答了 IAM 身份中心服务(以前称为 AWS SSO)用户的最大投诉之一。如果您使用 IAM Identity Center 服务管理多个 AWS 帐户的访问权限，则可以使用 API 来创建、删除、读取和更新用户、组及其权限。这些 API 通常是可用的，您可以在使用该服务的任何地方试用它们。

## AWS 阶跃函数增加了 14 个新的固有函数

[引用 AWS](https://aws.amazon.com/about-aws/whats-new/2022/08/aws-step-functions-14-new-intrinsic-features-process-data-workflows/) 的话，“现在，Step 函数使得在工作流中执行数组操作、JSON 对象操作和数学函数等数据处理任务变得更加容易，而无需调用下游服务或添加任务状态。”

您需要编写的代码越少越好！

## Karpenter 现在可以进行工作负载整合

如果您以前没有使用过 Karpenter，它是一款开源的 Kubernetes cluster-autoscaler，可以通过[根据集群工作负载](https://aws.amazon.com/about-aws/whats-new/2022/08/workload-consolidation-karpenter/)扩展集群来帮助提高应用可用性和运营开销。

您可以将 Karpenter 与 EKS 或任何其他兼容的 Kubernetes 集群一起使用。因此，如果你以任何形式使用 Kubernetes，那么你需要了解这一点！

随着 Kubernetes 集群中工作负载的增加，可能有必要启动新的 EC2 实例来处理增加的工作负载。随着时间的推移，这些实例可能会变得利用不足；例如，如果工作负载缩减，或者从集群中删除。

这就是 AWS 九月份的所有头条新闻！

## 想每周了解 AWS 新闻吗？

[AWS 本周](https://www.youtube.com/playlist?list=PLI1_CQcV71RmeydXo-5K7DAxLsUX6SVhL)是 AWS 的每周新闻综述。加入我们的专家主持人，因为他们涵盖了你需要知道的关于过去一周发展的一切，保持简短、有趣和信息丰富。

无论您是刚刚开始您的云之旅，还是您已经了解自己的东西，每个人都有适合自己的东西！