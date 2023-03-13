# Kubernetes 1.24 中最重要的 3 个更新|云专家

> 原文：<https://acloudguru.com/blog/engineering/top-3-updates-in-kubernetes-1-24>

我们今年已经快过半了，感觉库伯内特的新闻还在继续！在本帖中，我们将看看最近发布的 Kubernetes 1.24 中最显著的三个特性——包括 Kubernetes 历史上最大的特性移除。我们还将回顾 2022 年 KubeCon Europe 的亮点，并讨论 Docker 的新收购。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## Kubernetes 1.24 中的三大亮点

这个月围绕 Kubernetes 的最大新闻是 Kubernetes 1.24 的 T2 发布。

这是 2022 年的第一个版本，代号为“Stargazer”——这是因为有一千多家公司和个人为最新版本做出了贡献。神奇！

这个新版本附带了 46 个增强功能。其中 14 个功能升级为稳定版，15 个功能升级为测试版，还有 13 个闪亮的新 alpha 功能。然而，在这个版本中占据头条的肯定是 Dockershim 或 Docker 运行时的移除。

### 1.删除 Docker 运行时

现在我明白了；感觉我们一直在谈论这个*，但这可能是 Kubernetes 历史上最大的功能移除，它有巨大的破坏潜力。*

*但好消息是现在还为时尚早。新版本已经发布，但还没有多少人会使用它。因此，对我来说，中断的可能性仍然存在，并将至少在未来 6-12 个月内继续存在。*

