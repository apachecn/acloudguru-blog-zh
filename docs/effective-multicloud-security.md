# 有效的多云安全解决方案的 4 个关键步骤|云专家

> 原文：<https://acloudguru.com/blog/engineering/effective-multicloud-security>

***更新于:***2023 年 3 月 2 日

在本文中，我们分享了四个关键步骤，您可以采取这些步骤来帮助提高云环境的可见性，并成功实施多云安全解决方案。

* * *

**通往更好职业的钥匙**

[立即开始 ACG](https://acloudguru.com/pricing) 通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室来改变你的职业生涯。

* * *

## 采取措施实现多云安全

众所周知，企业正在脱离传统的内部数据中心，并[迁移到多云框架](https://acloudguru.com/blog/business/what-is-cloud-migration)以提高其灵活性、效率和安全性。但有一点你可能没有意识到，多云策略可能会带来一系列的复杂性。

多云环境使用多个公共云。这意味着应用程序和操作流程可以在所有环境中一致地运行。

所以这应该可以最小化风险，不是吗？首先，每个云提供商都有自己的安全协议和管理控制台。这可能会给组织的整体安全状况带来混乱和不一致。它还会导致[阴影笼罩它](https://www.forcepoint.com/cyber-edu/shadow-it)。这是在 IT 部门不知情或未批准的情况下使用未经授权的云服务的地方。

此外，多云部署策略可以增加您组织的攻击面。这是因为每个云提供商都有自己的漏洞可以被利用。如果一个提供商被攻破，黑客可以通过[凭证填充](https://acloudguru.com/blog/engineering/protecting-yourself-against-credential-stuffing)访问你的其他云账户。

## 如何保护多云环境？

根据您正在构建的多云解决方案的类型(不同的应用程序存储在不同的云中，或者数据在多个云中存储和处理)，您的多云安全解决方案看起来会非常不同。

当数据包含在多个云提供商的单个应用程序中时，构建多云安全解决方案会更简单。需要保护的终端更少，数据传输不那么频繁，应用程序(以及这些应用程序所在的提供商)具有本机安全功能，您的数据永远不会传输到外部。您仍然必须确保每个应用程序和每个云的安全特性都是存在的、有效的、准确的。但是风险更小。

在数据频繁地在云提供商之间移动的情况下，保护多云解决方案是可能的，只是需要更多的努力。你必须:

*   保护您的解决方案、开发这些解决方案的云环境以及从一个迁移到另一个的数据
*   跨所有云管理不同的身份验证、授权、监控和存储服务
*   确保您的所有云环境都受到类似的保护

## 构建多云安全解决方案的 4 个步骤

无论您构建什么样的多云解决方案，都可以采取四个关键步骤来保护您的多云设置。

### 1.将多云安全集成到开发运维中

多年来，DevOps 一直是软件开发和部署的首选方法。但是就像任何成为主流的东西一样，它也有相当多的批评者。最常见的批评之一是 DevOps 过于强调速度和敏捷性，而对安全性重视不够。

这是一个合理的担忧。毕竟，在当今这个网络威胁不断的世界，安全应该是任何组织的首要任务，无论是哪个行业。

但是没有必要在安全性和速度之间做出选择——你可以两者兼得。将安全性集成到您的 DevOps 流程中，可以让您创建一个快速、安全的开发管道，保护您的应用程序和数据。

这里有两个提示可以帮助你开始。

#### 从一开始就实现 DevSecOps

如果您想在 DevOps 流程中构建安全性，您需要从头开始。这意味着将安全性融入开发生命周期的每个阶段，从规划和设计到测试和部署。这可能是一个挑战，但是如果您想要创建一个安全的开发过程，这是必不可少的。

#### 使用自动化和流程编排

自动化是 DevOps 的关键支柱之一，对于安全性也至关重要。通过[自动化安全任务](https://www.cioinsight.com/blogs/7-security-tasks-to-automate-to-match-cybersecurity-threats/)，您可以保持开发和操作过程的速度，并确保您的安全得到保障。

### 2.购买主密钥(BYOK)

当涉及到保护您的多云设置时，主密钥被称为圣杯。通过购买主密钥，您实际上是为您的数据购买了一份保险。

主密钥也称为自带密钥(BYOK)，是一种内部安全密钥，组织可以使用它来加密云中的数据。

大多数公司依赖公共云服务提供商提供的安全性，如 AWS、Azure 和 Google Cloud。主密钥为您的数据增加了一层额外的安全保护，有助于防止数据泄露。

您可以使用自己的主密钥，也可以导入一个主密钥，由云提供商放在他们的密钥管理系统(KMS)中。云 KMS 使用您的主密钥对数据加密密钥(dek)进行加密，然后将其保存到云中以获得额外的安全级别。您也可以将您的主密钥存储在云外 KMS 中。

* * *

[![Download the "Road to multicloud" white paper for more info on multicloud strategies](img/56c52338a4dfd0d67fa54fd8faa3e050.png)](https://www.pluralsight.com/landing-pages/resource/gate/road-to-multicloud-g)

Curious about multicloud? Check out *The Road to Multicloud* ebook for more on the pitfalls and obstacles to avoid when developing a multicloud strategy.

* * *

### 3.将监控融合到一个地方

另一种保护多云设置的方法是在一个地方监控所有内容。

将 [Stackify](https://stackify.com/) 或[亚马逊 CloudWatch](https://aws.amazon.com/cloudwatch/) 等监控工具集成到一个平台中，可以让您清楚地了解系统的性能，并快速发现问题。从日志到警报和事件，系统健康状况的完整视图有助于防止停机并保持应用程序平稳运行，同时提供对潜在安全问题的洞察。

通过将监控工具融合到一个平台中，您可以更全面地了解系统性能，并快速识别出现的任何安全问题。您可以深入了解以下情况:

*   实现并保持理想的应用性能
*   提高网络和应用安全性
*   由于快速解决问题和快速报告问题，优化了服务的可用性
*   简化连续性计划的实施，实现主动风险补救
*   不同设备上的可用性
*   云活动增加时的简单扩展
*   由于对架构的全面了解，减少了意外的云成本泄露

### 4.通过限制用户访问来提高云安全性

谈到数据安全，企业通常会忘记关注内部。但这很重要，因为问题可能首先出在那些有权访问你的基于云的系统和数据的人身上。

通过减少能够访问敏感数据的人数，您可以显著改善您的云安全状况。仔细考虑哪些用户应该有权访问系统的哪些部分，以便在发生违规时限制潜在的损害。

根据威瑞森 2021 年的一项研究，22%的网络攻击是内部人员发起的。因此，尽管看起来威胁总是来自外部，但有时最大的安全威胁离我们家更近。

这就是为什么区块链/加密存储数据保存在一个分散的网络中，然后存储在一个数字钱包中，该钱包通过加密的数字代码存储资产。这降低了加密购买者之间的信任度。同样的意识形态可以——也应该——适用于有权访问你的云数据的人。访问的人越少，敏感信息泄露的可能性就越小。

如果你想提高这方面的技能，可以看看我们的[安全课程](https://acloudguru.com/training-library/security-training)。如果你对多云导航感兴趣，并想亲自动手，请查看我们下面的视频挑战。

* * *

Nahla Davies 是一名软件开发人员和科技作家。在全职从事技术写作之前，她设法在一家拥有 5000 家公司的体验式品牌机构担任首席程序员，该机构的客户包括三星、时代华纳、网飞和索尼。