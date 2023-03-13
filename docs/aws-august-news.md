# 八月新闻综述:AWS 有什么新功能？|云专家

> 原文：<https://acloudguru.com/blog/engineering/aws-august-news>

你好，云大师！想知道 AWS 这个月发生了什么变化，但还没有时间查看标题？我们已经写了一篇文章，提供了你需要知道的所有信息。

## 亚马逊海王星全球数据库

这个月，随着亚马逊海王星现在支持全球数据库，行星已经排成一行。

亚马逊的 managed graph 数据库服务已经支持在同一地区跨区域读取副本。虽然这对于本地化中断来说很好，但是跨区域弹性对于云架构师来说是一个越来越明显的话题。使用此功能，您可以在其他区域创建次级集群。

点击这里阅读亚马逊关于使用该功能的便捷指南[，以及你需要考虑的事项。](https://docs.aws.amazon.com/neptune/latest/userguide/neptune-global-database.html)

## CloudWatch 自定义指标提升

是否使用 CloudWatch 自定义指标？本月， [AWS 提高了向 CloudWatch 发送指标的频率上限](https://aws.amazon.com/about-aws/whats-new/2022/08/amazon-cloudwatch-metrics-increases-throughput/)，将吞吐量提高了 150 倍！

现在，您可以在一次调用中发送 50 倍的指标，默认调用速率提高了三倍。他们还将单个指标中可以包含的维度数量增加了三倍，所以如果您一直保持跟踪，那么单个 API 调用中的数据量是原来的 450 倍！

这将允许用户更加灵活地批量定制度量，并最终减少 API 调用:节省带宽，最重要的是节省资金。

## AWS 无服务器代码片段集合现已推出

你喜欢所有无服务器的东西吗？截至本月，无服务器土地网站现在[包括代码片段](https://serverlessland.com/snippets)！

每个代码片段都是由 AWS 开发者拥护者或社区中受信任的成员提供的。此处没有添加到 [r/badcode](https://www.reddit.com/r/badcode/) 中。使用它很容易:您只需通过 AWS 服务或编程语言过滤掉示例，然后将代码复制到您的编辑器中。

## AWS Lambda 转向分层定价

对于没有服务器的人群来说，还有一些更好的消息！如果你是一个使用 Lambda 做大量繁重工作的组织，从这个月开始，你将会节省更多的钱。

AWS Lambda 已转向分层定价模式，根据您的计算持续时间提供高达 20%的定价折扣。

这已经在除中国以外的所有地区实施。要了解更多信息，请查看这篇文章。

## 计算优化器适用于多个客户

这个月，AWS 组织和 AWS Compute Optimizer 走到了一起。您现在可以使用[一个帐户从组织中的所有帐户收集计算优化器报告](https://aws.amazon.com/about-aws/whats-new/2022/08/optimize-resources-organization-aws-compute-optimizer-designated-account/)。

使用这一功能，您只需检查一个位置，就可以确定所有方法来正确调整您的服务器、存储桶和功能，这样您每个月都可以节省更多的资金，并提高运营效率。

## AWS 让你可以打造自己的专用 5G 网络

如果你有拥有自己的个人移动网络的冲动，好消息是:AWS 本月公开了 AWS 私人 5G。

Private 5G 面向希望在设施内本地建立自己的私有安全移动网络的企业。这可以用来将手机以及其他物联网设备连接到一个安全、低延迟的网络，具有极其强大的安全性和访问控制。

通常情况下，这是非常复杂的设置，但 AWS 已经简化了它。你所要做的就是注册 AWS 控制台，请求你想要连接的设备数量，他们会给你邮寄一个迷你插件蜂窝无线电单元和连接它所需的 SIM 卡。

## 想了解最新的 AWS 新闻吗？

本周请务必遵守[AWS](https://www.youtube.com/playlist?list=PLI1_CQcV71RmeydXo-5K7DAxLsUX6SVhL)！每周，我们的 ACG 技术讲师都会分享亚马逊网络服务领域的最新发展，以及他们有价值的见解，这样你就可以知道它对你有什么影响。