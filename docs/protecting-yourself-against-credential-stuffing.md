# 保护自己免受凭据填充

> 原文：<https://acloudguru.com/blog/engineering/protecting-yourself-against-credential-stuffing>

在本帖中，我们将讨论如何通过使用密码管理器和 MFA 来保护自己免受凭据填充。此外，OWASP、他们的十大列表和 web 应用程序安全性。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

我们都看到了。感觉每周都有关于凭据或个人身份信息被泄露的新闻报道。

为了应对这些攻击，组织实施了各种安全措施，包括阻止攻击的 Web 应用程序防火墙(WAF)和监控攻击的大型安全运营团队。尽管这些措施对于 web 应用程序攻击来说是很好的防御措施，但是许多最终用户的凭据仍然受到威胁，并且未经授权的用户帐户访问仍然是一个问题。

因此，问题依然存在:**即使在凭据被盗后，最终用户如何更好地保护自己？**

让我们来看看导致 web 应用程序凭据受损的攻击，以及您(最终用户)可以保护自己免受攻击的方法。

## 什么是凭据填充？

凭据填充是黑客使用的一种技术，通过使用窃取的凭据来接管合法用户帐户。

这种攻击基本上包括获取窃取的凭据(通常来自犯罪来源或最近的违规行为),并尝试使用窃取的凭据登录一系列网站。这种自动攻击非常成功，因为人们经常对多个网站重复使用相同的凭据。

* * *

[![AWS Cloud Compliance Governance Security](img/6248396917d6ad72577def2a4bf7b70e.png)](https://acloudguru.com/content/securing-aws-environment-webinar)

[**观看:保护您的 AWS 环境**](https://acloudguru.com/content/securing-aws-environment-webinar) 在[这个免费的点播网络研讨会](https://acloudguru.com/content/securing-aws-environment-webinar)中，云安全专家唐·麦咭详细介绍了如何让复杂的 AWS 环境从零到安全。

* * *

### 密码管理员

显而易见的解决方案是对每个网站使用不同的密码。。。但是记住所有这些密码是一项具有挑战性的任务。然而，有一种叫做“密码管理器”的解决方案，可以把你所有的密码储存在一个加密的保险箱里。

可以访问此保险库以快速简便的方式检索密码，同时防止您重复使用密码。

密码管理器有效地降低了凭据填充的风险，因此一个受损的网站帐户不会导致其他帐户因凭据被盗而受损。

### 多因素身份认证(MFA)

除了密码管理器，许多网站现在还提供多因素身份验证(MFA)的使用。这意味着用户必须使用两种形式的身份验证来登录他们的用户帐户。

*   第一种形式的认证是“你知道的东西”，通常是用户名和密码。
*   第二种形式的认证通常是 SMS 文本消息，它被认为是“您拥有的东西”,因为您必须实际接触移动设备才能接收第二种形式的认证。
*   “你是什么”将是一种生物认证形式，如指纹或面部扫描。

使用 MFA 降低了帐户泄露的可能性，因为远程黑客不太可能访问移动设备或身份验证所需的指纹。

## Web 应用程序安全性

借助这些解决方案，用户能够更好地保护他们的在线帐户，并防止对这些帐户的未授权访问。然而，这只是 web 应用安全(或 web app sec)方面的冰山一角。

[开放 web 应用安全项目(OWASP)](https://owasp.org/) 是一个非营利基金会，致力于研究 Web 应用安全问题并领导解决这些问题的项目。

OWASP 十大项目涵盖了一些与 web 应用程序相关的最重要的安全风险，并对跨站点脚本和注入等攻击进行了深入分析。黑客利用这些攻击来危害 web 应用程序数据库，并为我们讨论的凭证填充攻击获取用户凭证。

## 了解有关 web 应用程序安全性的更多信息

想要更好地了解 web 应用程序安全性吗？无论您有兴趣了解黑客是如何进行这些攻击的，还是想了解更多关于防御这些攻击的信息，我们的 [OWASP 十大安全风险介绍](https://acloudguru.com/course/introduction-to-owasp-top-10-security-risks)课程将从这两个方面进行介绍。还有一个动手实验室来练习 web 应用程序黑客技术，让您的技能更上一层楼。

## 锁定最受欢迎的技能

[加入云专家](https://acloudguru.com/pricing)并访问我们所有的课程、实验室、测验和学习途径，在您所选择的云领域逐步将您从新手变成专家。[开始免费试用](https://acloudguru.com/pricing)或查看[本月免费云培训](https://acloudguru.com/blog/news/whats-free-at-acg)。

你还可以[在 YouTube 上订阅一位云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每周云新闻，就像我们在[脸书](https://www.facebook.com/acloudguru)上一样，在[推特](https://twitter.com/acloudguru)上关注我们，并在 [Discord](http://discord.gg/acloudguru) 上加入对话。