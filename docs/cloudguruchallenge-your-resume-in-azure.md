# #CloudGuruChallenge:你在 Azure 的简历|一位云专家

> 原文：<https://acloudguru.com/blog/engineering/cloudguruchallenge-your-resume-in-azure>

*什么是[#云谷挑战](https://acloudguru.com/blog/news/introducing-the-cloudguruchallenge)？点击获取更多信息。*

| **挑战** **话题** | 你在 Azure 的简历！ |
| **挑战** **创造者** | [Gwyneth Pena-follow](https://www.linkedin.com/in/gwyneth-pena) |
| **挑战** **目标** | 创建一个 100% Azure 托管版本的简历。 |
| **挑战** **胜负** | 用 Azure 建立技能(如果你以前用另一种云完成过这个挑战，也可能是多种云)。 |
| **挑战** **截止日期** | 2021 年 5 月 31 日 |

## 挑战

大众需求(我说大众需求是因为我真的想这么做)的背后是[云简历挑战](https://cloudresumechallenge.dev/)。除了这一次，我想看到一些 Azure 提交。

### 先决条件

### 图表

### 挑战步骤

1.  为您的项目创建一个 GitHub 资源库
2.  在您的 GitHub repo 中，创建您的网站:
    *   你的网站需要有你的简历信息。
    *   为此你可以使用 [HTML](https://developer.mozilla.org/en-US/docs/Web/HTML) 和 [CSS](https://www.w3schools.com/css/) 。
    *   它可以像你喜欢的那样时尚或简单，如果你喜欢，你可以使用一个模板，[这里的](https://www.themezy.com/free-website-templates/151-ceevee-free-responsive-website-template)是我用的那个。
    *   [下面是我的一个例子](https://www.gwynethpena.com)。
3.  在您的网站上添加访问者计数器:
4.  将[网站部署到 Azure Blob 存储](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blob-static-website)
5.  启用 HTTPS 和自定义域支持:
6.  设置 GitHub 操作:
    *   任何时候你对你的网站或者你的 API 做了改变，那些改变应该会被自动部署，你可以使用 [GitHub 动作。](https://www.google.com/search?client=firefox-b-1-d&q=get+started+with+github+actions)
    *   如果你对你的 API 进行修改，你的代码应该被测试。您也可以使用 GitHub 操作来实现这一点。这里是关于网络测试的文档，例如。
7.  撰写您的博客文章:
    *   如果你还没有开发者博客，你可以在 [Hashnode](https://hashnode.com/) 上创建一个。
    *   博文的目标是让您记录您的解决方案。我建议您做以下几件事:
        *   你为什么接受挑战？
        *   你是如何完成挑战的？包括截图、图表、代码片段、链接和任何你想要的东西。
        *   最难的部分是什么？
        *   你最喜欢哪一部分？
        *   你最大的收获是什么？
        *   如果您以前使用另一种云解决过这个难题，您会注意到哪些不同？

### **完成后**

你可以自己或与他人合作完成项目要求。欢迎在我们的 [Discord 服务器](https://acloudguru.com/blog/news/join-the-acg-community-on-discord)中提问 [](https://acloud.guru/forums/cloud-guru-challenge/recent?p=1&opt_id=oeu1596472190462r0.43263125574439387) (有一个专门的挑战频道)或者在社交媒体上使用 [#CloudGuruChallenge](https://twitter.com/search?q=%23cloudguruchallenge) 标签提问！

当你完成项目的所有步骤后，在指定的 [](https://acloud.guru/forums/cloud-guru-challenge/recent?p=1&opt_id=oeu1596472190462r0.43263125574439387) Discord 频道发布你的博文链接和你的 LinkedIn 个人资料链接。然后，我将能够在 LinkedIn 上为你在这个项目中展示的技能背书:Azure、CI/CD 和你为 API 选择的编程语言。

挑战结束后，你还将有机会赢得一些超酷的奖品，并获得一个来自云专家 LinkedIn 账户的特别大喊！

这项挑战将无限期开放，但要想在 LinkedIn 上获得支持、赢得奖品并在 LinkedIn 上大声喊出来，您需要在 5 月 31 日之前**提交您对 Discord 的挑战。**

最重要的是，#CloudGuruChallenge 是免费的，每个人都可以使用！

### **资源**

准备好做一些谷歌搜索，但如果你是 ACG 会员，这里有一些资源可以帮助你更好地使用 **Azure Functions 和 Azure CosmosDB:**

如果您还不是 ACG 会员，我们鼓励您注册一个免费帐户(不需要信用卡)来开始学习和探索每月轮换的免费课程。

你不需要执行这些额外的步骤来在挑战中“宣布胜利”，但是它们*将*帮助你的项目脱颖而出，并提供令人敬畏的额外学习。

*   使用 [Azure CLI](https://acloudguru.com/course/azure-cli-essentials) :这可能是你使用 Azure 的第一个项目，所以如果你通过 UI 创建资源，我会给你一个通行证。然而，这是[熟悉 Azure CLI](https://docs.microsoft.com/en-us/cli/azure/get-started-with-azure-cli) 的绝佳机会
*   作为代码的基础设施:Azure CLI 非常适合动态创建资源和进行试验，但是在现实生活的生产场景中，您可能希望将基础设施定义为代码。[创建一个 Azure 资源管理器模板](https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/template-tutorial-create-first-template?tabs=azure-powershell)来定义你的后端基础设施。

### **最终收获**

我知道有些服务捆绑了你必须放在一起的许多功能，例如 [Azure Static Web Apps](https://docs.microsoft.com/en-us/azure/static-web-apps/overview) 建立了一个静态网站，有 HTTPS、Azure Functions 后端、GitHub 操作和自定义域支持——它只需几下点击就能为你完成所有工作。但是你自己把这些拼凑起来还是很有价值的。此外，如果您已经在另一个云环境中完成了这项工作，您将获得另一个平台的大量信息，这是另一个很好的优势。

熬过这一关，你不仅会有一个很棒的项目添加到你的简历中展示给招聘经理，你还能解释整个基础设施。

祝你好运。我们走吧！

* * *

## 获得更好职业所需的技能。

掌握现代技术技能，获得认证，提升您的职业生涯。无论您是新手还是经验丰富的专业人士，您都可以通过实践来学习，并在 ACG 的帮助下推进您的云计算职业生涯。