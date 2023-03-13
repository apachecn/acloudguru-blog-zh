# 自动气象站红移数据交换:Lambda 支持 IPv6 |云专家

> 原文：<https://acloudguru.com/blog/engineering/aws-data-exchange-for-redshift-is-ga-lambda-supports-ipv6-for-inbound-connections>

新的一年，新的 AWS 新闻！在这篇文章中，我们将讨论亚马逊红移的 AWS 数据交换，AWS Lambda 现在支持 IPv6 的入站连接，以及亚马逊翻译的新脏话屏蔽。这是本周 AWS 的新内容。我们走吧！

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## 亚马逊红移在 GA 的 AWS 数据交换

亚马逊的 AWS 数据交换红移于[年现](https://aws.amazon.com/about-aws/whats-new/2022/01/aws-data-exchange-amazon-redshift/)年全面上市。

如果您以前没有使用过 RedShift，它是一个数据仓库解决方案，允许您对存储在数据湖和数据库中的数据运行复杂的分析查询。

AWS 数据交换是一项服务，使您能够访问和使用第三方数据进行分析。比如路透社这样的公司的新闻数据。

这一新的声明意味着现在可以轻松地在数据交换中查找和订阅第三方数据，并使用 RedShift 直接查询数据，甚至将其与您自己的数据相结合。

## Lambda 直接支持 IPv6 的入站连接

Lambda [现在](https://aws.amazon.com/about-aws/whats-new/2021/12/aws-lambda-ipv6-endpoints-inbound-connections/)直接支持互联网协议版本 6 (  IPv6)的入站连接。

这非常酷，因为这意味着你现在可以通过 IPv6 调用 Lambda 函数，而不必担心 IPv6 和 IPv4 之间的转换。

Lambda 的新双栈端点支持 IPv4 和 IPv6，使这一新功能成为可能。

因此，当客户端向双栈 Lambda 端点发出请求时，端点会根据客户端使用的协议解析为 IPv6 或 IPv4 地址。

## 亚马逊翻译补充？$ # @-使用亵渎屏蔽

亚马逊翻译现在包括[亵渎屏蔽](https://aws.amazon.com/about-aws/whats-new/2021/12/amazon-translate-profanity-masking/)。如果你不熟悉 Translate，它是一种机器学习支持的服务，允许你将纯文本从一种语言翻译成另一种语言，使你能够轻松地构建支持多种语言的应用程序。

这个新的脏话屏蔽功能可以检测 AWS 归类为脏话的单词，并使用 Grawlix 字符串屏蔽该单词，如下所示:“？$#@$

别担心。此功能是可选的。如果你想使用它的话，这是你必须去做的事情。

### 跟上 AWS 的所有事情

想要跟上 AWS 的所有事情？在推特[上关注 ACG](https://twitter.com/acloudguru)和[脸书](https://www.facebook.com/acloudguru)，[在 YouTube 上订阅云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每周 AWS 更新，并在 [Discord](http://discord.gg/acloudguru) 上加入对话。

想了解更多关于云和 AWS 的信息吗？查看我们每月更新的[免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)的轮换阵容。(不需要信用卡！)

* * *

### 了解如何像 SRE 人一样思考

观看[这个免费点播的网络研讨会](https://get.acloudguru.com/think-like-an-sre-webinar)，了解 Nobl9 工厂可靠性工程总监 Alex Hidalgo 对 SRE 文化和工具的剖析。