# 自动气象站云形成和 IOT 更新 2021 

> 原文：<https://acloudguru.com/blog/engineering/aws-makes-cloudformation-do-overs-easier-cloudwatch-adds-custom-widgets>

AWS 有什么新功能？在本帖中，我们将报道最近的 AWS 新闻，包括 CloudFormation 模板调试变得更加容易，AWS 的物联网套件推出了一些方便的新功能，以及我们现在如何将自己的小部件添加到 CloudWatch 仪表盘中。

想了解更多？请继续阅读！

## **云的形成变得更加容易**

调试[云构造](https://acloudguru.com/course/mastering-aws-cloudformation)模板总是让我想起希腊神话中的一个故事，一个人试图把巨石推上山，结果却让它滚了下来。即使我的模板的前 20 步成功完成，第 21 步的失败也会使一切归零。

好吧，谢天谢地，我们现在有一个选项来禁用自动回滚，并保持所有那些成功创建的资源不变，同时我们找出步骤 21 出错的地方。

我们甚至可以改变我们的模板和参数，然后从故障点再次尝试，这是一个非常受欢迎的特性。

现在，所有云计算专家都可以冷嘲热讽地向初级云工程师抱怨，在我的*时代，模板在失败时不得不一路回滚。你喜欢它是因为它本来就是这样！*

* * *

[**Watch:成为 AWS CloudFormation 高级用户**](https://get.acloudguru.com/aws-cloud-formation-power-user-webinar) Watch [这款免费的点播网站](https://get.acloudguru.com/aws-cloud-formation-power-user-webinar) r 深入了解鲜为人知的功能，您可以使用它成为 CloudFormation 高级用户。

* * *

## CloudWatch 添加自定义小部件

由于我们现在可以添加自己定制的小部件，仪表盘变得更加灵活。

我们可以从 AWS 之外的数据源添加我们自己的图形或图表，我们甚至可以创建按钮和其他启动事物的控件。

例如，如果我们的仪表盘显示有问题，我们可以提供操作手册或自动补救流程的链接。我们甚至可以创建一个按钮，询问我们是否已经关闭并再次打开它。

为了让我们开始，AWS 提供了一些示例定制小部件，包括一个 RSS 阅读器和一个带有 EC2 重启按钮的小部件。(你可能认为我只是开个玩笑，把它关掉，然后再打开。)

## **AWS 物联网获得新功能**

AWS 物联网用户本周欢迎该套件的一些新功能。[green grass](https://acloudguru.com/blog/engineering/aws-greengrass-pro-tips)2.4 版引入了为设备提供声明证书的功能，并允许我们为设备上的每个进程设置内存和 CPU 限制。

物联网设备管理现在有一个名为“车队指标”的功能，让我们可以将聚合的设备信息发送到 CloudWatch 以监控趋势。

此外，IoT Core 现在支持 MQTT 主题的保留消息。在处理只能间歇性连接的物联网设备时，这是一个很小但很重要的功能。保留的消息现在会挂在主题“就绪”上，等待设备再次连接。如果设备没有这个功能，要么会完全错过消息，要么当设备在线时我们不得不撤销。

* * *

*对升级或开始云架构之旅感兴趣吗？云专家的 [AWS 架构师](https://acloudguru.com/learning-paths/aws-architect)学习路径提供适合初学者和高级专家的定制课程！*

* * *

说到物联网，请关注即将发布的 ACG 项目，该项目让我可以深入了解 AWS 物联网 Greengrass v2。我将向您展示如何构建一个远程任务的离网图像和数据收集站。为了这个，我甚至拿出了旧烙铁。

好了，我的朋友们，这就是我本周所有的 AWS 新闻。保持安全，互相照顾，并保持令人敬畏，云大师。

*想跟上万物云？[在 YouTube 上订阅云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每周亚马逊新闻和 AWS 服务公告。您也可以在[脸书](https://www.facebook.com/acloudguru)上喜欢我们，在 [Twitter](https://twitter.com/acloudguru) 上关注我们，或者在 [Discord](http://discord.gg/acloudguru) 上加入对话！*

* * *

## 在云中开启更好的职业生涯

学得更快。动作快点。[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。