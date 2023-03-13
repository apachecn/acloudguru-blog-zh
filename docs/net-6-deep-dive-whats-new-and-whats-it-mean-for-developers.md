# 。NET 6 deep dive:有什么新特性，对开发者有什么意义？

> 原文：<https://acloudguru.com/blog/engineering/net-6-deep-dive-whats-new-and-whats-it-mean-for-developers>

本周蔚蓝的世界有什么新鲜事？。网 6！它在这里！这是的最大版本。NET 框架，它不仅渗透到 Azure 的每个角落，还渗透到性能、跨平台等等。详情请继续阅读！

## 。云中的 NET 6

我将从[的云部分开始。NET 6](https://devblogs.microsoft.com/dotnet/announcing-net-6/) 以及所有相关公告。先说我最喜欢的(因为是我的博文): [Azure 功能现在在 4.0 版本](https://techcommunity.microsoft.com/t5/apps-on-azure/azure-functions-4-0-and-net-6-support-are-now-generally/ba-p/2933245)，这意味着完全支持。NET 6。

Azure 函数还支持进程内和隔离(进程外)执行模型，这对于像持久函数这样的服务来说是非常关键的。

* * *

## 通往更好职业的钥匙

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

[应用服务现在也支持。NET 6](https://azure.github.io/AppService/2021/11/08/Dot.Net6.on.App.Service.html) 在 Windows 和 Linux 机器上都可以。您也可以使用 ASP.NET 核心，如果您已经在使用的预览版。NET 6 为你的 app 服务，不用慌。当您的应用程序重新启动时，新的运行时版本将自动获得。

Azure 静态 web 应用现在支持全栈。NET 6 应用程序，或者使用 Blazor Web Assemblies，或者使用 Azure Function APIs，或者同时使用两者。

Azure 上的 Kubernetes 也获得了。NET 6 治疗，而且肯定会有更多的服务。。NET 6 是 LTS，长期支持，版本。这意味着任何支持该框架的服务都将拥有该版本。

* * *

*想了解更多关于使用 Azure 进行云开发的信息吗？查看[本月的免费 ACG 课程阵容](https://acloudguru.com/blog/news/whats-free-at-acg)，包括我们闪亮的新 [AZ-400 DevOps 认证考试课程](https://acloudguru.com/course/az-400-designing-and-implementing-microsoft-devops-solutions)。只需[创建一个免费账户](https://acloudguru.com/pricing)并升级。不需要信用卡！*

* * *

## 表现在。网络 6

业绩是一个难以捉摸的目标，当你实现它时，它会立即远离你。然而，这并没有阻止微软的奇才。的新版本。NET 有如此多的改进，以至于宣布它的博客文章长达 8 公里。或者差不多。不过，让我给你总结一下。

*   Just in Time (JiT)编译器已经以“难以置信的方式”进行了更新。不，事实上，我相信他们。它与内联和非虚拟化有关。。。不过，我不明白。
*   垃圾收集器的实现已经从段变成了区域，这对于如何确定内存块的大小和使用内存块具有重要意义。
*   Guid、string、random、environment 等系统类型的吞吐量已经大大提高。在某些情况下，与以前的版本相比，改进了 90%或更多。
*   收藏和 LINQ 也得到了改善。对列表和字典采取“克隆”的方法。它比以前提高了 97%。净 4.8。天啊。

还有很多，但我有时间做的只有这些了。

我提到这些性能改进是因为，当然，它将*所有*流入你使用. NET 的 Azure 应用中。如果你对性能调整和改进的细节感兴趣，那么土星 V 大小的[博客帖子](https://devblogs.microsoft.com/dotnet/announcing-net-6/)值得一读。

* * *

[![Complete guide to the Cloud and Dictionary ](img/93ebf63b88ab7fbd48705a01952ba688.png)](https://get.acloudguru.com/cloud-dictionary-of-pain)

[**得到蔚蓝云痛苦辞典**](https://get.acloudguru.com/cloud-dictionary-of-pain)
说云不一定要辛苦。我们分析了数以百万计的回复，找出了最容易让人犯错的概念。抓住这个[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)获取 Azure 中一些最痛苦术语的简洁定义。

* * *

## 。NET 6 提供了一个统一的平台

编程的圣杯时刻之一是重用代码。我过去常常在我的 Windows 和 Windows Phone 应用程序之间重用代码。啊，那是过去的美好时光。。。但是我跑题了。

。NET 6 在创建一个包括浏览器、云应用、桌面、物联网和移动应用的统一平台方面取得了巨大进展。

这个平台让分享变得更加容易。目标之间的净 6。您可以编写在浏览器中运行的机器学习应用程序，并查找流数据异常或使用 web assembly 来。浏览器中的. NET 应用程序。用[。NET MAUI](https://github.com/dotnet/maui) (多平台应用程序 UI)，您甚至可以编写一个项目，在移动和桌面上创建类似的体验。

这些只是所有惊人的创新和进步的一小部分。NET 6。如果你生活在微软 Azure 开发者领域，这真的是一件大事，对 Azure 来说也是一件大事。我鼓励你去看看微软的博文，因为它真的很全面，值得一读。

正如我们在云专家团队中所说的，“寻找，你就会云。”下周见。继续牛逼吧，云大师们！

*想跟上万物云？* [*在 YouTube 上订阅一位云专家*](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1) *的每周微软 Azure 新闻(以及其他云提供商的新闻)。你也可以像我们一样关注*[](https://www.facebook.com/acloudguru)**，关注我们的* [*推特*](https://twitter.com/acloudguru) *，或者加入* [*不和谐*](http://discord.gg/acloudguru) *的对话！**