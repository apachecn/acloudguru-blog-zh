# Azure SQL 超大规模、站点恢复和流量管理器获得更新|云专家

> 原文：<https://acloudguru.com/blog/engineering/azure-sql-hyperscale-site-recovery-and-traffic-manager-get-updates>

本周 Azure 有什么新消息？这里有五个更新，包括 Azure SQL 超大规模自动故障转移组，Azure 站点恢复的 Azure 策略支持，Azure 流量管理器中为端点监控添加了额外的 IP 地址，Azure Cognitive Services 的新语义搜索功能，以及一些有用的 Azure IoT Central 更新。让我们开始吧！

* * *

## 蔚蓝你的事业成功

[从 ACG 开始](https://acloudguru.com/pricing)通过微软 Azure、AWS、谷歌云等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## 1.Azure SQL 超大规模的自动故障转移组现已在预览中

Azure SQL 中的超大规模服务层不仅是一个很酷的名字，而且在快速横向扩展和纵向扩展、支持高达 100TB 的大型数据库、几乎即时的备份和非常快速的恢复方面，它也是 Azure SQL 的顶级层。这就像数据库世界的超级跑车。一辆巴士大小的超级跑车？

总之，本周，超大规模的自动故障转移组在预览版中发布。自动故障转移组的一些好处包括

*   简化了一组地理复制数据库的管理，包括对整个数据库组进行故障切换的能力。
*   故障切换后，应用程序能够保持相同的读/写和只读端点。
*   通过地理故障切换在整个区域丢失期间进行恢复，这可以手动启动，也可以通过自动故障切换策略启动。
*   可读在线辅助节点可用于只读工作负载，方法是连接在地理故障切换期间保持不变的只读侦听器端点。

相当整洁！你可以在这里阅读更多相关信息[。](https://techcommunity.microsoft.com/t5/azure-sql-blog/auto-failover-groups-for-azure-sql-hyperscale-now-in-preview/ba-p/3052119)

## 2.Azure 站点恢复的 Azure 策略支持正式发布

Azure Site Recovery 的政策支持现已全面推出。一旦为给定订阅或资源组创建了灾难恢复策略，添加到该订阅或资源组的所有新虚拟机都将自动启用 Azure Site Recovery。

这有助于遵守公司政策，但不要忘记，您需要为启用的每个 ASR 付费。可能会很贵。

点击阅读更多[。](https://azure.microsoft.com/en-au/updates/asr-policy-support-ga/)

## 3.Azure 流量管理器:端点监控服务的附加 IP 地址

如果您曾经使用过 Traffic Manager，您可能知道它有一个端点监控服务，用于评估流量被定向到的端点。这是为了确保流量不会被定向到中断的端点，从而保持您的应用程序健康。

为了确保探测器的容量跟随 Traffic Manager 的增长，Azure 将在未来几年增加部署在 Traffic Manager 端点监控服务中的探测器数量。您需要监控探头的 IP 地址列表，以确保您允许它们与您的流量管理器一起工作。

更多[此处](https://azure.microsoft.com/en-au/updates/azure-traffic-manager-additional-ip-addresses-for-endpoint-monitoring-service/)。

## 4.公共预览:语义搜索更新

语义搜索现在处于公开预览阶段，这意味着你可以在 Azure 门户中轻按一下开关来启用它。

什么是语义搜索？它是 Azure Cognitive Services 的新功能，可以理解用户意图，并根据上下文对最相关的搜索结果进行排序。

今天跟它玩一玩[这里](https://azure.microsoft.com/en-au/updates/semantic-search-public-preview-update/)。只是不要再搜索羊驼彩虹了。你知道上次发生了什么。。。

## 5.Azure 物联网中央更新

最后，Azure IoT Central 有一些小的更新:

*   在 Azure IoT Central Dashboard 上的单个磁贴上可以显示的设备限制为 10 到 100 个。

*   我想，您现在可以复制物联网仪表盘，以大幅增加仪表盘的数量。

*   此外，您现在可以发送不同形状的设备遥测数据，并在 Azure IoT Central ingress 将遥测数据转换为结构化数据。

如果你做物联网中心的事情，你现在有更多的更新可以玩。点击查看[。](https://azure.microsoft.com/en-au/updates/copydashboardsiniotcentral/)

## 希望在 2022 年提升您的云游戏水平？加入我们 1 月 18 日的直播！

美国东部时间 1 月 18 日下午 3:30(澳大利亚东部时间 1 月 19 日上午 7:30)，Scott "Omnibus" Pletcher 和 Mattias " the Certification Ninja " Andersson 将在 [Youtube](https://youtu.be/B8-qDoiadPM) 上直播，为您提供如何开始云计算之旅的一些建议。带着你的问题，我们会带着答案。还有零食！(不过只是对我们来说。我们会分享，但是，你知道，这是互联网。)

想要跟上所有的事情 Azure 和 cloud？在 YouTube 上订阅一位云专家的每周微软 Azure 新闻(以及其他云提供商的新闻)。你也可以在[脸书](https://www.facebook.com/acloudguru)上喜欢我们，在[推特](https://twitter.com/acloudguru)上关注我们，或者在 [Discord](http://discord.gg/acloudguru) 上加入对话。

云挑战:Lars vs AWS

* * *

### 当热爱 Azure 的 Lars 前往黑暗面并尝试 AWS 任务时会发生什么？我们向 Lars 挑战，让他在云平台上走过(或绊倒)一个他从未见过的场景，他也不知道要找出答案。

What happens when Azure-loving Lars goes to the dark side and tries his hand at AWS tasks? We [challenged Lars](https://youtu.be/GczeRU79-4s?t=585) to walk (or stumble) through a scenario he’d never seen on a cloud platform he didn’t know to find out.