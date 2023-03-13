# Azure SQL 数据库区域全部冗余！

> 原文：<https://acloudguru.com/blog/engineering/azure-sql-database-zone-redundancy-for-all>

本周蓝色新闻发生了什么？我们看一下 Azure SQL 数据库的冗余和 Azure 静态 Web 应用的 DevOps 改进。我们还查看了 Azure Monitor 代理的最新更改和增强。

开发运维、监控和冗余——我最喜欢的三个话题！让我们开始吧。

* * *

**加速您的 Azure 职业生涯**

无论你是新手还是认证专家，云专家都能让你轻松(也很棒)地提升自己的职业生涯。查看 [ACG 的免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)或[现在就开始](https://acloudguru.com/pricing)免费试用。

* * *

## 【Azure SQL 数据库通用层的区域冗余

微软[最近宣布](https://techcommunity.microsoft.com/t5/azure-sql-blog/zone-redundancy-for-azure-sql-database-general-purpose-tier/ba-p/3280376)你现在可以在通用服务层配置你的 Azure SQL 数据库以实现区域冗余。

这在以前只保留给成本较高的业务层和关键层。

区域冗余保护您的数据库免受更大范围的 Azure 故障，包括数据中心停机，并因此将微软提供的 SLA 提高到 99.995%。而且，由于您在同一区域使用分区，您仍然可以获得零恢复点目标(RPO)。这意味着在发生区域故障时不会丢失数据。总是很方便。

您还可以使用门户、ARM 模板 PowerShell 或 Azure CLI 轻松切换到现有数据库上的区域冗余。

值得注意的是，这项服务*将*花费更多一点，目前仅在特定地区提供，其他地区将在预览版中提供。

## **Azure 静态 Web 应用中预览环境的稳定 URLs】**

Azure Static Web Apps 是我最喜欢的新兴 Azure 服务之一。

我说它很有前途，因为它在 Azure 世界中仍是一个婴儿，距离全面上市才一年。它允许您轻松部署全局冗余的 web 前端，也可以轻松集成到 Azure 功能中。

但是 Azure 静态 Web 应用真正伟大的地方是它们与现代 DevOps 工具的集成，如 GitHub 和 Azure DevOps，以持续部署您的更改。

以前，每当您针对生产分支创建一个拉请求时，Azure Static Web apps 都会生成一个预览 URL，以便您可以在合并拉请求之前查看更改。

有了[稳定的网址](https://azure.microsoft.com/en-au/updates/public-preview-stable-urls-for-preview-environments-in-azure-static-web-apps/)，你现在可以永久预览你网站的不同分支。假设您有一个用于持续集成的长期运行的开发分支，您现在可以为该分支永久设置一个 URL。

可爱！

## **Azure Monitor 代理更新**

Azure Monitor Agent 是一个新的代理，您可以将其部署到您的 Azure 虚拟机、规模集和支持 Azure Arc 的服务器，以将日志和指标数据发送到您的日志分析工作区。

以前，这种收集都是使用一些不同的代理完成的，包括日志分析代理。日志分析代理现在的退休日期是 2024 年 8 月。这意味着微软正忙于将所有的日志分析代理功能添加到 Azure Monitor Agent 中。

最新进入公开预览版的特性是[支持基于文本的自定义日志和基于 Windows 的 IIS 日志](https://azure.microsoft.com/en-au/updates/public-preview-azure-monitoring-agent-supports-custom-and-iis-logs/)。

这是对最近添加的对 Windows 10 和 Windows 11 客户端的支持的补充。

我喜欢 Azure Monitor Agent 的地方在于它支持数据收集规则，允许您精确地配置收集哪些日志和指标。您甚至可以将这一职责交给工作负载团队，以分散您的监控配置工作。

所以看看 Azure Monitor 代理，将它与 Log Analytics 代理一起运行，看看它是否支持您的需求。哦，请确保在日志分析代理退出之前完成迁移！

## 跟上所有蓝色的事物

好了，这就是本周的全部内容！想要跟上云的所有事物？在推特上关注 ACG，关注 T2 和脸书。你还可以[在 YouTube 上订阅一位云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的 Azure 每周更新，并在 [Discord](https://discord.gg/zbvhJz66VE) 上加入对话。

想了解更多关于云和 Azure 的信息，或者想在 2022 年开始你的云计算生涯？查看我们每月更新的[免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)的轮换阵容。(不需要信用卡！)