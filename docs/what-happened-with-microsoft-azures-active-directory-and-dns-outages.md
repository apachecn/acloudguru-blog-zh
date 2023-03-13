# 微软 Azure 的 AD 和 DNS 宕机是怎么回事？

> 原文：<https://acloudguru.com/blog/engineering/what-happened-with-microsoft-azures-active-directory-and-dns-outages>

在过去的一个月里，微软 Azure 经历了两次宕机。那么这些 Azure 宕机是怎么发生的呢？微软正在采取什么措施来防止将来出现这样的中断？

## 2021 年 3 月 Azure 广告中断

我们已经开始将云视为将移动应用程序、我们的电子邮件访问和公司基础架构的用户身份验证结合在一起的神奇调料。云永远不会停止计算，对吗？

但在 3 月 15 日，Azure 的中断导致了第二大云计算平台的大范围中断。这次宕机不仅影响了 Azure 服务，还影响了 Office、团队、Dynamics 365、Xbox Live 等等。发生了什么事？

大约 14 小时的中断始于 Azure Active Directory (Azure AD)安全密钥的例行轮换。这些密钥轮换是一件好事，可以保证用户的安全。

*(旁注:好奇[Active Directory 和 Azure Active Directory 有什么区别](https://acloudguru.com/blog/engineering/active-directory-vs-azure-active-directory-whats-the-difference)？)*

但在这一天，微软正在云提供商之间进行复杂的数据迁移。他们在一把特殊的钥匙上标上了“不要旋转”这个密钥需要暂时保留，以完成迁移。酪。。自动旋转过程忽略了这个“不要旋转”标记，当新密钥到达 Azure 服务时，用户无法登录。

打个简单的比方，想象一下一家公司在没有告诉任何人的情况下更换了进入大楼所需的刷卡。然后，第二天所有人都出现在办公室，没有人能进去。

* * *

[**后 COVID DevOps:加速未来**](https://get.acloudguru.com/post-covid-devops-accelerating-future-webinar) COVID 如何影响——甚至加速——工程团队的 DevOps 最佳实践？[观看这个免费的点播网络研讨会](https://get.acloudguru.com/post-covid-devops-accelerating-future-webinarhttps://get.acloudguru.com/post-covid-devops-accelerating-future-webinar)与 DevOps 领导者进行小组讨论，我们将在后 COVID 时代探索 DevOps。

* * *

## 2021 年 4 月 Azure DNS 宕机

2021 年 4 月 1 日，Azure DNS 开始遇到可用性问题，导致多个地区的许多客户无法访问和管理 Azure 服务，随后发生了一次较小的宕机。

这可能被认为是世界上最不好笑的愚人节玩笑，但它实际上是由 Azure DNS 服务器遇到针对 Azure 上托管的一组域的 DNS 查询激增引起的。这一系列事件暴露了 DNS 服务中的代码缺陷。这导致了服务过载和可用性下降。

[据微软](https://status.azure.com/en-gb/status/history/)称，DNS 服务自动恢复，恢复时间“超过了[微软]的设计目标。”微软报告说，它已经在努力修复代码缺陷，改善自动滞留和缓解异常流量。

### 这与 2020 年 Azure 广告中断有什么关系？

如果你以前听过这个，就打断我。2020 年 9 月也发生了类似的中断(足够有趣)，这也影响了 3 月份的 Azure AD。那为什么当时没有修好呢？

2021 年 3 月的中断部分是由于微软修复了 2020 年 9 月中断的根本原因。工作尚未完成——重大改变需要时间——但它可以防止 3 月份的停机。那么为什么会这样呢？

一个软件错误未能识别“请不要旋转这把钥匙”的标志一个修复在几个小时内就实现了，但是服务清理缓存和旧密钥传播到 Azure 的各个角落需要时间。

* * *

[**获得痛苦的云词典**](https://get.acloudguru.com/cloud-dictionary-of-pain)
说云不一定要努力。我们分析了数以百万计的回复，找出了最容易让人犯错的概念。抓住这个[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)获取一些最痛苦的云术语的简洁定义。

* * *

## 我们如何确保停电不会再次发生？

正如一位智者曾经说过的:“所有的软件总有无限多的未知 bug。”

软件总会有 bug。没有任何云平台能够提供无中断服务。但是我们可以期待更快的恢复和对所发生的事情的透明度——以及为避免将来的问题所做的努力。

就其本身而言，微软正在采取措施减少未来的中断，[写道](https://status.azure.com/en-gb/status/history/):

> *“Azure AD 正在分多个阶段努力对后端安全部署流程(SDP)系统应用额外的保护，以防止包括此问题在内的一类风险。。。我们理解这一事件的不可思议的影响和不可接受性，并深表歉意。我们正在不断采取措施来改进 Microsoft Azure 平台和我们的流程，以帮助确保此类事件不会在未来发生。”*

## 云中断的频率有多高？

如此成熟的平台应该有数百万个捕捉 bug 的功能和设施，但现在我们来了。这种中断*不应该发生，对吗？*

对云来说，有*种方式*比缺点更有[的好处，但是中断可能会发生。](https://acloudguru.com/blog/business/what-is-cloud-migration#cloudbenefits)

亚马逊网络服务(AWS)和谷歌云(GCP)最近也出现了宕机，所以这是我们在一定程度上必须预料到的事情。2020 年 11 月的 AWS 中断影响了从 Adobe 到 Roku 的网站和服务，2019 年 6 月的 GCP 中断影响了 YouTube、G-Suite 和 Snapchat。

* * *

## 提升您的云计算职业生涯

无论您是云新手还是经验丰富的专家，云专家都能让您轻松(而且非常棒)地获得认证并掌握现代技术技能。查看 [ACG 目前的免费课程](https://acloudguru.com/blog/news/whats-free-at-acg-april-2021)或[立即开始](https://acloudguru.com/pricing)免费试用。