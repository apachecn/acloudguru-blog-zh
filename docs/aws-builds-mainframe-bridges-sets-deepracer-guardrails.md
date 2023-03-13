# AWS 建立大型机桥，设置 DeepRacer 护栏

> 原文：<https://acloudguru.com/blog/engineering/aws-builds-mainframe-bridges-sets-deepracer-guardrails>

本周，我们得到了另一组精心策划的适合框架的 AWS 新闻！AWS 继续为大型机商店搭建桥梁，Amazon Lookout for Metrics 得到了一个后视镜，我们的小伙伴 DeepRacer 得到了一些护栏。让我们来看看本周所有有趣的 AWS 新闻。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## AWS 大型机现代化现已全面推出

你有多少次坐在会议室里想，“嘿，让我们把大型机迁移到 AWS 吧？”只要启动你的 [3270 终端](https://commons.wikimedia.org/wiki/File:IBM_3277_Model_2_terminal.jpg#/media/File:IBM_3277_Model_2_terminal.jpg)，让每个人从退休状态中醒来，开始复制粘贴。要是有那么简单就好了，对吧？

[AWS 大型机现代化服务于 2021 年发布，现已全面上市](https://aws.amazon.com/about-aws/whats-new/2022/06/aws-mainframe-modernization-generally-available/)。但是 AWS 对大型机了解多少呢？嗯，通过收购和与专门从事大型机迁移的公司合作，AWS 组建了一支相当不错的团队。AWS 去年收购的 [Blu Age](https://www.bluage.com/) ，是他们给我们带来了在 Lambda 上运行 COBOL 的能力。AWS[还与 Micro Focus](https://www.microfocus.com/en-us/partners/strategic-alliance-aws) 合作，后者提供一套大型机迁移工具。

但是工具本身并不能完成工作。大多数大型机商店在数万行 COBOL 或 PL/1 代码中嵌入了几十年的业务逻辑。我们在这里谈论的不是简单的提升和转移，而是一项重大的平台迁移工作。为此，AWS 还为大型机建立了[迁移加速计划，并创建了](https://aws.amazon.com/migration-acceleration-program/mainframe/)[大型机现代化合作伙伴资格](https://aws.amazon.com/blogs/apn/introducing-the-new-aws-mainframe-modernization-competency-featuring-validated-aws-partners/)。

但是…大型机真的还是一个东西吗？绝对的！尤其是在银行、保险和医疗保健行业。据路透社报道，约 80%的现场商务交易和 95%的 ATM 交易仍然依赖于运行在大型机上的 COBOL 代码。

## 亚马逊寻找更快工作的指标

亚马逊 Lookout 系列服务是一个完美的例子，它将一些复杂的机器学习过程抽象为易于获取的现实世界价值和交钥匙服务。

核心是，亚马逊 Lookout 服务使用异常检测算法来识别不寻常的事情，并让这些事情引起你的注意。

*   **Amazon Lookout for Equipment**可以发现设备性能的细微变化，并进行更主动的维护。
*   **Lookout for Vision** 可进行大规模视觉检测，并有助于质量保证。
*   **Amazon Lookout for Metrics** 可以在 CloudWatch 中提供相同的异常，从我们开始覆盖的那一点开始。

[这种回溯测试模式允许 Amazon Lookout for Metrics 及时回溯，以创建更准确的基线](https://aws.amazon.com/about-aws/whats-new/2022/06/amazon-lookout-metrics-enables-anomaly-detection-historical-cloudwatch-data/) —这对于有季节性波动或其他不一定是异常的涨落的组织来说非常有用。

DeepRacer 安装了护栏

## 意想不到的后果。我们可能都有过这样的经历。

例如，假设你在组织内发起了一个 [DeepRacer League](https://learn.acloud.guru/series/deepracer) ，以此作为提高员工参与度和学习新技能的有趣方式。假设您的团队开始起步，应用程序开发团队和网络工程团队之间的竞争变得异常激烈。假设在月底，你接到应付账款人员打来的恐慌电话，询问为什么你的 AWS 账单比以往高出三倍。

我明白了。它发生了。

幸运的是，如果你愿意，你现在有一些护栏可以用在你的 DeepRacer 上。 [AWS DeepRacer 多用户模式](https://aws.amazon.com/about-aws/whats-new/2022/06/aws-deepracer-quota-management/)现在允许我们对参与者应用配额——帮助控制训练小时数、模型数量，甚至打开和关闭训练功能。毫无疑问，这一特性源自那些发现自己与我们完全假设的例子处于相同位置的组织。

[**自动化 AWS 成本优化**](https://go.acloudguru.com/AWS-Cost-Optimization-Webinar)
经济高效地使用 AWS 可能是一项挑战。在这个[免费点播的网络研讨会](https://go.acloudguru.com/AWS-Cost-Optimization-Webinar)中，您将了解 AWS 成本优化工具和策略的概况，如[数据存储优化](https://acloudguru.com/course/introduction-to-optimizing-data-storage-in-aws)。

* * *

油炸机器人 Flippy

* * *

## 在我们结束之前，最后一个小花絮——你可能很快就会感谢 AWS 提高了你的快餐薯条的质量。机器人油炸站 Flippy 背后的公司 Miso Robotics 已经宣布与 AWS 合作，使用 AWS Robomaker [来大大加快他们的模拟和开发过程](https://misorobotics.com/newsroom/miso-robotics-announces-collaboration-with-aws-to-test-robots-at-scale/)。Flippy 2 煎炸机器人已经被几家快餐连锁店订购了——他们更喜欢被这样称呼——包括我自己心虚的选择“白色城堡”。

就我个人而言，欢迎我们新的油炸机器人霸主，并提前感谢他们不知疲倦的服务。

*想跟上 AWS 的一切？* [*在 YouTube 上订阅一位云大师*](https://www.youtube.com/c/AcloudGuru) *，获取每周亚马逊新闻和 AWS 公告。你也可以像 ACG 上的*[](https://www.facebook.com/acloudguru)**一样，关注我们上的* [*推特*](https://twitter.com/acloudguru) *，或者加入* [*不和谐*](https://discord.com/invite/pluralsight) *的对话！**

**Want to keep up with all things AWS?* [*Subscribe to A Cloud Guru*](https://www.youtube.com/c/AcloudGuru) *on YouTube for weekly Amazon news and AWS announcements. You can also like ACG on* [*Facebook*](https://www.facebook.com/acloudguru)*, follow us on* [*Twitter*](https://twitter.com/acloudguru)*, or join the conversation on* [*Discord*](https://discord.com/invite/pluralsight)*!**