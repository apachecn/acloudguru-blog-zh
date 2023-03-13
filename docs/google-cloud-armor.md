# 谷歌云甲是做什么的？

> 原文：<https://acloudguru.com/blog/engineering/google-cloud-armor>

Web 应用程序提供了一个购物、游戏、流式内容、理财等等的地方。组织[保护其最重要和最有利可图的应用程序的机密性、完整性和可用性至关重要](https://www.pluralsight.com/blog/cloud/5-pillars-cloud-security)。

谷歌的回答:谷歌云甲。

## 什么是谷歌云甲？

鉴于这些 web 应用程序的安全风险，谷歌[让其云客户能够使用谷歌云盔甲服务来保护他们的应用程序](https://acloudguru.com/blog/engineering/cloud-apps-secure-by-design)。这种安全服务与云负载平衡相集成，以保护您的后端服务和应用免受分布式拒绝服务(DDoS)流量的影响，这些流量可能会危及这些资产的可用性。GCP 装甲利用谷歌的全球威胁情报馈送和机器学习来识别针对您的谷歌云平台(GCP)资源的 DDoS 流量，并阻止恶意流量。

## 谷歌云甲是做什么的？

Google Cloud Armor 整合了一个 web 应用防火墙(WAF)来保护 web 应用免受 OWASP 十大安全风险列表中列出的许多安全风险的影响。GCP 的客户可以利用 GCP 装甲的 WAF 功能，使用预先配置的 WAF 规则来阻止 web 应用攻击。客户还能够定制 WAF 规则，并根据 IP 来源、HTTP 请求头和其他属性定义过滤流量的条件。

### 最常见的 web 应用程序安全风险是什么？

非营利组织开放 web 应用程序安全项目(OWASP)列出了互联网上一些最臭名昭著的 Web 应用程序安全风险。该列表包括跨站点脚本(XSS)攻击和 SQL 注入(SQLi)攻击，它们可以读取存储在 [SQL 数据库](https://www.pluralsight.com/blog/it-ops/google-cloud-sql)中的机密数据。

在 XSS 攻击中，对手可能会在 web 应用程序中注入恶意代码，或者危害客户端的浏览器。此外，我们不要忘记 DDoS 攻击，这种攻击试图通过用大量流量淹没应用程序来关闭 web 应用程序。

* * *

### 从 GCP 开始，不知道什么认证适合你？

查看[这篇文章](https://acloudguru.com/blog/engineering/which-google-cloud-certification-is-best-for-me)，它介绍了所有最新的 GCP 云认证，它们涵盖了哪些内容，以及你如何利用它们来推进你的职业生涯。

* * *

## 谷歌云甲是免费的吗？

Google Cloud Armor 有两个定价等级:标准和管理保护增强版。

对于标准用户，GCP 装甲是一种按月或按请求付费的服务。WAF 请求是每百万个请求 0.75 美元，WAF 安全策略是每个策略每月 5 美元，WAF 规则是每个规则每月 1 美元。虽然这一层没有时间承诺和数据处理费用，但它不提供任何受保护的资源。

对于托管保护增强版用户，GCP 装甲是一种年度订阅服务，每月起价 3000 美元。订阅中包含的受保护资源超过 100 个，每个资源每月需额外支付 30 美元。虽然所有 WAF 请求、安全政策和规则都包含在此订阅中，但它还收取额外的数据处理费。

* * *

### **刚到 GCP，想了解如何保护谷歌云中的资源和应用程序？**

登录您的 ACG 账户，观看我们的[谷歌云安全介绍](https://learn.acloud.guru/course/b624331f-8c99-49b2-86e9-30301ea9a732/dashboard)课程。本课程将介绍谷歌云盔甲、云防火墙、云身份以及其他保护您的 GCP 资源的基本原则。