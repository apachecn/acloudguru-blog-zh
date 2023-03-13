# AWS 升级 CodeGuru Reviewer |一位云专家

> 原文：<https://acloudguru.com/blog/engineering/aws-upgrades-codeguru-reviewer-efs-waf-and-aws-budgets>

你好，云大师们！我是斯蒂芬·塞尼特，为您带来本周最精彩的 AWS 新闻！这一次，我们对 CodeGuru Reviewer 进行了新的安全更新(即日志注入缺陷的检测器)，以及 EFS 的新性能特性、Web 应用程序防火墙的新安全特性和 aws 预算的新自动调整特性。请继续阅读所有细节。

* * *

**通往更好职业的钥匙**

[立即开始 ACG](https://acloudguru.com/pricing) 通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室来改变你的职业生涯。

* * *

## **CodeGuru Reviewer 安全更新**

亚马逊的 CodeGuru Reviewer 最近有了[两个有趣的更新](https://aws.amazon.com/blogs/aws/new-for-amazon-codeguru-reviewer-detector-library-and-security-detectors-for-log-injection-flaws/)，宣布了新的[检测器库](https://aws.amazon.com/about-aws/whats-new/2022/02/codeguru-reviewer-detector-library-repositories/)，以及针对日志注入漏洞的新的[安全检测器](https://aws.amazon.com/about-aws/whats-new/2022/02/amazon-codeguru-reviewer-detects-apache-log4j/)。

我们只需要回想一下去年 12 月，当时阿里云的安全研究人员在流行的 Java 日志工具 Log4J 中发布了现在臭名昭著的 Log4Shell 漏洞。这场混乱影响了从推特到《我的世界》再到联网烤面包机的一切。任何参与发现和补救这个问题的人(*举手*)都会知道这是一个多么大的挑战。

这种新的检测器可以更容易地防止伪造或恶意的条目进入我们正在开发的应用程序。诚然，这不会解决所有问题，但它让我们更近了一步。新的检测器库包含 CodeGuru 使用的所有不同安全和质量检测器的信息，包括代码示例、合规性指标和其他信息，以帮助您更深入地了解他们的发现。

此外，如果你仍然不完全熟悉 Log4Shell 漏洞，我们在 Pluralsight 的团队整理了一个很酷的[博客帖子](https://www.pluralsight.com/blog/security-professional/log4j-vulnerability-security-flaw-and-solution)进一步解释它，并且有一个[网络研讨会](https://www.youtube.com/watch?v=9usNJgRJIW4)讨论后果和剩余的问题。

## **EFS 支持亚毫秒级读取延迟**

亚马逊弹性文件系统现在支持[亚毫秒级读取延迟](https://aws.amazon.com/blogs/aws/amazon-elastic-file-system-update-sub-millisecond-read-latency/)用于通用存储。EFS 的分布式特性意味着它在跨系统处理文件时会产生一些延迟。虽然许多应用可能能够忍受这种延迟，但高性能解决方案需要更低的效率。第一个字节到达的时间有很大的不同:将延迟降低到 600 微秒就可以将延迟减半。

通用 EFS 的写操作仍然处于较低的个位数毫秒范围内，尽管 EFS 最大 I/O 延迟仍然较高，但在许多情况下，吞吐量的权衡仍然非常值得。要了解全部细节，请查看关于 EFS 性能的 AWS 文档。此功能现在在 EFS 可用的所有地区都可用，不需要任何更改即可生效。

## **晶圆欺诈控制**

新的 AWS [Web 应用防火墙欺诈控制–防止帐户盗用(ATP)](https://aws.amazon.com/about-aws/whats-new/2022/02/aws-waf-fraud-control-login-credential-attacks/) 解决方案(*phew*)已经发布，旨在帮助保护您的 Web 应用登录页面免受一系列攻击。“帐户接管预防”会查看尝试的登录活动，并记录任何可能表明尝试的异常行为，例如:

*   凭据填充，攻击者试图使用从以前的数据泄露中窃取的各种凭据，或者
*   暴力破解，只需在登录页面上输入随机密码，直到成功

到目前为止，该功能仅在少数地区可用，激活该功能需要额外支付[费用](https://aws.amazon.com/waf/pricing/)。每月的订阅费和每千次登录尝试 1 美元的费用，肯定不便宜。但是对于大型企业来说，这是一笔很小的成本。由于它是 WAF 的一部分，并在网络边缘阻止攻击，我希望暴力攻击在产生巨大成本之前被关闭。

如果你运行的是自己的登录解决方案，还没有包含这种保护，那么[查看一下](https://docs.aws.amazon.com/waf/latest/developerguide/aws-managed-rule-groups-atp.html)可能是值得的。

## **自动调整预算**

AWS Budgets 现在支持[自动调整预算](https://aws.amazon.com/about-aws/whats-new/2022/02/auto-adjusting-budgets/)，可以根据您的使用情况动态更新预算限额。除了固定预算和计划预算之外，自动调整预算还会跟踪上一个预算期间的平均支出，并使用该数字来设置新的基准，并向任何预算订阅者发送警报。

为了解决房间里的大象，是的，这是 AWS 采取了旨在限制您的支出的服务，并增加了旨在增加您的支出的功能。

Corey Quinn 对此进行了精彩的总结，他在推特上解释道，“AWS 的预算到了。”

组织在云账单方面面临的挑战之一是，他们的财务管理通常仅次于构建材料。这意味着当您新部署的数据库集群开始每月运行额外的 20，000 美元时，它有时不会在预算报告中考虑。警报被触发，只是变成白噪音，直到有人将预算重新调整到新的水平——通常是在首次做出改变后的几周或几个月。这就是自动调整预算的目的。

组织需要有可靠的管理实践来了解他们的云成本。没有 it，您绝对无法发展成熟的云组织。否则，组织会因为预算太难而完全忽略它，我认为这是一个方便的特性——如果使用时绝对小心的话。

## 我们会持续更新

想要跟上 AWS 的所有事情？在 YouTube 上订阅一位云专家的每周云新闻。你也可以在[脸书](https://www.facebook.com/acloudguru)上喜欢我们，在[推特](https://twitter.com/acloudguru)上关注我们，或者在 [Discord](http://discord.gg/acloudguru) 上加入对话。

本周新闻到此结束！直到下一次，勇往直前，学习所有的东西。一如既往地保持敬畏，云大师们！