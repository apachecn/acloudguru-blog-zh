# AWS re:Invent 2021:周二的 6 大要点

> 原文：<https://acloudguru.com/blog/engineering/aws-reinvent-2021-tuesdays-top-6-takeaways>

要跟上 AWS re:Invent 发布的大量新服务和新技术，感觉就像从消防水管里喝水一样。为了帮助我们以更容易理解的速度满足对 AWS 新闻的渴望，我们求助于云专家开发者传道者 Mattias Andersson 和 CTO 顾问兼 Pluralsight 作者 David Tucker。

这两种动态云一起提供了一个 TL；DW(太长了，没看)新闻导读出 [AWS re:Invent 2021](https://acloudguru.com/blog/tag/reinvent2021) days 1 和 2。请继续阅读他们迄今为止的 6 大要点。(更喜欢完整的事实？点击[这里](https://acloudguru.com/blog/engineering/aws-aims-to-reduce-cloud-barriers-expand-industry-specific-focus)查看所有公告的摘要。)

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

为了清晰、简洁和总体美观，这段对话已经过编辑。任何错误都可能是编辑的失误。(那家伙有什么问题？他只有一份工作！)

**David:** 我想说的第一个消息是听到他们在芯片方面的进步是多么令人惊讶。随之而来的是两件不同的事情。

首先是我们有了新的 Graviton3 芯片，所以我们将会看到它的巨大性能提升。它将使人们能够以更具成本效益的方式运行更多的工作负载。他们甚至谈到了碳足迹的影响，这也是我们最近经常听到谷歌和微软谈论的话题。

另一件大事是 AWS 之前宣布的 Tranium 芯片现在可以使用了。因为我们知道，在机器学习的战斗中，有两个方面:软件和硬件。所以我们看到了这方面的巨大进步。你最喜欢的公告是什么，马蒂亚斯？

Mattias: 这可能不是我最喜欢的公告，但我不得不说[大型机现代化](https://aws.amazon.com/mainframe-modernization/)公告是。。。等等，大卫在给我侧目！这里有一些有趣的价值。让人们有机会减少三分之二的项目时间？每个项目都要快三分之二！你不相信我，大卫？

大卫:我只是好奇。它到底在做什么？

马蒂亚斯:我不知道。

大卫:如果它上面有主机标签，就可以用了？

马蒂亚斯:是的，我想是主机制造商的人。。。我确定这是和他们的合作关系。

大卫:他们有主机贴纸可以贴在你的应用程序上吗？

Mattias :它就像一个贴在前面的“主机内部”的小标签。

大卫:嗯，如果它能让你的项目时间减少三分之二，那就完全值得了。

马蒂亚斯:好的。另一件让你印象深刻的事是什么？

大卫:这几乎是我在这里提到的第一件事的延续，但是，机器学习。围绕 ML 肯定有一股推动力，因为你看到他们在主题演讲中花时间重申了他们帮助人们进行机器学习的所有不同方式。然后，他们推出了一个名为 [SageMaker Canvas](https://aws.amazon.com/blogs/aws/announcing-amazon-sagemaker-canvas-a-visual-no-code-machine-learning-capability-for-business-analysts/) 的新解决方案，它是为那些实际上对数据科学没有任何了解的人设计的，这样他们就可以进入数据并从中获得有价值的见解。这实际上是我们在 [SageMaker 自动驾驶仪](https://aws.amazon.com/sagemaker/autopilot/)上看到的扩展。

马蒂亚斯:你甚至都没有编码。你正在使用拖放来组装机器学习管道。它让这项技术更加贴近人们。这就是需要发生的事情。AWS 在堆栈的所有不同层都有这样做的历史。这只是其中的一个。

大卫:绝对是。如果你去查看一下[AWS 关于这个的博客文章](https://aws.amazon.com/blogs/aws/announcing-amazon-sagemaker-canvas-a-visual-no-code-machine-learning-capability-for-business-analysts/)，它会告诉你它实际上会如何查看数据，并告诉你应该再次使用什么算法，而你不必知道什么算法解决了什么数据问题。

马蒂亚斯:即使是这方面的专家，他们也会花很多时间试图弄清楚这些。但是如果你能有一个真正能帮你解决问题的服务，那就是利用 AWS。这就是我们在这里的原因。

大卫:没错。那么，你还从主题演讲中听到了什么让你兴奋的事情？

Mattias :我总是对无服务器公告感到兴奋。因此，看到现在有了一系列分析工具的无服务器和按需服务，这是非常酷的。特别是，我们有[红移无服务器](https://aws.amazon.com/blogs/aws/introducing-amazon-redshift-serverless-run-analytics-at-any-scale-without-having-to-manage-infrastructure/)、[亚马逊 EMR 无服务器](https://aws.amazon.com/about-aws/whats-new/2021/11/amazon-emr-serverless-preview/)、[亚马逊 MSK 无服务器](https://aws.amazon.com/about-aws/whats-new/2021/11/amazon-msk-serverless-public-preview/)——因此 Kafka 的管理流。我们还有 [Kinesis 数据流点播](https://aws.amazon.com/blogs/aws/amazon-kinesis-data-streams-on-demand-stream-data-at-scale-without-managing-capacity/)。那很酷。

例如，使用 Redshift 无服务器，当您的红移集群(他们仍在幕后为您管理)空闲时，您根本不需要付费。你正在加载数据，当你停下来的时候，你就停止付费。然后，您可以稍后开始查询，并根据您加载和查询的时间再次开始付费。那真是太棒了。

大卫:这绝对让分析变得更容易，尤其是对那些新手来说。

我想强调的另一件事是——因为对我来说——这是整个主题演讲中最意想不到的宣布，即 AWS 现在有一个私有 5G 产品， [AWS 私有 5G](https://aws.amazon.com/private5g/) 。

这样，他们将打包组织在仓库、工厂等地方部署 5G 所需的一切。我真的很想知道客户将来会如何使用 AWS。

对于希望进行大量物联网工作的组织来说，有时有太多的传感器，传统的通信方法并不理想，这对他们来说可能是一项改变游戏规则的服务，它将简化他们进入 5G 的方式。我们必须拭目以待，但我认为这可能会带来一些令人兴奋的事情。

说到这里，请务必保持关注，因为本周会有*所以*更多的公告发布，您可以在这里找到您需要的一切。

 **马蒂亚斯**:你可以在[推特](https://twitter.com/acloudguru)和[脸书](https://www.facebook.com/acloudguru)上关注 ACG，在[上订阅 YouTube 上的云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)来更新 2021 年的发明。你也可以顺便访问我们的 [Discord 社区](https://discord.com/invite/acloudguru)，与 AWS 培训架构师和作者联系，并结识各种其他令人敬畏的阴云密布的人。但最重要的是，保持敬畏，云大师们！