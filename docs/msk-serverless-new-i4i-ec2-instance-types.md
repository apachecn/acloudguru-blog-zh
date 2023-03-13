# MSK 无服务器和新 EC2 I4i 实例类型|云专家

> 原文：<https://acloudguru.com/blog/engineering/msk-serverless-new-i4i-ec2-instance-types>

哇，这周我们有很多要从 [AWS 了解的吗！现在，在 GA 中，我们已经为 Kafka 无服务器管理流。我们来看看 Amazon Rekognition 的流视频事件特性和新的 I4i 实例类型。我们得到了一个更新的 EKS 控制台来帮助 Kubernetes 集群管理。此外，我邻居的猫甚至会出现在本周的公告中。我们开始吧！](https://acloud.guru/series/aws-this-week/view/508?&ajs_aid=a9b08306-f702-48dc-925f-a7754381eb09)

* * *

准备好提升你的 AWS 技能了吗？无论你是刚刚起步还是经验丰富的云专家，云专家的边做边学方法都将帮助你掌握云技术并在职业生涯中取得进步。

* * *

## 面向 Kafka Serverless 的托管流现已正式推出

回到 re:Invent 2021，AWS 宣布了一套四个围绕数据和分析的预览服务产品，这些产品将在无服务器或按需配置中提供。这包括 Redshift 无服务器、EMR 无服务器和 Kinesis 按需数据流。除了这三家之外，他们还宣布了针对 Kafka Serverless 的托管流媒体服务，这一服务现在已经由 T2 升级为普遍可用。

该产品的工作方式与 Kafka 的普通托管流产品类似，它使您能够在完全托管的服务中安全地接收和传输大量数据。主要区别在于，您不再需要管理集群的扩展。这使得将 MSK 无服务器集成到您的云应用程序中变得更加容易。

## Amazon Rekognition 流媒体视频活动现已全面推出

因此，每天凌晨 3 点左右，我都会收到手机通知，说地下室的监控摄像头检测到了动静。我会担心吗？不，只是我邻居的猫晚上出去散步。等等，这跟 AWS 新闻有什么关系？

嗯，这只是一种实时视频警报，你可以通过 AWS 的计算机视觉服务 Rekognition 的新功能为自己建立一种实时视频警报，它被称为[流媒体视频事件](https://aws.amazon.com/rekognition/connected-home/)。好消息是，它也刚刚过渡到普遍可用。

这项功能建立在现有的 Rekognition 服务和 Kinesis 视频流之上。它自带机器学习模型，可以检测人、包裹和宠物。

我相信你可以想到比跟踪邻居的猫更好的事情来做，但如果你喜欢跟踪猫，借助云的力量，这变得容易多了。

## EC2 的新 I4i 实例

我们有了一个新的 EC2 实例类型[！新的 I4i 实例是为需要最大化存储 I/O 的工作负载而设计的。这些实例基于 Ice Lake Xeon 处理器，根据 AWS，它们提供了“比 I3 实例高出 30%的计算性价比”，同时还提供了持续的内存加密。](https://aws.amazon.com/about-aws/whats-new/2022/04/amazon-ec2-i4i-instances/)

发布时只支持三个地区，所以请务必阅读 AWS 新闻博客了解所有细节，并了解如何在今天测试这些内容。

* * *

*从这些 [10 个有趣的动手项目开始构建你的云计算技能，学习 AWS](https://acloudguru.com/blog/engineering/10-fun-hands-on-projects-to-learn-aws) 。*

* * *

## 更新了 EKS 控制台以改进集群管理

最后，在 AWS 新闻中，我要向那些利用 EKS 处理 Kubernetes 工作负载的人宣布一个好消息。AWS 精心制作了一个[控制台更新](https://aws.amazon.com/blogs/containers/introducing-kubernetes-resource-view-in-amazon-eks-console/)，现在可以查看集群上所有的 Kubernetes API 资源类型。对于你们中的一些人来说，这可能意味着你不必利用那么多的第三方工具来管理你的 EKS 集群。

现在，您将能够深入了解服务资源、配置和存储资源、策略资源，甚至授权资源。如果不需要所有这些信息，可以过滤列表，只显示您感兴趣的资源类型。

### 关注 AWS 的所有新闻

在 YouTube 上订阅一位云专家的每周 AWS 新闻(以及其他云提供商的新闻)。你也可以在[脸书](https://www.facebook.com/acloudguru)上喜欢我们，在[推特](https://twitter.com/acloudguru)上关注我们，或者在[不和谐](http://discord.gg/acloudguru)上加入对话！