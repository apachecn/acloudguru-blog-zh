# 借助新的 AWS 预算控制台 UI |云专家，更好地监控预算

> 原文：<https://acloudguru.com/blog/engineering/monitor-budgets-better-with-new-aws-budgets-console-ui>

欢迎来到您的亚马逊网络服务头条新闻策划摘要。在本周的 AWS 新闻中，我们为您发布了一些重大消息。AWS 配置新的资源类型，C6gn 实例类型在新的地区可用，Amazon Aurora PostgreSQL 现在支持零停机更新。此外，对 AWS 预算控制台的改进使查看预算比以往任何时候都更容易。让我们开始吧！

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## AWS 配置的 15 种新资源类型

在将资源部署到 AWS 之后，您可能认为需要全天候监视您的资源，以确保您部署的配置不会改变。但是，在您构建一个全天候监视您的资源配置的系统之前，请先休息一下！AWS 已经有了可以帮你做到这一点的服务。AWS Config 持续监视资源配置，甚至可以根据您定义的规则对配置更改做出响应。

已经有几十个资源可以用 AWS Config 来监控，现在，[又多了 15 个](https://aws.amazon.com/about-aws/whats-new/2022/06/aws-config-15-new-resource-types/)。可以用 AWS Config 监控的新资源包括 SageMaker 模型、弹性负载平衡器监听器；AWS 工作区；和 Route53 解析程序规则。

因此，如果您想持续关注各种资源配置，可以使用 AWS Config。

## 在四个新地区访问 EC2 C6gn 实例

AWS 继续扩展基于 Arm 的实例的可用性，本周[为 C6gn 实例类型](https://aws.amazon.com/about-aws/whats-new/2022/06/amazon-ec2-c6gn-instances-available-additional-regions/)添加了更多区域。C6g 实例由基于 Arm 的 Graviton-2 处理器提供支持。C6gn 实例类型提供高达每秒 100 千兆位的网络能力以及弹性结构适配器支持。

这些非常适合高性能计算、网络设备、实时视频通信和数据分析。现在，C6gn 实例类型在欧洲的巴黎和米兰地区、亚太地区的首尔地区和中东地区的巴林地区可用。随着这一地区的扩张，C6gn 实例现在[在全球 19 个地区](https://aws.amazon.com/ec2/instance-types/c6g/)可用。

* * *

## 准备好观看云学习了吗？

![](img/bfb7b9915b29cd217c34556dfd956289.png)

CloudCheckr 使用 ACG 在短短 90 天内提升了他们在 AWS 上的所有销售人员。[看看他们是怎么做到的](https://go.acloudguru.com/cloudcheckr-case-study?cpn=7013u000000VDht)。

* * *

## Amazon Aurora PostgreSQL 零停机补丁

说到数据库引擎，使用 Amazon Aurora 就像获得一个数据库——包括一个数据库管理员。作为 Amazon 关系数据库服务的一部分，Aurora 提供了低延迟读取副本、自动故障转移等等。现在，亚马逊 Aurora 正在让更新变得更加无缝和简单。

[Amazon Aurora，PostgreSQL edition，现在支持零停机补丁](https://aws.amazon.com/about-aws/whats-new/2022/06/amazon-aurora-postgresql-compatible-edition-supports-zero-downtime-patching/)，允许您在不丢失客户端连接的情况下更新数据库版本或应用补丁。当数据库引擎重新启动时，所有客户端连接都将保留，因此您可以保持数据库最新，不会丢失任何一个节拍。因此，下一次您需要更新数据库版本时，停机时间将是一个少担心的事情。

## AWS 预算控制台的界面更新

你有没有在 AWS 中启动了一项服务却忘记关闭的经历？也许唯一提醒你停止服务的是你月底收到的账单？这里不做评判，因为我自己也做过，这是我开始使用 AWS 预算时需要的经验。

AWS 预算让您可以直接从控制台跟踪您的实际*和*估计使用量。[最近对 AWS 预算的改进现在可以让您轻松高效地管理多个预算](https://aws.amazon.com/about-aws/whats-new/2022/06/aws-budgets-ui-improvements/)。现在，您可以使用拆分视图以列表形式查看所有预算，同时查看选定预算的详细信息。如果您需要快速查看多个预算，页面内导航允许您移动到下一个或上一个预算，而不必刷新页面。

不要认为你局限于跟踪 AWS 预算的成本！您还可以跟踪资源使用情况，并在任何预算超出实际或估计阈值时得到通知。

* * *

*想跟上 AWS 的一切？* [*在 YouTube 上订阅一位云大师*](https://www.youtube.com/c/AcloudGuru) *的每周亚马逊新闻和 AWS 公告。你也可以像 ACG 上的*[](https://www.facebook.com/acloudguru)**一样，关注我们上的* [*推特*](https://twitter.com/acloudguru) *，或者加入* [*不和谐*](https://discord.com/invite/pluralsight) *的对话！**