# 新的 AWS 控制台主页有什么问题？|云专家

> 原文：<https://acloudguru.com/blog/engineering/whats-up-with-the-new-aws-console-home-page>

本周 AWS 怎么了？首先，AWS 展示了对管理控制台主页的重大改进。此外，EC2 上 Microsoft Windows Server 实例的启动速度刚刚得到优化。AWS 发布了新的 EC2 实例类型。

我们开始吧！

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## AWS 管理控制台主页获得更新

听叶的！听叶的！ [AWS 管理控制台](https://console.aws.amazon.com/console/home)主页已更新！

AWS 表示，重新设计的目标是每天给你带来更多相关的内容，并根据用户的反馈进行更新。这些更新包括一些很酷的新功能。虽然功能上与之前的版本相似，但视觉上却有很大的不同。

这里有一点预期的预览。(剧透:是 widgets！)

*   现在，当您登录时，有八个默认的小部件，包括三个供云新手使用的小部件(欢迎使用 AWS，构建解决方案，探索 AWS)。

*   其他 5 个小部件包括:最近访问，AWS 健康，成本和使用，可信的顾问，和收藏夹。

*   这些小部件也是可定制的。

就我个人而言，我不喜欢这些小部件缺乏可折叠性。但是我喜欢新增的颜色，以及当你登录的时候，你现在可以看到一切，知道一切。我迫不及待地想看到他们如何随着时间的推移发展这种新观点。

你可以检查新的控制台，为自己选择。或者访问 AWS 博客了解更多关于新功能的信息。

## 更快启动 Windows Server EC2 实例

如果你像我一样，你真的会为了更快的速度放弃一切。现在，EC2 上 Microsoft Windows Server 实例的更快启动速度已经成为现实！

在 EC2 上，启动 Windows Server 实例的速度可以提高 65%。

其美妙之处在于，一旦 AMI 被标记为更快的启动时间，它将自动从该 AMI 更快地启动任何实例。

为更快启动而标记 ami 不收取服务费，客户只需支付用于准备实例以更快启动的底层资源。

对于任何需要更快系统恢复或运行繁重峰值工作负载的人来说，这都是一个好消息。更快的启动时间意味着更顺畅的恢复和工作负载。配置启动速度更快的 ami 轻而易举。使用控制台、API、SDK 或 AWS CLI 启动或停止快速启动。

完整的细节在这里[。](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/windows-ami-version-history.html#win-ami-config-fast-launch)

## 新 Hpc6a EC2 实例类型

您准备好迎接新的 EC2 实例类型了吗？不管准备好了没有，它来了！

AWS[宣布了](https://aws.amazon.com/about-aws/whats-new/2022/01/amazon-ec2-hpc6a-instances/)新的计算优化 Hpc6a 实例。

惠普什么？高性能计算中的 HPC。这将包括计算流体动力学、油藏建模、天气模拟或有限元分析。

AWS 表示，Hpc6a 实例的性价比比同等的计算优化实例高出 65%。这些新实例由第三代 AMD EPYC 处理器的 96 个核心提供支持，全核心睿频为 3.6 GHz，内存为 384 GB。它们基于 AWS Nitro 系统构建，提供默认启用的 100 Gbps 弹性光纤适配器网络，用于高吞吐量节点间通信，以帮助大规模运行您的工作负载。

这些实例目前在 US-East-2(俄亥俄州)和 GovCloud(美国西部)地区可用。

## 关注并提升您的云计算事业

期待在 2022 年开始您的云计算生涯？如果你今年下定决心要在云计算领域找到一份更好的职业，宇宙会送你一份礼物来帮助你！

加入 ACG 培训建筑师 Lars Klint、Scott Pletcher 和 Mattias Andersson，观看 1 月 18 日美国东部时间下午 3:30 的 YouTube 直播。(那就是今天的*。。。假设你今天正在读这篇文章。但是如果你将来读到这段话，你也可以听到录音，我想你有点像*有*要做的。也就是说。。。你来自未来？哇哦。🤯)*

*在这一环节中，他们将讨论如何确定你的职业目标、提高认证技能，并回答你的所有问题。看看吧！*

## *跟上 AWS 的所有事情*

*想要跟上 AWS 的所有事情？在推特[上关注 ACG](https://twitter.com/acloudguru)和[脸书](https://www.facebook.com/acloudguru)，[在 YouTube 上订阅云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每周 AWS 更新，并在 [Discord](http://discord.gg/acloudguru) 上加入对话。*

*想了解更多关于云和 AWS 的信息吗？查看我们每月更新的[免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)的轮换阵容。(不需要信用卡！)*