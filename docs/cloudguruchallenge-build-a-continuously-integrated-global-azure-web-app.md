# #CloudGuruChallenge:构建持续集成的全球 Azure 应用|云专家

> 原文：<https://acloudguru.com/blog/engineering/cloudguruchallenge-build-a-continuously-integrated-global-azure-web-app>

| **挑战主题** : Azure 管道和持续集成 |
| **作者**:拉尔斯·克林 |
| **目标**:创建一个 web 应用程序，该应用程序在发生变化时持续集成，具有全局性能，并增加了对在线攻击的防护。 |
| **成果**:获得适用于现实场景的 Azure App 服务和 DevOps 技能，包括 ARM 模板和 YAML。创建一个安全快速的全球可伸缩的 web 应用程序。 |
| 截止日期:2021 年 3 月 31 日 |

### 背景

大多数互联网中断都是由被实时推送的破损或有错误的代码造成的。你可能听说过这句口头禅“永远不要在星期五部署！”

这背后的想法是，你部署你的新应用程序，然后回家，在这之后，没有人会在周末的几天里修复这些问题。在我看来，你应该能够在你喜欢的任何时候进行部署。如果不能，那么你的流程就坏了。

像谷歌和网飞这样的公司经常在你没有注意到的情况下，每天为不同的产品部署几次代码。DevOps 的应用程序和产品管理方法几乎强制执行新功能、错误修复和代码的即时和持续推送。

为一个补丁或功能等待数月的日子已经一去不复返了。或者他们应该是。据估计，2020 年 [60%的公司每天部署多次、每天一次或每隔几天一次](https://www.helpnetsecurity.com/2020/05/20/devops-software-development-teams/)。这意味着 40%的人不是——这对企业、员工和客户都不利。

成熟稳定的部署渠道的主要优势是:

*   确保更快、更安全地发布软件
*   降低维护成本
*   加快应用和功能的上市时间
*   提高团队的灵活性和敏捷性
*   给创新留出更多时间

* * *

* * *

### 挑战

快速发展的安全公司 Cloud Save 需要一个验证应用程序，用于其不断增长的安全产品套件。他们要求你建立一个应用程序，可以捕捉用户的姓名、地址、照片和声音样本。这是一系列支持工具的第一步，这些工具将使用 web 浏览器与用户进行交互。

该应用程序有望在全球获得成功，因此需要在边缘加速，并使用负载平衡来确保用户体验。还应该考虑应用程序的安全性和对攻击的防御。

Cloud Save 计划快速扩展您的工作，因此他们还需要您确保任何更改、错误修复和更新都可以立即自动测试和部署。您将实施持续集成和可选的持续部署，这是现代企业的一项重要云技能，无疑会在您的简历中脱颖而出。

说够了。让我们开始挑战吧！

*用 ACG 系列跟上微软 Azure 的一切 [Azure 本周](https://www.youtube.com/playlist?list=PLI1_CQcV71RmnrRBgJNlI1yY_WiOWIXov)！*

### 先决条件

### 挑战步骤

正如我们在 ACG 的其他[云专家挑战](https://acloudguru.com/blog/tag/cloudguruchallenge)一样，这个挑战也有多个正确答案。我不会告诉你如何执行下面的步骤，而是告诉你我想要的结果。你以你认为最好的方式做它。使用 Bing 随意搜索你需要的任何东西，询问你的朋友和同事，使用 Twitter，或者做你在实际工作项目中可能做的任何事情。

首先，请查看我们的 [AZ-900 微软 Azure 基础课程](https://acloudguru.com/course/az-900-microsoft-azure-fundamentals)。它在二月份(以及其他几门 Azure 相关的课程)在[是免费的，它将为你进入微软 Azure 工作打下坚实的基础。](https://acloudguru.com/blog/news/whats-free-at-acg-january-and-february-2021)

面临的挑战是创建一个可伸缩的、健壮的 web 应用程序，以及一个稳定的应用程序部署管道。这个挑战将让你在 Azure 管道、应用服务、Azure 前门、Cosmos DB、ARM 模板和 YAML 配置方面获得现实世界的技能。

![](img/6ca6bcf8bb08607d85576ea05dcf839f.png)

1.  使用 ARM 模板，创建一个具有以下属性的新 Azure 应用服务。
    *   与名为“ACGVnet”的 Azure 虚拟网络集成
    *   添加名为“staging”的部署插槽
    *   使用 1–3 个实例进行自定义自动缩放，默认为 1。
    *   在 CPU 使用率达到 70%时触发扩展操作的扩展规则。

2.  使用微软的 [Azure 快速启动模板](https://acloudguru.com/hands-on-labs/deploy-a-github-quickstart-arm-template-using-the-azure-portal)，创建一个 Azure 前台服务。
    *   将步骤 1 中创建的应用服务添加为后端
    *   对应用服务的所有请求必须是 HTTPS
    *   (可选)添加路由规则以控制流量和多个后端。

3.  使用 ARM 模板，创建一个 Cosmos DB 实例。
    *   如果可能的话，使用 Cosmos DB 免费实例(每个订阅只能有一个)。
    *   启用地理冗余
    *   API 类型应该是核心(SQL)

4.  创建一个简单的 web 应用程序，并使用 GitHub 作为源代码控制。
    *   应用程序必须至少有一个测试。
    *   应用程序必须用 ASP.NET、ASP.NET 核心、Java、Ruby、Node.js、PHP 或 Python 编写。
    *   用户数据必须存储在 Cosmos DB 中(您可以使用免费层)。
    *   照片和语音样本可以存储在 Cosmos DB 或 Azure Blob 存储中。

5.  使用 YAML 在 Azure DevOps 中创建包含以下组件的管道。
    *   它应该构建 web 应用程序
    *   如果构建成功，运行测试。
    *   如果测试通过，将应用程序部署到步骤 1 中创建的 Azure App 服务的“staging”部署槽。

6.  (可选)在 DevOps 的 YAML 中创建一个步骤，该步骤交换应用程序服务的生产和暂存部署槽。

### 当你完成的时候

你可以自己或与他人合作完成项目要求。欢迎在[论坛](https://acloud.guru/forums/cloud-guru-challenge/recent?p=1&opt_id=oeu1596472190462r0.43263125574439387&_ga=2.34776743.782125425.1612133956-1810528525.1603168127)或社交媒体上使用#CloudGuruChallenge 标签提问！

当你完成了项目的所有步骤后，在[指定论坛](https://acloud.guru/forums/cloud-guru-challenge/recent?p=1)线程中发布一个你的博文的链接。然后，我将能够在 LinkedIn 上为你在这个项目中展示的技能背书:Azure 应用服务、Azure DevOps、持续集成、Azure 前门、负载平衡、安全。(您还将有机会赢得一些超酷的奖品！)

这项挑战将无限期开放，但要在 LinkedIn 上获得支持并赢得奖品，你需要在 2021 年 3 月 31 日之前在论坛上链接你的博客帖子。

最重要的是，#CloudGuruChallenge 是免费的，任何人都可以使用:你只需要一个 [ACG 免费会员](https://acloudguru.com/pricing)就可以在论坛上发帖。

* * *

## 想提升你的蓝色力量吗？

ACG 的微软 Azure 实践学习可以帮助你从一个 Azure 业余爱好者变成微软云计算的大师。二月份，我们有一批特别的[免费 Azure 相关课程](https://acloudguru.com/blog/news/whats-free-at-acg-january-and-february-2021)。吃吧！