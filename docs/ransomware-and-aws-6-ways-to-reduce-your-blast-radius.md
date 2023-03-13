# 勒索软件和 AWS: 6 种减小爆炸半径的方法

> 原文：<https://acloudguru.com/blog/engineering/ransomware-and-aws-6-ways-to-reduce-your-blast-radius>

在本帖中，我们将讨论勒索软件和 AWS——它是如何工作的，以及如何在云中构建时降低勒索软件的风险。

勒索软件无处不在。除非你过去一年一直生活在岩石下(在过去 16 个月左右的时间里，这可能不是一个可怕的地方)，否则你可能已经看到了关于勒索软件的头条新闻。它搅乱了从[气体](https://www.cnn.com/2021/05/09/business/gas-price-spike-fears/index.html)到[保健](https://www.wsj.com/articles/irish-healthcare-system-struggles-with-tech-disruptions-after-may-ransomware-attack-11624037143)到[肉类](https://www.washingtonpost.com/politics/2021/06/02/cybersecurity-202-meat-industry-is-latest-be-thrown-into-chaos-by-ransomware/)的一切。(别碰我们的汉堡，你们这些怪物！)

就在本月早些时候，据[报道](https://www.reuters.com/technology/exclusive-us-give-ransomware-hacks-similar-priority-terrorism-official-says-2021-06-03/)美国政府现在给予勒索软件攻击与恐怖主义同等的优先权。

政府正在与之斗争。

人们正在写关于它的歌曲。

但是你能做什么呢？

说到勒索软件和 AWS，它是如何工作的？勒索软件常见的攻击媒介有哪些？在 AWS 云中构建时，您如何降低勒索软件的总体风险？

这些问题太多了。幸运的是，Mark Nunnikhoven 有很多答案。

Mark 是一名法医科学家/作家/演说家/教师/教练/建设者，他帮助组织在管理我们数字世界的风险的同时导航其云转型。除了在 [ACG](https://get.acloudguru.com/acg-community-summit) [社区](https://acloud.guru/series/acg-community-summit) [峰会](https://get.acloudguru.com/acg-community-summit)上发表演讲之外，Mark 还与 ACG 就从 [re:Invent keynotes](https://acloudguru.com/blog/engineering/breaking-down-the-werner-vogels-keynote-reinvent-2020) 到[云安全](https://go.acloudguru.com/Leaders-Cloud-Security-Webinar)到[AWS market place](https://acloudguru.com/blog/business/five-surprising-things-you-can-do-with-the-aws-marketplace)的 5 件令人惊讶的事情进行了交流。

在 ACG 社区峰会的会议上，Mark 谈到了在涉及勒索软件和 AWS 时，降低攻击半径的重要性。

这篇文章涵盖了 Mark Nunnikhoven 在 ACG 社区峰会上的一些重要观点。这是电影优于小说的一个例子。相信我们——它值一块表。点击查看 Mark 的完整会话[。](https://acloud.guru/series/acg-community-summit/view/103)

*注意:下面的内容包括来自 Mark 的引用和细节，为了清晰、简洁和总体美观，这些内容已经过编辑。任何错误或误解很可能是编辑的错误，而不是马克的错误。*

什么是勒索软件？

勒索软件是一种恶意软件，它对数据进行加密并持有数据以获取赎金。这是一个问题——一个 420 亿美元的问题。这是 2020 年全球勒索软件攻击的[估计](https://blog.emsisoft.com/en/35583/report-the-cost-of-ransomware-in-2020-a-country-by-country-analysis/)美元成本。到 2021 年，这个数字没有下降的迹象。

## 它是如何工作的？

有一天，你正在忙你的事情(也许你正在 ACG 社区峰会上做一个关于勒索软件的演讲)，你匆忙点击了一个弹出的通知。

类似这样的。

似乎没什么坏处。直到你看到这样的屏幕。

呀。红屏很少是一件好事。(注意:图片中的钱包无效。请不要往那里寄钱。)

![](img/fd2ffd033709bf40df842d4f19baa09d.png)

现在你被一个罪犯锁在了我们的数据之外，他拿着数据来勒索赎金。

![](img/01e6272e797e92ac997965520525eae8.png)

这在数字上相当于闯入卢浮宫去偷蒙娜丽莎。当然，在一个假设的艺术品盗窃案中，盗窃/赎金是可行的，因为蒙娜丽莎只有一份拷贝。但是在数字世界里，你*应该*有你数据的多份拷贝。(您确实有多份数据副本，对吗？)所以。。。问题解决了？

没有。今天，勒索软件已经发展到可以嗅出、锁定并销毁你的副本，确保你就像没有蒙娜丽莎的卢浮宫。(我不知道用法语怎么说，但用互联网上首字母缩略词来说:“你解决了。”)

**[看点:领导需要了解哪些关于云安全的知识](https://go.acloudguru.com/Leaders-Cloud-Security-Webinar)**
你的业务在云端安全吗？答案很大程度上取决于你。观看 Mark Nunnikhoven 的[免费点播网络研讨会](https://go.acloudguru.com/Leaders-Cloud-Security-Webinar)，他将解决云安全的关键问题。

勒索软件谁负责？

* * *

勒索软件背后的这些罪犯是谁？忘记你在电视上看到的。这不是民族国家。这是有组织的犯罪——为牟利而犯下的罪行。罪犯们试图尽可能多的赚钱，他们非常擅长这个。

* * *

## 如果我付了赎金，我能拿回我的数据吗？

也许吧！但这很复杂。

## 幸好(？)，因为这是*有组织的*犯罪，而且涉及到利益，所以这个游戏有一些规则。

2020 年支付的平均赎金为 312，493 美元。

记录在案的最大一笔赎金是 450 万美元。

![](img/5c679e2222b54f7e82acdc1480929800.png)

*   据报道，如果你支付赎金，你有 97%的机会获得一个有效密钥来解密你的数据。

*   然而，46%的情况下，公司[报告](https://www.cybereason.com/ebook-ransomware-the-true-cost-to-business)存在某种程度的腐败。当然，恢复不是立竿见影的，所以仍然有巨大的影响。

*   再次被勒索软件攻击的几率有多大？

*   据报道，80%的付费组织[再次受到打击。有道理。一旦你付出了，你就表明你更有可能再次付出。](https://www.cybereason.com/ebook-ransomware-the-true-cost-to-business)

## 从勒索病毒中恢复需要多少时间和金钱？

*   从勒索软件攻击中恢复的平均成本为 120 万美元。(这是直接成本，而不是间接成本，如业务下滑造成的收入损失。)

## 你不仅要向罪犯支付 312，000 美元，还要支付加班费、新系统费、顾问费——所有这些额外的费用。

![](img/0c63d14508ee9ce330aa2c0a8f9ed710.png)

*   从勒索病毒中恢复平均需要 16.1 天

*   “作为一名前事故响应者，让我告诉你，那 16 天*糟透了*，”努恩尼克霍文说。“你在夜以继日地工作。你压力很大。你要努力确保将所有攻击从你的网络中清除，因为如果你不这样做，它还会回来。”

*   该不该支付勒索软件？

从社区的角度来看，你不应该付钱。因为罪犯得到的报酬越多，他们就越会攻击。

## 但是从商业角度来看，你很可能最终会付钱。因为如果选择是你不能从你自己的备份中恢复，这将花费你几个月的时间来恢复在线，或者你可以支付赎金*可能*现在恢复在线，这是一个非常简单的商业决策。

最终的答案可能是:“呃，我不知道！”但不要只是从我们这里拿走。美国政府对此持什么立场？网络和新兴技术副国家安全顾问安妮·纽伯格(Anne Neuberger)提供了一个非常政治正确的版本“嗯，我不知道”——[说](https://www.whitehouse.gov/briefing-room/press-briefings/2021/05/10/press-briefing-by-press-secretary-jen-psaki-homeland-security-advisor-and-deputy-national-security-advisor-dr-elizabeth-sherwood-randall-and-deputy-national-security-advisor-for-cyber-and-emerging/):“我们认识到网络攻击的受害者经常面临非常困难的情况。当他们在支付赎金方面别无选择时，他们不得不经常权衡成本效益。”

“他们在网络钓鱼邮件中所做的大量研究和 A/B 测试——如果不是如此邪恶，这将是一件美妙的事情。”

勒索软件实际上是如何运作的？

* * *

> 当勒索软件的赎金在 300 到 500 美元左右时，事情非常简单。勒索软件会登陆你的系统并把你锁在外面。这种方法是高度自动化的，旨在击中尽可能多的人。
> 
> – Mark Nunnikhoven

* * *

## 幸运的是，我们再也看不到这种情况了。

幸运的是，攻击者现在已经扩大了他们的活动范围。

攻击者现在转向多阶段攻击。他们正在研究你，找出你的弱点，了解你的一切，然后他们登陆其他恶意软件，以找出最佳攻击方式。然后，他们会探索您的网络，寻找备份、弱点和高价值数据。然后，他们罢工。

勒索软件攻击的典型工作流程

**研究**

### 犯罪分子利用社交媒体和公司网站列出高管名单。这就为攻击者提供了一个简单的途径，让他们可以通过公布姓名的方式进入公司。

然后，他们研究移动应用程序、网站和 GitHub 来寻找密钥。我们当中有多少人开发过内置 AWS 密钥的 Android 或 iOS 应用程序？如果它被公布，攻击者可以得到这些。这是人们进入您的帐户的主要攻击媒介。

*   **着陆**

*   当他们登陆时，几乎都是网络钓鱼。不间断的网络钓鱼。94%的恶意软件是通过网络钓鱼电子邮件传播的。因为很简单。作为一名罪犯，我可以做足够的研究来了解你的公司，使我的电子邮件可信。“他们在网络钓鱼邮件中进行的大量研究和 A/B 测试——如果它不是如此邪恶，那将是一件美好的事情，”Nunnikhoven 说。

你所学的关于网络钓鱼的一切都是错的。他们告诉你的第一件事就是不要点击链接。但是链接是为了点击而建立的。所以不合拍？不会发生的。

*   这里是避免网络钓鱼的关键。如果你点击了一个链接，并被要求采取行动，如登录谷歌，下载文件，或运行程序，停止。*然后*质疑链接的出处。因为如果你在过去的五年里看了任何营销链接，你就知道你无法分辨什么是合法的，什么是非法的。

![](img/85090e6dd21bcb7751d7e3a80356f2db.png)

*   如果他们无法对您进行网络钓鱼，他们会因为薄弱的密码策略而进入。不要怪弱密码，要怪弱密码策略。

*   你被告知的关于选择强密码的一切都是错误的。选择一个密码短语并使用密码管理器。仅在一年一次或您认为自己受到攻击时更改密码。但是大多数组织还没有采纳这一指导。他们做 90 天的旋转和大写字母，符号——所有这些可笑的事情。没啥效果。数学不成立，这导致更多的安全漏洞。

*   这不是用户的责任，是安全团队的责任(但他们会责怪你)。所以请记住:强密码是长密码。

*   **探索**

*   探测 API、VPCS 等。—在探索时，犯罪分子会查看 AWS 中的 API，他们会查看 VPC 配置，他们会查看安全组—诸如此类。

检查角色和 IAM 键—他们也在查看他们能看到的角色。钥匙也一样。“这一把钥匙能让我走多远？我从你的手机应用程序里截取了这个。我拿着这把钥匙能去哪里？”

*   **锁定**

*   最后，他们将加密数据并阻止对这些数据的访问。

我们如何防御勒索病毒？

*   有大量不同的方法来抵御勒索软件，但没有一个是万无一失的。

## 但是，也有我们可以坚持的原则。总的来说，它们有点像你家前草坪上的安全系统警报标志。你的安全系统可能不会让你的房子成为一个坚不可摧的堡垒，但它可能会把罪犯推向更容易的受害者。

6 种减小爆炸半径的方法

记住这一点，这里有一些原则可以帮助你抵御勒索软件。这六个要点并不是它的结束，但它们是一个很好的概述，可以让你朝着正确的方向思考。

### “减小爆炸半径”的想法来自 AWS re:Invent 2020 的 Werner Voggels 博士。这个想法是为了确保如果(或当)事情搞砸了，它不会通过你的系统级联。

**不断更新实例和容器图片**自动更新对安全有奇效。如果你有问题的话，修补它并修复它。你将面临更少的问题和更容易的问题。

![](img/46983e255f148ba3d5bd1b16bc97e636.png)

**AWS 安全参考架构**
AWS 的安全参考架构上周刚刚从 AWS 退出。(更多[此处](https://aws.amazon.com/blogs/security/aws-security-reference-architecture-a-guide-to-designing-with-aws-security-services/)。)这个维护的参考体系结构包括所有与安全相关的 AWS 服务的链接，以及如何充分利用它们。

1.  **使用良好架构框架迭代** 我有偏见，因为我在 ACG 教[掌握 AWS 良好架构框架](https://acloudguru.com/course/mastering-the-aws-well-architected-framework)课程。但是安全不是孤立的事情。这只是你在构建一个好的解决方案时要做的事情之一。一个架构良好的框架围绕五个支柱构建，安全性是其中之一。这都是关于平衡，建设良好，并减少爆炸半径。

2.  最低特权原则
    确保用户或角色只能访问他们工作所需的内容。仅此而已。这意味着…

3.  **否*完全访问 IAM 策略** 我明白为什么它们会使开发变得更容易，但是它们永远不应该用于生产。如果你正在使用它们，请停止。你怎么停下来？

4.  **持续使用 IAM Access Analyzer**这个映射出使用权限方面的内容，并帮助您收紧这些策略。

5.  如何创建勒索软件灾难恢复和事件响应计划？

6.  对于您的灾难恢复和事件响应计划，让我们问自己几个问题。

## 灾难恢复问题

从备份中恢复需要多长时间？(你确定吗？)
你有备份。对吗？(对吧？？？)如果你还没有备份，确保你有备份，然后测试它们。您需要确保您可以恢复。

#### **如果你和你的团队没有笔记本电脑，你会怎么做？**还能恢复吗？如果没有笔记本电脑，您还能在 AWS 中运行您的构建吗？这似乎是一个奇怪的问题，但却是一个值得研究的问题。

*   **您是否正在备份到另一个仅附加帐户？**对于备份，您是否备份到一个单独的帐户—一个不同的 AWS 帐户(记住，它们是免费的)—并且该帐户是仅附加的吗？能不能只写不盖不删？那是保护自己的关键一步。因为现在你有了另一个独立的帐户，它总是有你的数据的副本，你可以恢复，而不必支付赎金。

*   事故响应计划问题

*   你怎么知道发生了事故？

#### 您最重要的数据在哪里？
不要尴尬。这个问题没人能回答。我和数以千计的组织合作过，几乎没有人能回答这个问题。但是，你今天应该试着弄清楚。

*   如果没有电子邮件，你会如何联系每个人？
    你有书面名单吗？如果您丢失了所有的 IT 系统，您将如何合作进行恢复？

*   这是您的事件响应计划的技术起点

*   我们将使用一个非常简单的模式来通知我们什么时候需要调查。

### 标记亚马逊云观察事件

将某些事件发送到 AWS Lambda

![](img/62eed7271196709befee2861e0a5abd9.png)

1.  然后把它们放进 Slack(或者你选择的工具)
2.  最后，根据你发给 Slack 的东西采取行动
3.  你在寻找什么项目？它们堆积如山，但这里有几个可以给你一个概念:
4.  AddUserToGroup

AttachUserPolicy

*   CreateAccessKey
*   CreateLoginProfile
*   DeleteAccessKey
*   DeleteUser
*   勒索软件和 AWS 常见问题
*   在我们结束之前，让我们快速回顾一下。

## **知道问题。**勒索软件是一种利益驱动型犯罪。

**减小爆炸半径。**确保如果出现故障或我们无法访问，不会影响到其他所有事情。

*   实践一个 IR 计划。建立并实践一个 IR 计划。你想解决这个问题，这样如果真的发生了什么，你就不会手忙脚乱。
*   这在现在的勒索软件中很常见。在“探索”阶段，攻击者会标出您备份到的位置。因为他们知道如果你有备份，你就不用付钱了。因此，在使用 AWS 时，一个与你的主账户完全分开的只写账户是关键。再说一遍，账号是免费的。所以你不会多付钱。但是作为一个新帐户，您会得到一个很好的硬边界，您可以锁定所有权限并创建一个角色，该角色只允许创建新备份，而不允许其他任何操作。通过这种方式，您可以将所有东西完全分开。
*   有时候！这完全取决于你的政策。随着勒索软件的兴起，网络安全保险在过去一年变得突出。此时，你需要一个出色的法律团队来逐行检查，你需要一个真正能干的安全团队来告诉你你当前的状态。但是，如果你遵循合同中的所有要求，很多时候你的网络保险将涵盖潜在赎金的成本——并且它将涵盖大部分恢复成本。

    它不会覆盖任何损失的收入或机会成本。因此，如果你正在寻找 120 万美元的恢复和 30 万美元的赎金，很有可能你的保险会涵盖这一点。但是如果你在这两周内损失了 1000 万美元的销售额，那你就亏了。(当然，在那次袭击之后，你的保险费也在上涨。)

**What’s the best way to prevent ransomware from excluding the backup strategy?**

我的一个爱好就是看电视电影里是怎么刻画安全感的。从来都不是真的。总是超级无聊。枯燥乏味的工作最终变得令人兴奋。但是当你谈论来自民族国家的勒索软件时，它提高了赌注，使它变得超级令人兴奋，这就是为什么你在电影和媒体中看到它这么多。

我们已经看到了一些国家使用勒索软件的孤立案例，但这更多是为了分散注意力。所以他们进入并获取信息，这才是真正的目标。但他们基本上是让你*相信*这是勒索软件，所以当他们带着你的数据从后门出去时，你只能用一种方式回应。很少见，但确实有。如果你被勒索软件攻击，很可能有 99.99%的可能性是有组织犯罪试图赚钱。

**Does cybersecurity insurance cover the costs of ransomware?**

尽管有 [AWS 认证安全专业认证](https://acloudguru.com/course/aws-certified-security-specialty)——这很值得参加——但我认为，特别是在开始时，如果你学会如何更好地构建，你将成为一名更好的安全人员。

所以看看 [DevOps 考试](https://acloudguru.com/learning-paths/aws-devops)和 [AWS 架构](https://acloudguru.com/learning-paths/aws-architect)考试会是一个更好的起点。因为你会了解环境。如果你不了解它，你就无法保护它。这就是我们遇到关于云安全的大多数问题的地方:当人们采用旧的方法并试图在云中应用它时。从学习如何更好地构建开始，一旦你确定了这一点，就去参加安全专业化认证。

**How many ransomware attacks involve nation states?**

*你可以在网上找到马克·努尼霍文[@马克恩卡](https://twitter.com/marknca)和[https://马克恩.卡](https://markn.ca/)。*

**What certifications do you recommend for someone starting in a security operations analyst role?**

**锁定你的安全技能**。
想了解更多关于勒索软件和云中安全性的信息吗？查看我们的[掌握 AWS 架构良好的框架](https://acloudguru.com/course/mastering-the-aws-well-architected-framework)课程，然后挖掘我们的大规模实践云学习库。

* * *

*You can find Mark Nunnikhoven online [@marknca](https://twitter.com/marknca) and [https://markn.ca](https://markn.ca/).*

* * *

**Lock down your security skills**.
Want to learn more about ransomware and security in the cloud? Check out our [Mastering the AWS Well-Architected Framework](https://acloudguru.com/course/mastering-the-aws-well-architected-framework) course, then dig into our massive library of hands-on cloud learning.