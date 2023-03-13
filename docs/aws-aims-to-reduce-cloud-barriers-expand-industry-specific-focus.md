# AWS 旨在减少云障碍，扩大行业特定的关注点|云专家

> 原文：<https://acloudguru.com/blog/engineering/aws-aims-to-reduce-cloud-barriers-expand-industry-specific-focus>

AWS 首席执行官亚当·塞利普斯基(Adam Selipsky)发表了两个多小时的主题演讲，讲述了 AWS 的[历史，以及他对未来扩展云的可用性和可访问性的愿景，从而开启了第一个全天的AWS re:Invent 2021](https://acloudguru.com/blog/engineering/what-is-amazon-web-services-aws)。。。和佛罗伦萨·南丁格尔的历史。

这听起来有点奇怪，但它实际上以好的“吸引每个人”的基调的方式工作。

以下是今天早上从拉斯维加斯宣布的所有重大新闻的概要，包括 Graviton3、AWS SageMaker Canvas、私有 5G、无服务器和按需分析、AWS Lake Formation 的新安全功能等等。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## 1.15 年来，AWS 的状态一直很好

随着 AWS re:Invent 庆祝其作为几乎是“云”同义词的服务 10 周年和亚马逊网络服务(AWS) 15 周年，Selipsky 以回顾过去和讨论该公司的发展方向作为开场白。

当天的新闻包括重点关注为各种行业专门打造的服务，以及让几乎没有或根本没有技术经验的人比以往更容易获得复杂的技术。

“云是一个重新想象一切的机会，”塞利普斯基说。"它提供了一条通往真正转变的道路."。

历史部分提醒每个人，云怀疑论者最近仍在否定云技术，从认为它只是一种时尚，只是企业组织的东西，到一些有用但肯定不是任务关键型工作负载的东西。

“你已经证明他们错了，”塞利普斯基说。

今天，S3 存储了超过 100 万亿个对象，AWS 提供了超过 200 个全功能服务和 81 个 AZ 和 25 个地区(肯定会有更多)。

塞利普斯基说:“尽管感觉像是大规模采用，但我们才刚刚开始”。“没有哪个行业没有被触及，也没有哪个行业不能被彻底颠覆。今天在座的每个人都是这场运动的一部分。”

这一天是塞利普斯基继亚马逊首席执行官安迪·雅西(Andy Jassy)之后第一次发表主题演讲。

## 2.亚马逊发布 **Graviton3 处理器**支持 C7g 实例

一开始，亚马逊就宣布了其下一代基于 ARM 的 Graivton3 处理器，性能提高了 25%，功耗降低了 60%，从而改善了碳足迹。

AWS 还声称，这些芯片将提供 2 倍的浮点和加密性能，以及 3 倍的机器学习工作负载性能。

由 Gravinton3 处理器支持的 C7g 实例目前在[预览版](https://aws.amazon.com/blogs/aws/join-the-preview-amazon-ec2-c7g-instances-powered-by-new-aws-graviton3-processors/)中可用。

Honeycomb 的首席开发人员 Liz Fong-Jones 曾在之前的[中谈到过](https://go.acloudguru.com/state-of-the-cloud-webinar?)Honeycomb 大量使用 Graviton2 来帮助降低成本和环境足迹，同时增加计算量。她在 Twitter 上谈论了她看到的结果:“我们已经尝试过了，对于我们的工作负载来说，它甚至好于 25%。”

## 3.深度学习培训的亚马逊 EC2 Trn1 实例正在预览中

AWS [宣布](https://aws.amazon.com/about-aws/whats-new/2021/11/amazon-ec2-trn1-instances/)基于 AWS Trainium 的亚马逊 EC2 Trn1 实例正在预览中。

这些实例针对在云中训练深度学习模型进行了优化，为模型训练提供了 AWS 声称的最佳性价比，并提供了 800 Gbps 的网络带宽。

这些对于像语言处理或图像识别这样的用例是非常理想的。获取[产品页面上的所有信息。](https://aws.amazon.com/ec2/instance-types/trn1/)

## 4.AWS 大型机现代化有助于迁移本地大型机工作负载

Selipsky 说，客户正试图摆脱大型机，并“通过迁移降低 70%或更多的成本。”一些人选择[提升和移位](https://acloudguru.com/blog/business/what-is-lift-and-shift-cloud-migration)，而另一些人决定重构。

AWS 认为这两者都不像客户希望的那么容易。解决办法？AWS 大型机现代化。

Selipsky 表示，该平台将帮助组织在 AWS 上迁移、现代化和运行大型机工作负载，将迁移时间缩短三分之二，分析和评估迁移准备情况，并帮助他们进行自动化重构或平台重建。

更多信息[点击这里](https://aws.amazon.com/mainframe-modernization)。

## 5.AWS Private 5G 让您拥有私人蜂窝网络

厌倦了糟糕的手机服务？也许是时候创建自己的 5G 网络了。奇怪的是，现在这是一种选择，AWS 私有 5G。

AWS Private 5G 允许企业设置和管理自己的专用网络，声称设置可以在几天内完成，而不是几个月。

为什么你可能想要一个专用的 5G 网络(除了让你害怕 5G 的邻居搬走)？

AWS 声称，专用 5G 网络可以帮助组织处理企业网络限制，方法是增强现有网络，为越来越多的设备提供高带宽、远程覆盖，同时保持专用网络的安全性和控制力。

AWS 提供您需要的东西(硬件、软件和 SIM 卡)，您的员工插入 AWS 提供的 SIM 卡，网络就会自动配置。Selipsky 提供了一个大型园区、仓库或工厂作为潜在的使用案例。客户只为他们请求的容量和吞吐量付费。

在此获取全部详情[或](https://aws.amazon.com/private5g/)[请求预览访问](https://pages.awscloud.com/Private5GPreview.html)。

## 6.SageMaker 画布:假人的 ML 模型？

人们想要访问很酷的机器学习系统。但这意味着依赖一个可能有更好的事情要做的数据科学团队。进入:亚马逊 SageMaker Canvas，现在是 GA。

SageMaker Canvas 旨在帮助业务用户和分析师使用可视化、无代码、点击式界面生成 ML 预测。创建模型后，用户可以发布结果并与其他人协作。

更多信息[点击这里](https://aws.amazon.com/blogs/aws/announcing-amazon-sagemaker-canvas-a-visual-no-code-machine-learning-capability-for-business-analysts/)。

## 7.新的无服务器和按需分析选项

AWS 宣布，预览版中的红移、EMR、MSK 和 Kinesis 现已提供无服务器和按需选项。

无需配置或扩展集群或服务器。只要启动它们，服务就会在你忙的时候扩大规模，在你不忙的时候缩小规模。你只有在使用服务时才付费。

ACG 的 Stephen Sennett 对 T2 的 Kinesis 数据流按需的潜力感到特别兴奋:“Kinesis 数据流具有按需模式很有趣，可能会为那些不愿意以‘X 大小’提交的人打开许多用例——类似于按需 DynamoDB 如何向非常不频繁的用例或高度不可预测的工作负载打开东西。”

在围绕 Kinesis 数据流点播的[公告](https://aws.amazon.com/blogs/aws/amazon-kinesis-data-streams-on-demand-stream-data-at-scale-without-managing-capacity/)中，Marcia Villalba 解释了一些潜在的用例。

“按需模式非常适合具有未知或可变工作负载的客户，或者只是不想处理容量管理的客户。按需模式最适合具有均匀分区键分布的工作负载。例如，您运行一款手机游戏，该游戏的流量在一周或一天中是可变的，因为客户大多在晚上或周末玩游戏。或者，你运营一个直播节目的流媒体平台，你会发现根据你拥有的嘉宾，需求会突然增加。”

您可以通过以下链接获得更多信息:

## 8.AWS Lake Formation 引入了 spalshy 新的安全功能

AWS 正在升级针对 [AWS Lake Formation](https://aws.amazon.com/blogs/aws/aws-lake-formation-general-availability-of-cell-level-security-and-governed-tables-with-automatic-compaction/) 的安全特性，增加了行和单元级别的安全和受管表，这些都是今天正式发布的。

受管表是一种新型的 S3 表，它使数据的接收和管理变得更加容易，支持允许用户并发地插入和删除数据的 ACID 事务。行级和单元级安全性确保数据只向特定行和列的授权用户公开。这适用于受治理的和传统的 S3 表。

正如 Selipsky 所说，这“将正确的数据交给正确的人，并且只交给正确的人。”

## 9.亚马逊 S3 冰川即时检索

AWS 围绕存储服务和功能发布了一小堆更新，包括 [Amazon FSx for OpenZFS](https://aws.amazon.com/blogs/aws/new-amazon-fsx-for-openzfs/) 和[Amazon EBS snapshot s Archive](https://aws.amazon.com/blogs/aws/new-amazon-ebs-snapshots-archive/)存储层。

但是最突出的是亚马逊 S3 冰川即时检索存储类的[公告](https://aws.amazon.com/about-aws/whats-new/2021/11/amazon-s3-glacier-instant-retrieval-storage-class/)，它看起来非常酷。(抱歉……)

AWS 声称，它将为很少访问的数据提供最低成本的存储(比 S3 标准-不频繁访问低 68%)，同时提供毫秒级检索。

## 10.AWS 揭示面向工业和汽车垂直行业的物联网服务

在今天的重要主题演讲即将结束时，Selipsky 宣布 [AWS IoT TwinMaker](https://aws.amazon.com/about-aws/whats-new/2021/11/aws-iot-twinmaker-build-digital-twins/) 和 [AWS IoT Fleetwise](https://aws.amazon.com/about-aws/whats-new/2021/11/aws-iot-fleetwise-transferring-vehicle-data-cloud/) 正在预览中。

AWS IoT TwinMaker 允许开发人员制作现实世界系统的数字双胞胎，如工厂、工业设备或产品线。

AWS IoT Fleetwise 旨在让汽车制造商更容易几乎实时地收集和分析数百万辆汽车产生的大量数据。这些数据可以用于从远程诊断到训练自动驾驶或辅助驾驶系统的机器学习模型的所有事情。

## 跟上 AWS 的一切:发明 2021

在推特[上关注 ACG](https://twitter.com/acloudguru)和[脸书](https://www.facebook.com/acloudguru)，以及[在 YouTube 上订阅一位云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)来更新:发明 2021！查看 [ACG 和 Pluralsight re:Invent 内容中心](https://www.pluralsight.com/reinvent-2021)获取新闻和 AWS 资源。加入我们令人敬畏的 [Discord 社区](https://discord.com/invite/acloudguru)，与 AWS 培训架构师和其他志同道合的阴云密布的人一起接触数字。