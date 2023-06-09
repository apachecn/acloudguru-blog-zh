# 抽象即服务的兴起

> 原文：<https://acloudguru.com/blog/engineering/the-rise-of-abstraction-as-a-service>

2020 年是相当疯狂的一年。随着世界已经转变为一种完全远程的生活方式(至少目前如此)，云基础设施已经成为我们日常运营方式中越来越重要的一部分。你每天用来工作的大多数服务都运行在某个地方的某个服务器上。你在家里与之交谈的许多设备都在做同样的事情。

如果你想要一个小的微观世界，看看云现在在哪里，我们可以回顾一下过去几周的 AWS re:Invent——在那里，十几个云产品的字母汤问世了。它们中的每一个都有其独特的用例，但它们都符合云的发展方向这一总主题:一个适用于你能想象到的每一种服务的工具。

这也不仅仅是亚马逊的事情。您可能会将其称为抽象即服务，这是另一个即服务术语。这使我们走上了 IBM Cloud 副总裁兼 IBM Fellow Jason McGee 所描述的“一切即服务”模式的道路。接下来的十年，甚至更久，将会让在互联网上部署应用的过程尽可能的无缝。

从现在到这个十年结束，将会发生很多事情，我们很期待看到接下来事情的发展。此外，还有许多其他移动部分——围绕安全性的理念变化、实际芯片和技术架构的创新等等。

但这一切都带我们走上了同一条道路——更快地生产出更好的产品，出错的机会更少。

一切即服务

云最初是一种笨重的硬件，虽然有时难以管理，但它为未来提供了令人印象深刻的一瞥:完全摆脱控制应用程序主干的需要。回想起来，这些东西对消费者来说并不友好。考虑到现在的成本效率，你可能会说它也很贵。

在过去的十年里，让你的应用程序出门变得越来越容易——也许是如此渐进以至于很难注意到。当我们到达 2030 年时，我们可能会回顾这十年，并指出容器是完全消除服务器管理的转折点之一。

“集装箱是这一旅程的半步，”麦基说。“更接近 app，也是更好的版本。我认为十年后，我们会继续这一进程，向以应用程序为中心的方向发展，隐藏很多复杂性。”

回到过去几周的字母汤:我们看到了针对如此多特定服务的如此多产品的公告，以至于可能很难确定云提供商的最终目标，甚至超越亚马逊。但是这种几十种服务的杂耍行为本身可能就是最终目标。每个行业都将有一项服务来支持他们获得一个应用程序，并尽可能廉价高效地运行。简而言之，就是一路向下的小众服务。

“随着我们远离基础设施，想象[一切即服务的未来]变得更加容易，”McGee 说。“你有一个 edge 视频设备，可以让你分析流式摄像机——仔细想想，这是一项非常小众的服务。我想在我的办公楼里做视频分析；这里有一个我可以安装的特殊盒子。这就是我们前进的方向。”

这不仅仅是你用来管理服务的软件和网络控制台。

## (抽象)盒子里是什么？

过去十年的另一个元趋势是机器学习的兴起，为你今天使用的几乎每一项服务提供动力。与此同时，公司和风险投资公司已经投入了数十亿美元来创新驱动这些设备的东西:这些设备中的实际硅，无论它们是在边缘还是在数据中心。

云也为所有这些处理能力的创新提供了一个令人兴奋的试验场。公司可以在需要处理复杂过程的边缘设备中试验新型硬件，而不是马上出现在你的手机或笔记本电脑中(尽管苹果可能刚刚采取了这一举措)。同样，您甚至不必管理这些设备。

“我认为云可能是他们首先接受审查和暴露的地方。由于基础设施的管理性质，我们可以更容易地在环境中引入专门的硬件，”McGee 说。“这比在大盘中容易得多。无论是 FPGA、新处理器、人工智能优化芯片，所有这些东西都更容易首先进入公共云，并将其作为服务公开。我们甚至在量子上也做了同样的事情。我们把其中一些放在云上，这样人们就可以在不购买和运行量子系统的情况下实验构建量子，而这是你做不到的。”

硬件本身也可能在某一点上被抽象。你也可以认为它是一个无服务器的模型，但是在处理 4K 视频的工厂里有数百台摄像机在运行。随着硬件变得更容易迭代，特别是在核心处理层，这是一个相同的原则:只关注你的应用程序，真的。

“你必须考虑如何部署终端模型，以及如何使用这些模型，”McGee 说。“这是云边缘版本的‘即服务’模式的主要驱动力。你拥有人工智能、框架和模型的完美融合，带来了自己部署的技能要求。没有多少人能够大规模部署并自己操作它。但是，作为一种服务，有人为你运行这种服务是很有价值的。”

## 保护开发人员免于抽象(和他们自己)

大规模安全漏洞经常成为新闻。但是，对于国家行为者的每一个重大违规行为，你可能还会看到另一种违规行为:有人无意中向公众公开了一些数据，一个有进取心的开发人员发现了这些数据。在最好的情况下，公司会得到一个提醒。在最坏的情况下，他们可能永远也不会发现这一点——而坏人继续从中获利。

这通常可以归结为一系列简单的错误。他们可能配置了错误的 IAM 权限。他们可能只是把一个 S3 桶向公众开放。他们看错了 YAML，或者在第二台显示器上观看篮球比赛时无意中输入了一个错误。或者任何其他数量的看似简单的因素。

因此，尽管管理适当的安全性通常是云提供商最优先考虑的事情之一(如果不是最优先考虑的话),但还有另一个挑战。假设你抽象出*所有的东西*，让用户只关注他们的应用。在这种情况下，你可能会引入另一个失败点:有人太专注于应用程序，以至于他们没有考虑他们的配置。

“这是一个我们花费大量时间的领域，”McGee 说。“服务交付试图保证安全性，因为有专家为您处理安全性问题。你自己不一定要成为专家。很多这样的错误来自于人们错误的配置。我们试图直接解决配置、控制和合规性方面的问题。”

这可能说起来容易做起来难，特别是当我们到达一个点，可能会有数百种服务，几乎每一个可能的利基市场。但 McGee 表示，主动确保这些开发者的配置正确，就像保护他们免受政府支持的黑客攻击一样重要。

## 向 2030 年进军

重要的是，我们要记住 2020 年全面发生的一些巨大创新。在不到一年的时间里研制出新冠肺炎疫苗是一项巨大的科学成就，并将继续影响我们的研究几十年。正如艾萨克·牛顿爵士所说，“如果说我看得更远，那是因为我站在巨人的肩膀上。”

但是我们可以花一点时间来欣赏不断涌现的新工具和技术，它们继续抽象出获得应用程序的所有挑战——也许是脸书或谷歌的规模。消除这一挑战不仅对你的底线有利:它能加快创新，迫使每个人反过来创新。这对每个人来说都是最好的结果。

当然，这是假设每个人都加入了云。但 McGee 对此持乐观态度。

“我认为从现在起十年的渗透率可能会非常高——也许是 80%的范围，”他说。“今天，有些人可能会说是 20%，而其他人可能会说是 4%。这取决于你如何定义“云”我们正在将我们所认为的云从集中式公共数据中心扩展到更加分布式的云。我们有边缘计算，这些核心云数据中心的计算，以及更多可用的选项。如果这是真的，那么将会有更多的应用程序可以从中获益。"