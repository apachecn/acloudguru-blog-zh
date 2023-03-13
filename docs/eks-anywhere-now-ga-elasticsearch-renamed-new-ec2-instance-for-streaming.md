# EKS Anywhere 现已正式上市，Elasticsearch 更名，面向流媒体的新 EC2 实例|云专家

> 原文：<https://acloudguru.com/blog/engineering/eks-anywhere-now-ga-elasticsearch-renamed-new-ec2-instance-for-streaming>

你好，云大师们！本周 AWS 怎么了？EKS 扩大了它的覆盖范围，live streamers 有了一些强大的新 EC2 实例，以前被称为 Elasticsearch 的服务有了一个新名字。另外，我们即将举办几场现场活动，您一定不想错过。

我是斯科特·普莱彻，这里有另一批 AWS 新闻，你可能会用到。我们开始吧！

EKS 任何地方是 GA

## *弹性 Kubernetes 服务现已全面普及*

#### 早在 re:Invent 2020 上宣布，[Elastic Kubernetes Service Anywhere](https://aws.amazon.com/blogs/aws/amazon-eks-anywhere-now-generally-available-to-create-and-manage-kubernetes-clusters-on-premises/)旨在让组织在自己的数据中心舒适安全地运行 EKS。

从架构上来说，容器化是对冲云提供商风险的一个很好的方法，因为所有主要的提供商都对容器有很好的支持。

EKS Anywhere 的价值主张是，它提供了一种一致的方式来管理本地和基于 AWS 的 EKS 集群。如果您生活在工具和实用程序的 k8s 生态系统中，您会知道一致性有时很少。

还没准备好和 EKS 一起深入任何地方吗？您可以试用 EKS 连接器的新公共预览版，它可以将任何 Kubernetes 集群连接到 EKS 控制台。

**[保护您的 AWS 环境](https://get.acloudguru.com/securing-aws-environment-webinar)** 在[这个免费的点播网络研讨会](https://get.acloudguru.com/securing-aws-environment-webinar)中，了解如何从零开始保护复杂的 AWS 环境，并学习如何正确[审计和保护 AWS 帐户](https://acloudguru.com/blog/engineering/how-to-audit-and-secure-an-aws-account)。

* * *

[![Ransomware and Reducing Your Blast Radius on AWS](img/82cdea1597d3af97d42e03398b92931f.png)](https://get.acloudguru.com/securing-aws-environment-webinar)

亚马逊弹性搜索现在是亚马逊开放搜索

* * *

## “我现在将你命名为开放搜索！”

#### 听着，听着。亚马逊弹性搜索服务现在将被称为[亚马逊开放搜索服务](https://aws.amazon.com/blogs/aws/amazon-elasticsearch-service-is-now-amazon-opensearch-service-and-supports-opensearch-10/)。

要理解这一更名的原因和方式，人们必须回到今年早些时候，Elasticsearch 和 Kibana 背后的公司 Elastic 宣布，他们将从 Apache 许可证版本 2 转向更具限制性的许可证——这一举动引起了开源社区的愤怒，并使 Elastic 和 AWS 相互指责对方是罪魁祸首。

作为回应，AWS 在 2021 年 4 月宣布了 OpenSearch，这是 Elasticsearch 和 Kibana 的开源分支，AWS 仍然保留在 Apache 版本 2 许可下。

此外，fork 允许 AWS 继续添加功能和增强，它们最近发布了 OpenSearch 1.0。他们决定也是时候改名了。

AWS 并没有完全退出 Elasticsearch，因为客户仍然可以运行 7.10 版本的产品。不过，除此之外，客户还要做出决定。

用于实时多流的新亚马逊 EC2 VT1 实例

## 过去几年，随着个人和企业试图找出如何在现场活动不被允许或不切实际的情况下继续下去，在线流媒体迎来了一个全新的世界。直播曾经是新鲜事物，现在已经成为一项大生意。曾经需要卫星上行链路和制作人员的工作现在可以用一台很好的笔记本电脑、OBS 和互联网连接来完成。

虽然直播的门槛可能很低，但观众——尤其是那些付费观看的观众——希望获得非常高的质量。

最近，AWS 推出了一个专门为直播构建的新 EC2 实例，名为 [VT1 家族。](http://Resource/link:%20https://aws.amazon.com/blogs/aws/new-amazon-ec2-vt1-instances-for-live-multi-stream-video-transcoding/)它们的独特之处在于，它们包含 Xilinx 的专用转码芯片，在媒体流方面比基于 GPU 的实例更高效。与 GPU 实例相比，VT1 系列以高达 60%的低成本提供了更多的流能力。

AWS 甚至计划在 AWS 前哨站上提供这些 VT1 实例，允许广播公司在本地进行代码转换。

Kotlin 的 AWS SDK 获得 alpha 版本

## 作为对所有 Kotlin 开发人员的一个快速提醒:AWS 悄悄发布了一个针对 Kotlin 的 alpha 版本的 [AWS SDK。它还不能投入生产，但可能值得一看。](https://aws.amazon.com/blogs/developer/aws-sdk-for-kotlin-alpha-release/)

即将在 ACG 举行的现场活动

## 说到现场活动，我们正在准备另一场 ACG 现场考试演练——这次包括 [AWS 认证系统运行管理员助理](https://acloudguru.com/course/aws-certified-sysops-administrator-associate)考试。

Faye Ellis 和我将分发新考试的资料，并浏览一些样题。此外，我们将向您展示这些新的考试实验室如何工作以及如何准备。也就是 9 月 28 日星期二，东部时间上午 11 点，太平洋时间上午 8 点，英国夏令时下午 4 点，并将在 [Twitch](https://www.twitch.tv/acloudguruofficial) 和 [YouTube](https://youtu.be/Tm1wBx0paAs) 上同步播出。

本周，你可以加入 Mattias Andersson、Lars Klint 和我……再次……在 [ACG Discord 服务器](https://discord.com/invite/acloudguru)上享受认证办公时间。是时候去拜访一下，打个招呼，问一些关于云认证的问题了。(或者给我们讲个好笑话——我们也喜欢。)发生在 9 月 22 日东部时间下午 6 点，太平洋时间下午 3 点。

*跟上万物云。[在 YouTube 上订阅云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每周亚马逊新闻和 AWS 服务公告。你也可以在[脸书](https://www.facebook.com/acloudguru)上喜欢 ACG，在 [Twitter](https://twitter.com/acloudguru) 上关注我们，或者在 [Discord](http://discord.gg/acloudguru) 上加入对话！*

加速您在云计算领域的职业发展

## 学得更快。动作快点。[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

Learn faster. Move faster. [Get started with ACG](https://acloudguru.com/pricing) and transform your career with courses and real hands-on labs in AWS, Microsoft Azure, Google Cloud, and beyond.