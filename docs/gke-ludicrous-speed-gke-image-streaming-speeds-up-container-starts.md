# GKE 图像流加速容器启动

> 原文：<https://acloudguru.com/blog/engineering/gke-ludicrous-speed-gke-image-streaming-speeds-up-container-starts>

Google Kubernetes 引擎现在可以比以前更快地启动容器了！

谷歌称这项功能为“T0”图像流，但它与你乘坐内胎顺流而下时拍摄照片没有任何关系。更确切地说，这完全是关于容器映像如何从工件注册中心及时地传输到 GKE，因为需要它的各种数据。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

对于一个很小的容器图像来说，这真的没有什么区别。少量的数据被一次发送出去，GKE 像往常一样运行容器。但是随着容器的增长(这在真实的世界中肯定会发生),这个特性开始发挥作用。

正如谷歌所写:

> “图像流的工作方式是使用复杂的网络挂载将容器数据层挂载到 containerd 中，并通过网络、内存和磁盘上的多个缓存层为其提供支持。一旦我们准备好映像流装载，您的容器将在几秒钟内从映像提取状态转换到运行状态(无论容器大小如何);这有效地将应用程序引导与容器映像中所需数据的数据传输并行化。因此，您可以期待看到更快的容器启动时间和更快的自动伸缩。

谁不想这样呢，对吧？尤其是因为他们让我们放心，“就你的容器化应用而言，图像流是完全透明的。”

现在，唯一的问题是——如果你密切关注的话，你可能已经发现了——GKE 图像流依赖于谷歌的工件注册产品。如果您仍在使用他们较旧的容器注册中心，那么这可能是您进行迁移所需的推动力。

这个月谷歌还有什么新消息？请观看以下视频，了解 Prometheus 的托管服务、云日志记录上下文跟踪、现已正式发布的一系列服务(包括云域和顶点管道——一种新的无服务器 MLOps 解决方案),以及 Redis 更新的 Memorystore！

*通过在* [*上追随一位云宗师【推特】*](https://twitter.com/acloudguru)*[*【脸书】*](https://www.facebook.com/acloudguru)*[*上订阅一位云宗师*](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1) *进行每周更新，并在* [*上加入对话*](http://discord.gg/acloudguru) *。您也可以查看我们本期的* [*免费课程*](https://acloudguru.com/blog/news/whats-free-at-acg) *！***