*你可以在这里找到准备指南[的链接。希望这是我们最后一次需要它。](https://kubernetes.io/blog/2022/03/31/ready-for-dockershim-removal/)*

### *2.默认情况下，新的测试版 API*关闭**

*另一件有趣的事情是。默认情况下，新的测试版 API 将**关闭**。现在，这与以前相反，默认情况下他们在上**，这非常有用，但几乎太有用了。人们发现自己上瘾了，却没有完全意识到他们是测试版。***

*因此，从 1.24 开始，新的测试版 API 将被默认关闭，但任何在以前版本中已经测试并启用的 API 都将保持打开状态。所以对于全新的测试版，比如 1.24 中的 15 个增强，如果你想使用它们，你必须手动启用它们。*

*唷！*

### *3.存储容量跟踪和卷扩展现已稳定*

*现在最后一个 1.24 亮点来自我。*

*作为一名前存储人员和一名认为 Kubernetes 中功能丰富的存储对于关键工作负载非常重要的人，我很高兴存储容量跟踪和卷扩展现在成为稳定的功能。*

*Volume expansion(从 1.11 开始就是测试版，非常喜欢)允许您直接编辑现有的 PVC 并指定一个新的更大的尺寸。而且要更大。没办法让它们变小。它需要 CSI 驱动程序和后端存储系统的支持。*

*另一个是容量跟踪。这暴露了容量信息，因此调度程序可以为需要存储的 pod 选择合适的节点。好东西，相信我。*

*非常感谢 James Laverack 和发布团队的其他成员让这个版本上线了！*

*KubeCon 欧洲 2022*

*继疫情之后，我们第二次亲身体验了 KubeCon，这也是我们第一次回到欧洲。*

## *现在，围绕 CNCF 处理口罩政策的方式有一些酝酿中的紧张情绪。如果你注意的话，你肯定能感觉到。但是我认为那里 90%的人都不会注意到。*

*无论如何，这个活动很好，总体感觉是比 6 个月前在洛杉矶有更多的参与者。尽管如此，我不确定这是一个巨大的成功。我不知道。只是感觉有点压抑。*

*这一切都始于常见的零日事件:像 GitOpsCon、云原生安全大会、普罗米修斯日、eBPF 日等小型会议。外加一大堆工作室。很多都卖完了，但不是全部。*

*在那之后，是三天的会议，走廊轨道，简报，摊位，甚至海滩和几个派对。*

*我认为，如果说脚踏实地有什么好处的话，那就是混合和云计算工具和产品的增加。不出所料，安保人员大批出现在那里。也有对 101 初学者内容的需求。感觉每次会议都会有越来越多的 it 和运营人员参加。*

*那就是 KubeCon Europe。回来的感觉真好。*

**免费 Kubernetes 培训**

**查看一月份[ACG](https://acloudguru.com/blog/news/whats-free-at-acg)的免费课程，其中包括我们[为 Kubernetes](https://acloudguru.com/course/designing-applications-for-kubernetes)课程设计申请。只有这个月免费。不需要信用卡，不开玩笑！**

* * *

### *码头工人获得倾斜*

*紧随最近一轮融资之后， [Docker 收购了 Tilt](https://www.docker.com/press-release/docker-acquires-tilt-to-help-fix-the-pains-of-microservices-development-for-kubernetes/) ，这基本上是一个让微服务开发更容易的工具或项目。*

* * *

## *现在，从 40K 英尺的高度来看，这似乎是一个很好的举措，因为 Docker 是为了让开发人员的生活更轻松。然而，我认为宣布这一举措的博客文章有点滑稽。这真的感觉就像他们在说，“是的，这里有很大的协同潜力，”但它缺乏两者如何实际整合的清晰路径。我的意思是，博客最后说得差不多了，“我们要集思广益，找出 Docker 和 Tilt 可以整合的地方。”什么！？*

*GKE 自动驾驶仪上的光点吊舱*

*我真的很有兴趣看到 [Spot Pods 在 GKE 自动驾驶集群上运行](https://cloud.google.com/kubernetes-engine/docs/release-notes)。*

## *它们基本上是 Pods，在 Spot 实例上运行，而且——和大多数 Spot 一样——它们很便宜，但是它们可能会在没有警告的情况下被驱逐。因此，它们并不适合所有工作负载。但在不断完善和成熟的 GKE 生态系统中，它们绝对是一个很酷的功能。*

***[观看:自动化 Kubernetes 安全](https://go.acloudguru.com/automating-kubernetes-security-webinar)** [](https://get.acloudguru.com/aws-cloud-formation-power-user-webinar) 在[这个免费的点播网络研讨会](https://go.acloudguru.com/automating-kubernetes-security-webinar)中，学习如何用 Pod 安全策略来增强您的 K8s 安全。我们将向您展示它们是如何工作的，以及在一个真实的 Kubernetes 集群中实现它们的样子。*

*跟上 K8s*

* * *

*本月 [Kubernetes 本月](https://acloudguru.com/videos/kubernetes-this-month)到此为止。注意安全，我们下个月再见——同一时间，同一地点。*

* * *

## **想要了解 Kubernetes 的所有信息？在推特[上关注奈杰尔](https://twitter.com/nigelpoulton)或者在这里关注他[。在 YouTube 上订阅一位云计算专家](https://nigelpoulton.com/),获取定期更新、分析和各种精彩内容。你也可以在[脸书](https://www.facebook.com/acloudguru)上喜欢 ACG，在[推特](https://twitter.com/acloudguru)上关注我们，或者在[不和谐](http://discord.gg/pluralsight)上加入对话！**

*That’s it for this month’s edition of [Kubernetes this month](https://acloudguru.com/videos/kubernetes-this-month). Stay safe, and I’ll see you all again next month — same Kube time, same Kube place.*

**Want to keep up with all things Kubernetes? Follow Nigel on [Twitter](https://twitter.com/nigelpoulton) or keep up with him [here](https://nigelpoulton.com/). [Subscribe to A Cloud Guru](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1) on YouTube for regular updates, analysis, and assorted awesomeness. You can also like ACG on [Facebook](https://www.facebook.com/acloudguru), follow us on [Twitter](https://twitter.com/acloudguru), or join the conversation on [Discord](http://discord.gg/pluralsight)!**