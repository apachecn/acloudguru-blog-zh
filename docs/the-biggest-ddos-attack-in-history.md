# 史上最大的 DDoS 攻击？

> 原文：<https://acloudguru.com/blog/engineering/the-biggest-ddos-attack-in-history>

微软发布了一些关于他们如何减轻分布式拒绝服务(DDoS)攻击的统计数据。他们不仅描述了他们如何保护 Azure 服务，还描述了有多少攻击。这让我震惊。。。

完整的故事(以及本周 Azure news 的其他一些有趣的花絮)请继续阅读！

* * *

**通往更好职业的钥匙**

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## 微软缓解了 3.47 Tbps 的攻击

我们都知道，互联网服务经常遭受攻击，服务越大，目标越大。我只是不知道有这么多。

在 2021 年 8 月，平均每天有 1955 次攻击，Azure 阻止或减轻了这些攻击——最高的是 8 月 10 日的 4296 次。单日 4000 多！

2021 年下半年，总共发生了 359713 起攻击事件。神圣的蝙蝠侠！这是一次攻击。。。而现在。。。而现在。

去年 10 月，[我告诉过你们](https://acloudguru.com/blog/engineering/azure-reveals-new-az-305-and-details-biggest-ddos-attack-ever)一次每秒 2.4 太比特的巨大 DDoS 攻击。也就是说，每秒钟有 300Gb 的垃圾数据被扔向一项服务。自那以后，Azure 已经缓解了三次较大的攻击，最大的一次是在 11 月，在 DDoS-o-meter 上测量到 3.47 Tbps。

这可能是 DDoS 和互联网历史上最大的一次，Azure 也能够击败那次。

虽然这些数字令人印象深刻(坦率地说很难理解)，但我认为这里的主要信息是 DDoS 攻击不会消失，也不会变得更小。因为它们很容易安装，而且价格便宜(是的，你可以买一个 DDoS 即服务)，我们只会看到更多更大的。然而，利用像 Azure 这样的云平台意味着你很可能永远不用担心这个问题。这是我喜欢云的原因之一。

在此获取所有详情[。](https://azure.microsoft.com/en-us/blog/azure-ddos-protection-2021-q3-and-q4-ddos-attack-trends/)

## Azure 开源日是 2 月 15 日

你听说过 Azure 开源日吗？这个以 Linux 为主的活动是全在线的，在 2 月 15 日可以免费参加。微软列出了你应该参加的 [7 个理由。看看吧！](https://azure.microsoft.com/en-au/blog/7-reasons-to-attend-azure-open-source-day/)

## 微软和美国宇航局将量子计算带入太空

这是过去一周的另一个最受欢迎的故事，主要是因为标题中有“量子”和“空间”。(我不找借口。)

“美国宇航局喷气推进实验室(JPL)已经转向 Azure Quantum，以探索与探索我们太阳系及其他地方的航天器更有效地沟通的方法，”微软在一篇博客文章中说。

JPL 正在 Azure 上使用量子启发的优化算法，以提高他们在火星漫游车和詹姆斯·韦伯太空望远镜等任务中使用的保真度。Azure 上的量子服务是对 JPL 深空网络的补充，这是一个在加利福尼亚州，西班牙和澳大利亚的大型射电望远镜网络。

在这个具体的例子中，微软描述了他们如何将计划优化所需的时间从 2 小时减少到 16 分钟。

当你处理发送到火星的信息时，优化火星车、望远镜或你控制的任何东西的每次更新或时间表的处理时间，几乎十分之一的时间减少是巨大的。

对于那些仍然怀疑太空探索和技术价值的人来说，请记住时间安排问题并不是 NASA 和太空所独有的。这些问题存在于大多数行业，他们也将受益于这一进步。爱死了。

## 微软为支持 Azure Arc 的服务器推出登陆区加速器

Azure Arc 允许您在 Azure 中包含您的内部和“其他云”虚拟机、SQL 服务器和 Kubernetes 集群。有了 Arc，你可以控制和监视它们，就像在 Azure 上一样。它是 Azure 上促进高效混合基础设施的关键工具之一。

Azure 登录区是多订阅 Azure 环境的输出，它考虑了规模、安全治理、网络和身份。换句话说，这是一种以安全和可伸缩的方式充分利用 Azure 的推荐方法。将此与云采用框架结合在一起，您将获得一个着陆区加速器，它现在可以将 Arc 考虑在内。

正如微软所说，“着陆区加速器提供最佳实践、指导和自动化参考实施，以便客户能够快速轻松地开始部署。”

“快速”和“容易”这两个部分应该有所保留，因为混合环境并不总是一帆风顺的。至少着陆区加速器将提供一个初始的方法和前进的方向。

欲了解更多信息，请点击[此处](https://azure.microsoft.com/en-au/blog/microsoft-launches-landing-zone-accelerator-for-azure-arcenabled-servers/)。

## Azure 您在云中的成功

如果你想让 2022 年成为你开始云计算生涯的一年，或者开始掌握在科技行业获得一些[高薪职位所需的技能，那么就去看看](https://acloudguru.com/blog/engineering/top-paying-cloud-certifications-and-jobs) [ACG 的免费计划](https://acloudguru.com/pricing)。它给你提供了[免费课程和测验](https://acloudguru.com/blog/news/whats-free-at-acg)，以及学习路径和原创系列内容。

整个二月,[微软 Azure 云采用框架](https://acloudguru.com/course/introduction-to-the-microsoft-cloud-adoption-framework-for-azure)的完整课程介绍是免费的——以及一系列其他内容。你不需要信用卡来注册。这里[开始](https://acloudguru.com/pricing)！

好了，这就是这周的全部内容。直到下一次，我会在云中见到你。继续牛逼吧，云大师们！

*想跟上万物云？在推特[上关注 ACG](https://twitter.com/acloudguru)和[脸书](https://www.facebook.com/acloudguru)，[在 YouTube 上订阅一位云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)，并在 [Discord](http://discord.gg/acloudguru) 上加入对话。*