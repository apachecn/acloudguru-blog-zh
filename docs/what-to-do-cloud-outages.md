# 云崩溃时要采取的 5 个步骤|云专家

> 原文：<https://acloudguru.com/blog/engineering/what-to-do-cloud-outages>

假设你是一名为一家大公司工作的云工程师，你负责维护网站的正常运行。您已经尽了最大努力来确保故障转移、高可用性等方面的冗余。你正在享用周一的晚餐，突然你得到一个警告，说网站关闭了。呀！

您匆忙进行调查，并了解到停机不是由您造成的(咻！).这是由于云提供商的认证机制失败，并且您不确定这种中断会持续多长时间。你需要让网站尽快上线，但是你具体能做些什么呢？

在本文中，我们将讨论当云关闭时你可以做什么(除了*恐慌*)。

## 云服务宕机的主要原因是什么？

云故障[可能并且将会发生](https://techgenix.com/7-biggest-cloud-outages-services-2021/)，这就是为什么提供商提供 99%到 99.99%的正常运行时间，而不是 100%。据[正常运行时间研究所](https://uptimeinstitute.com/publications/asset/annual-outage-analysis-2021)称，停机的主要原因是软件或配置错误。其他常见原因是网络或连接问题，以及数据中心的机械或电气故障。

当软件或配置错误导致云宕机时，问题可能包括糟糕的部署包、应用程序的错误配置等等。这种导致云服务中断的例子发生在 2022 年 2 月[日的 Slack](https://status.slack.com/2022-02-22) ，当时一个数据库的配置更改导致了大约三个小时的大范围中断。

网络和连接是云的维系方式，因此中断会导致各种各样的问题。在这一类别中，最常见的故障类型与配置有关(您是否注意到了一种趋势？)、变更管理和第三方网络提供商错误。

如果我们在 Google Cloud 上查看从【2022 年 1 月的一次中断，我们可以看到一个配置错误导致了几个小时的延迟增加，其中“检查点数据错误地丢失了一条特定的配置信息；这传播到了大约 15%为 us-west1-b 服务的网络交换机。”

在机械或电气故障方面，大多数断电是由不间断电源故障或公用设施或发电机故障引起的。从 2022 年 7 月开始的 [AWS 断电事件来看，可用性区域的断电导致了大约两个小时的大面积断电。](https://metrist.io/blog/aws-us-east-2-outage-analysis-july-28th-2022/)

## 当云消失时会发生什么？

正如我们在介绍场景中看到的那样，当云崩溃时，对于我们这些终端用户来说，这很少是美好或有趣的！这通常会导致压力、焦虑和疯狂地去解决问题，或者寻找备用解决方案或替代方案。

在最好的情况下，我们的网站只会关闭几分钟，并且只会影响一小部分用户。然而，如果我们考虑最坏的情况，我们的网站可能会关闭几天，这将影响我们所有的客户使用我们的网站。这不仅会使我们因网站崩溃而丢失数据，还会损害我们的声誉，损失我们的生意，等等。

Ponemon Institute 在 2015 年[进行了一项研究，确定平均每分钟停机的成本接近 9000 美元。由](https://www.vertiv.com/globalassets/documents/reports/2016-cost-of-data-center-outages-11-11_51190_1.pdf)[正常运行时间研究所](https://uptimeinstitute.com/publications/asset/annual-outage-analysis-2021)最近进行的一项研究发现，他们调查的组织中有超过一半的组织表示，最近的一次停机造成的损失超过了 10 万美元！

## 案例分析:2021 年自动气象站大规模停电

在这篇博客的前面，我们已经看到了一些小规模的中断，但是现在让我们来看看最近的一次大规模中断。

2021 年 12 月一个寒冷的早晨，发生了一次影响多项服务的大规模自动气象站服务中断。从美国东部时间上午 10:30 到大约晚上 9:40(为了全面恢复服务)，包括 API Gateway、Fargate、EventBridge 和 EC2 实例在内的一些服务受到了影响。这导致了一些企业和许多亚马逊服务的大范围中断。[人们不能点披萨](https://www.reddit.com/r/aws/comments/rb1xrd/comment/hnmnz1y/)，甚至 [AWS 自己的服务健康仪表板也瘫痪了](https://aws.amazon.com/message/12721/)。

那么是什么导致了这一切混乱？

简而言之，亚马逊“us-east-1”地区(北弗吉尼亚州)的一个自动化系统试图扩大在 AWS 内部网络上运行的内部服务。不幸的是，这个自动化过程存在一个问题，它使网络流量泛滥，基本上导致了无意的分布式拒绝服务(或 DDoS 攻击)。

为了解决这个问题，亚马逊工程师首先试图将 DNS 流量从拥堵的路径上移走。虽然这似乎有助于解决问题，但它不是解决办法。接下来，他们禁用了 EventBridge 的事件传递，以帮助减少受影响的网络设备上的负载。在这一点上，拥塞开始改善，不久，AWS 运营商报告说，“所有网络设备在太平洋标准时间下午 2 点 22 分完全恢复。”然而，一些服务仍然需要一段时间才能完全稳定，即 API Gateway、Fargate 和 EventBridge。

对于任何停机或 IT 问题，它都应该为将来提供一些经验教训。对于 AWS 团队来说，他们决心修复自动化流程错误，并在这样的停机期间改善与客户的沟通。如果你想了解更多关于 AWS 服务中断的信息，请查看 Mattias Andersson 在 ACG 的博客文章。

## 云消失时要采取的 5 个步骤

现在我们已经看到了云中断的影响和后果，您应该如何为下一次中断做准备呢？让我们来看一下当云消失时你可以采取的五个步骤。

### 1.在云中断之前:考虑一个多云策略

首先，在停机发生之前，需要考虑的是针对您的环境的多云策略。现在，这种方法有几个利弊取决于您的环境、架构和团队，多云战略可能是一种负担，而不是一种好处。

你可以考虑的另一个选择是利用[多个区域](https://acloudguru.com/blog/engineering/why-and-how-do-we-build-a-multi-region-active-active-architecture)和你的首选云提供商。这为您提供了更高的冗余性，并提供了针对区域性中断的保护，而无需承担拥有多个云提供商的所有负担。

### 2.云中断前:备份重要数据

其次，在停机发生之前，您应该确保备份您的重要数据。

*   如果你使用 Azure， [Azure Backup](https://learn.microsoft.com/en-us/azure/backup/backup-overview) 是一个将备份你的虚拟机、SQL 服务器、Azure Blobs 等上的数据的解决方案。
*   在 AWS 方面，您可以使用 [AWS 备份](https://aws.amazon.com/backup/)，它支持 RDS 服务、EC2 实例等等。
*   有了 GCP，[谷歌云备份和灾难恢复](https://cloud.google.com/solutions/backup-dr)将通过备份您在 GKE、虚拟机和更多其他地方的数据来保护您。

如果您在停机前备份了所有重要数据，那么如果由于停机导致数据丢失或者停机持续数小时或数天，您将能够恢复这些数据。

### 3.首先检查用户错误

对于我们的第三步，我们可以看看发生中断后该做什么。在这一点上，最好的办法是确定这个问题是否只是你的问题。

*   排除互联网或连接问题的最快方法是前往 [Down Detector](https://downdetector.com/) 并输入网站的 URL。Down Detector 将让您知道是否有任何其他用户报告错误，以及是否有大范围的中断。它们还包括网站支持页面、twitter 或 facebook(如果有)的有用链接。

*   另一个有用的工具是[IsItDownRightNow.com](https://www.isitdownrightnow.com/)，它可以快速检查一个网站是否宕机，并帮助你排除本地连接问题。是否立即关闭将帮助您确定您正在检查的站点是否可用，以及该站点的响应时间。

如果这些检测器没有发现任何问题，您可以查看您的云提供商的状态页面。例如，要检查谷歌云的状态，你可以前往他们的[状态页面](https://status.cloud.google.com/)，该页面将显示他们是否有任何服务问题或服务降级。这些状态页面有时会包含有关问题的更新、问题解决的时间以及正在采取哪些步骤来解决问题。

如果你这边的网络完全瘫痪或者停电了，你可以去当地的咖啡店，使用他们的 wifi，看看提供商是否真的停电了。一旦您排除了任何局部问题，我们就可以进入列表中的下一步。

### 4.联系您的云提供商

在我们排除了任何本地连接问题之后，我们可以继续联系云提供商，以获得关于中断的更多信息。请准备好提供有关您遇到的问题的具体信息，包括受影响的服务、任何错误消息以及问题开始的时间。

每个提供商都有不同的联系支持的方法和多种联系方式:

*   对于 Azure，你可以使用 Azure 门户或者在 Twitter 上发布 Azure 支持的消息[。后者特别有助于获得快速响应。](https://twitter.com/intent/tweet?text=@azuresupport+%23azhelp:)
*   有了 AWS，你可以使用 AWS [支持页面](https://aws.amazon.com/contact-us/)或者在 Twitter 上发推文 [AWS 支持](https://twitter.com/AWSSupport)。
*   谷歌云让你可以选择使用他们的支持页面。
*   如果您没有使用三大云提供商之一，那么找到支持信息的最简单方法是在提供商网站上，或者使用 [Down Detector](https://downdetector.com/) 和提供商网站，这些网站通常会有该提供商支持网站的链接。

一旦你联系了供应商，请记住要有耐心。在停机期间，提供商支持团队正在努力帮助客户并回答问题，因此可能需要一点时间才能做出响应。

### 5.检查您的云服务协议

最后，你需要检查你的提供商的云服务协议。审查您的协议对于了解提供商的义务和您作为客户的权利非常重要。

首先，您需要检查您的服务水平协议(SLA)。SLA 是提供商对保持一定可用性级别的承诺。例如，如果您正在使用 AWS，并且您的 API 网关服务受到影响，AWS 为 API 网关服务提供了[三个级别的 SLA。根据该服务在特定月份经历的停机时间，您将有权获得部分或全部退款。](https://aws.amazon.com/legal/service-level-agreements/?aws-sla-cards.sort-by=item.additionalFields.serviceNameLower&aws-sla-cards.sort-order=asc&awsf.tech-category-filter=*all&aws-sla-cards.q=api%2Bgateway&aws-sla-cards.q_operator=AND)

假设 API 网关服务在本月早些时候中断了三个小时，这相当于 99.58%的正常运行时间。根据 AWS 提供的 [SLA，您将有权获得 10%的服务积分。因此，请确保您正在审查您的云服务协议！](https://aws.amazon.com/legal/service-level-agreements/?aws-sla-cards.sort-by=item.additionalFields.serviceNameLower&aws-sla-cards.sort-order=asc&awsf.tech-category-filter=*all&aws-sla-cards.q=api%2Bgateway&aws-sla-cards.q_operator=AND)

## 制定多云策略来保护您的数据

对于依赖云服务来执行日常活动或运营业务的任何人来说，云中断都会令人沮丧。通过遵循本文中的步骤和资源，您将为停机做好更好的准备。然而，正如我们所看到的，云中断随时都可能发生。

为了保护您的业务免受中断的影响，您应该确定是否可以设计您的应用程序或服务以主动-主动方式或主动-被动方式从[多个区域](https://acloudguru.com/blog/engineering/why-and-how-do-we-build-a-multi-region-active-active-architecture)运行，当出现问题时，您可以故障转移到另一个区域。

如果您仍然担心单一云提供商的停机时间，下一步是开发一个多云策略来保护您的数据。您将需要确保拥有合适的人员和流程来成功实施这一战略，我们建议您回顾一下采用云计算的利弊。