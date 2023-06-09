# Brazeal:您的组织如何预测您的 CI/CD 渠道

> 原文：<https://acloudguru.com/blog/engineering/cd-pipeline>

我和你打个赌。

告诉我你的开发和运营团队是如何合作的，我会告诉你你的 [CI/CD 管道](https://acloudguru.com/course/implementing-a-full-ci-cd-pipeline)是什么样子的。

那是因为 CI/CD 是[康威定律](https://en.wikipedia.org/wiki/Conway%27s_law)最纯粹的表述。你的 CI/CD 管道会像你的工程组织一样破碎混乱。这就是你如何得到这样的“管道”:

[![](img/9e4da481a8b224499e6f7cf0b625a5ba.png)](https://faasandfurious.com/93)

好吧，也许这有点夸张(虽然，以我在大企业的经验，不多)。但是另一方面也是真的:一旦你的沟通正确，你就可以开始看到你一直希望的 CI/CD 的好处。

不服气？让我给你看一些图案。

**冷战**

请记住，CI/CD 管道的存在是为了通过自动化手动步骤和增加对发布的信心，平滑和加速代码从开发到运营和 QA 到生产的流动。

这与许多大型组织仍然采用的瀑布式发布方法正好相反，在瀑布式发布方法中，开发人员将代码“越过墙”扔给运营部门。开发人员无法接触到产品，而运营人员也不太了解代码是如何工作的。

让我们称之为“冷战”模式:

![](img/de524e50edf0862d086419a61cdde9fe.png)

一个冷战时期的组织竟然会考虑实施 CI/CD，这有点令人惊讶。但是他们和其他人一样，很可能会抛出这个流行词。当新的自动化出现故障时，除了增加人工劳动外，这还会导致额外的管理开销。基本上，只是旧的瀑布流程加上了[额外的步骤](https://faasandfurious.com/97)。

你不能在你的发布过程中摆脱这堵墙而不摆脱你组织中的这堵墙。

**秋葵汤**

嗯，秋葵汤。虽然 ops 倾向于在冷战中抑制开发速度，但是 gumbo 组织是开发人员活动的一个狂热的沼泽。你可以在很多成长中的初创公司看到这一点。工程团队变得太大，无法维持一个简单的发布过程，随之而来的是混乱。

如果没有明确的安全指南或针对开发人员的云操作培训，就很容易停止生产或暴露带有轻率配置更新的 S3 桶。如果说冷战是不连续的融合，这更像是持续的解体。

![](img/b3b0d75565dbc1e242e6e28935ff0bcf.png)

聪明人在秋葵汤里工作。一些伟大的 CI/CD 管道可能漂浮在表面之下。但是没有办法在全公司范围内发现和分享这些知识。

谢天谢地，秋葵阶段是如此不稳定，没有人可能会误认为是一件好事，所以该组织很快凝结成…

**斑点**

这一团在比冷战或秋葵汤更高的成熟状态下融合。

有人意识到“我们需要标准！指导方针！一个统治他们所有人的工具——这将停止这种疯狂！”

因此，他们建立了一个由现有最佳基础设施工程师组成的中央 DevOps 团队。中央团队创建了每个人都应该使用的管道基础设施。这可能就像一个共享的 Jenkins 实例一样简单。它可能像与一系列动态代码管道模板相关联的 AWS 帐户自动售货机一样复杂。

![](img/4bd26834d3d2c7e32355631c3acc3a61.png)

但是其他团队真的会*使用*中央管道吗？有的会！他们会发现他们的用例非常适合通用解决方案，并被吸收到 blob 中。然而，其他团队会发现他们的应用程序需要不同的方法。他们将次优地使用中央解决方案，或者更糟，忽略它，并建立他们自己的秘密 CI/CD 解决方案——在 blob 本身的阴影下[隐藏它](https://faasandfurious.com/99)。

**雨伞**

blob 希望你认为这是成功的唯一途径。这就是 blob 的力量，为什么这么多团队无限期地陷入其中。

但是斑点是错误的。

成熟的组织不仅在 CI/CD 领域，而且在普遍采用云的情况下，最终会让单个团队以自己的方式取得成功，同时仍然为他们提供所需的保护和培训，以满足组织的卓越云标准。

这意味着要有一个中央架构委员会和一个安全团队来创建清晰的指导——我最近与一位 ACG 客户交谈过，他称之为“云不可协商”这意味着将您的云专家嵌入到需要实际支持的产品团队中，以便从云新手过渡到专家。是的，这意味着通过培训和认证，确保每个人都说同样的云语言。

你可以称之为伞状模式。每个产品团队都是不同的:云流畅的保护伞覆盖了他们所有人。

![](img/7a0f0410d2869308e0e8c1b9e32561e8.png)

现在我要跟注:我描述过你组织吗？还是你看到了其他模式？在 Twitter 上联系我，让我们继续对话。

* * *

***ACG 商业版帮助您组织中的每个人都说云语言，因此您可以打破壁垒，更快地创造价值。***