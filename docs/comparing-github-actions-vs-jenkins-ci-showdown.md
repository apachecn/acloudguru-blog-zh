# 比较 GitHub 行动与 Jenkins: CI 摊牌

> 原文：<https://acloudguru.com/blog/engineering/comparing-github-actions-vs-jenkins-ci-showdown>

GitHub Actions 和 Jenkins 哪个更好？看情况！在本帖中，我们比较和对比了 Jenkins 和 GitHub 的操作和聊天用例，这样你就能感觉到哪种 CI 工具最适合你的需求。

CI/CD 已经从科技巨头的时髦词汇变成了许多软件开发公司的主要产品。但是，就像决定迁移到云(或者决定让你蹒跚学步的孩子给你穿衣服)一样，决定采用 CI/CD 意味着你需要做出许多后续决定。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

为了迁移到云，您需要选择—至少—一个云提供商。(对于为你挑选衣服的蹒跚学步的孩子，你需要问自己一些艰难的问题:你是如何走到今天这一步的。)当您决定采用 CI/CD 时，您将需要选择一个工具，而且有很多这样的工具，看起来每年都在增加。

## GitHub 行动 vs Jenkins

因此，让我们比较和对比 CI 工具领域的两个强国:Cloudbees 的 Jenkins，该领域的开拓者之一，以及 GitHub Actions，由那些将社交媒体的令人上瘾的快感引入版本控制的人带给您的。

我们将从四个方面进行比较:开发者体验、安全性、操作复杂性和成本。我们不会挑选一个赢家(抱歉)，因为最终，最适合的取决于具体情况。但是我们*将*强调优势，并将它们与具体的用例联系起来，这样你就可以知道什么对你最有意义。

### **开发者体验**

首先，我们有开发经验。“什么是开发者体验？“你可能会问。

简单地说，开发者体验是 UX，但是对于开发者来说。你的团队对使用这个工具有什么看法？好学吗？错误信息是否清晰？有社区支持吗？

詹金斯已经存在 10 多年了。它拥有数量惊人的各种工具和框架的社区插件。几乎任何你能想到需要做的事情，都有一个插件。

所有这些插件的缺点是，有时试图找到对你有用的东西会感觉像用弯刀在丛林中穿行。此外，Jenkinsfiles 是用 groovy 编写的，如果你对它感到满意的话——groovy。但是我已经看到许多新的开发人员在为它而奋斗——特别是如果他们不经常使用 Java 的话。

另一方面，GitHub Actions 没有多年的迭代和强大的社区支持档案。然而，用户创建的社区动作可以支持广泛的用例。

Community Actions 方法的缺点是，它将开源解决方案的使用限制在作业中运行的步骤，而不直接支持围绕安全性、成本或分析的其他潜在增值产品。GitHub 动作工作流是用 [YAML](https://acloudguru.com/course/yaml-essentials) 编写的，这在如今的 DevOps 工具中似乎更常见，对于新手来说也更容易掌握。

因此，如果说詹金斯有时可以是一片郁郁葱葱的丛林，那么 GitHub 的行动就像一个有围墙的花园。

### **安全**

Jenkins 和 GitHub 操作的安全考虑有很多重叠。您带入环境的每个开源解决方案都需要经过独立审查。

GitHub Actions 有一些额外的注意事项。GitHub 有两种截然不同的风格:GitHub Enterprise 和 GitHub.com。

*   GitHub Enterprise 是一个在您自己的环境中运行的服务器，与您运行 Jenkins 服务器的方式类似。

*   **GitHub.com**是更知名的 SaaS 产品。有了 GitHub.com，你不需要担心更新和修补服务器，但是任何 GitHub 用户都可以创建一个公共存储库的 pull 请求。这可能允许恶意用户针对您的存储库运行他们的代码。这可能会耗费资金、影响环境并泄露机密。这是公共存储库的权衡——当向社区征求反馈时，你得到了好的，需要减少坏的。

* * *

[**观察:后 COVID DevOps:加速未来**](https://get.acloudguru.com/post-covid-devops-accelerating-future-webinar) COVID 如何影响——甚至加速——工程团队的 DevOps 最佳实践？[观看与 DevOps 领导者的免费点播](https://get.acloudguru.com/post-covid-devops-accelerating-future-webinar)小组讨论，我们将探索后 COVID 时代的 DevOps。

* * *

### 操作复杂性

运营复杂性是指该工具将使用运营/基础架构团队的多少带宽。

对于这个类别，Jenkins 和 GitHub Enterprise 处于同一条船上:两者都需要管理托管工具的服务器(补丁、更新、备份等)，以及管理将实际执行作业的运行程序或节点。

另一方面，GitHub.com 的运营成本非常低。由于平台和运行者都由 GitHub 管理，所以不需要管理服务器。如果你愿意，你可以在 GitHub.com 上使用你自己的定制跑鞋，有一些令人信服的使用案例，但这不是必需的。

### **成本**

Jenkins 和 GitHub 的行动都可以从很低的成本开始，但是如果你没有一个合适的策略，成本会迅速上升。

当然，成本不仅仅是你每个月从供应商那里得到的账单。如果一个工具需要 20 个资源小时来维护，那就是成本。如果新员工在开始编码之前需要花一周时间学习如何使用这个工具，那就是一个成本。如果一个过时的开源插件导致了数据泄露，那就是代价。

因此，当最小化成本时，通常最好采取比本节所涵盖的更广泛的视角。

Jenkins 是完全开源的，因此您可以将其安装在服务器上并开始使用。您可以添加工作节点、开源插件和第三方集成，并获得一个强大的 CI/CD 解决方案，而无需支付超过运行一切的服务器的成本。然而，Cloudbees 确实提供了一些具有潜在价值的增强功能的企业选项。

另一方面，Github.com 不提供开源选项，它根据任务运行的分钟数收费。GitHub 免费账户持有人每月获得免费分钟的预算，这有利于学习，或支持一两个个人项目，但一旦预算耗尽，成本会迅速增加。您可以使用自定义运行器来降低成本，同样，您只需支付底层服务器的成本，但这会增加您的操作复杂性。

## 哪种 CI 工具适合您？

在竞争情报工具的战争中，没有失败者。(所以希望这意味着我们都是赢家？)

GitHub Actions 和 Jenkins 都可以为您的项目添加许多 CI 优点，但它们以有意义的不同方式来做。选择最适合您的工具将使添加 CI 的过程变得更加容易，并且您将更快地看到附加价值。

要了解更多关于 GitHub Actions 的信息，请查看新的 [GitHub Actions 深度课程](https://acloudguru.com/course/github-actions-deep-dive)。或者，如果你认为 Jenkins 可能是你的工具，你可以通过 ACG 的[通过做](https://acloudguru.com/course/learn-jenkins-by-doing)系列动手实验或我们的 [Jenkins 基础](https://acloudguru.com/course/jenkins-fundamentals)课程来了解更多关于 Jenkins 的信息。

无论哪种方式，玩得开心，并自动化所有的事情！

* * *

[**获得痛苦的云词典**](https://get.acloudguru.com/cloud-dictionary-of-pain)
说云不一定要努力。我们分析了数以百万计的回复，找出了最容易让人犯错的概念。抓住这个[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)获取一些最痛苦的云术语的简洁定义。