# Azure 虚拟广域网、Azure 功能获取更新

> 原文：<https://acloudguru.com/blog/engineering/azure-virtual-wan-azure-functions-get-updates>

本周蔚蓝的奇妙世界有什么新鲜事？我们来看看 Azure 的虚拟广域网及其最新的更新，一些新的 Azure 功能，以及为你推荐最佳实例的新 VM 选择器工具。让我们开始吧！

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## 使用 Azure 虚拟广域网简化连接、路由和安全性

广域网(或 WAN)已经存在很长时间了，这是一个技术术语，意为“很长一段时间”WAN 将不同的小型网络(包括局域网)连接起来，形成一个更大的网络。

例如，它对于想要连接办公室局域网、保护网络等的企业来说是很有用的。

Azure 也有广域网产品，不出所料，它是虚拟的。这是一个统一的基于中心和分支的架构，使用微软全球骨干网提供网络即服务(NaaS)的连接、安全和路由。这是关键。你可以使用微软主干网，这是一条洲际数据高速公路。

现在正式提供的一些新功能包括:

*   自定义流量选择器，确保站点间连接的预定义和一致路由。这与 VPN 网关基于策略的功能相结合，并允许您指定精确、宽或窄流量选择器。
*   Azure Virtual WAN VPN gateway 上的数据包捕获功能可捕获所有连接上的所有数据包，从而获得整体视图。这可以帮助您确定任何问题是在内部网络还是 Azure 或两者之间。
*   远程或本地 RADIUS 服务器在 VPN 连接设置期间对用户进行身份验证。这也包括 RADIUS 部署的一些简化。
*   高级路由利用特定的 ExpressRoute 要求。
*   最后，BGP 与 Azure 虚拟广域网集线器对等。

* * *

### AWS 中的 Azure 用户？

当热爱 Azure 的 Lars 前往黑暗面并尝试 AWS 任务时会发生什么？我们挑战 Lars 在他不知道的云平台上走过(或绊倒)一个他从未见过的场景。

* * *

## 构建实时 web Azure 功能更新

似乎每周都有更多关于 Azure 功能的新闻和特性。你知道吗？我不介意！就开发、定价和维护而言，Azure Functions 是最容易接近的服务之一。我就是喜欢。

无论如何，这个星期我有两个功能更新给你。

*   首先， [Node.js 版本 16.13x](https://azure.microsoft.com/en-au/updates/public-preview-nodejs-16-in-azure-functions/) 现已公开预览。这是 Node.js 的下一个长期支持(LTS)版本，可用于 Linux 函数应用程序。运行 Windows 的功能应用的更新将在下个月的某个时候到来。

*   其次，Azure 函数现在可以通过 Azure SQL 的[输入和输出绑定](https://azure.microsoft.com/en-au/updates/public-preview-azure-sql-bindings-for-azure-functions/)与 SQL 数据库交互。你可以得到微软。蔚蓝色。WebJobs.Extensions.Sql 库，并直接使用它。使用 Azure SQL 绑定，数据可以通过输入绑定从数据库输入到函数，数据可以从函数输出到数据库。这非常简洁，并且将传统的 SQL 数据存储与轻量级功能应用程序联系起来。

* * *

[![Complete guide to the Cloud and Dictionary ](img/93ebf63b88ab7fbd48705a01952ba688.png)](https://get.acloudguru.com/cloud-dictionary-of-pain)

[**得到蔚蓝云痛苦辞典**](https://get.acloudguru.com/cloud-dictionary-of-pain)
说云不一定要辛苦。我们分析了数以百万计的回复，找出了最容易让人犯错的概念。抓住这个[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)获取 Azure 中一些最痛苦术语的简洁定义。

* * *

## 虚拟机选择器现已正式推出。

Azure 上有数百个不同用途的虚拟机。有些是用于测试的，运行起来非常便宜，有些有令人难以置信的规格，比如上周的超级计算机，有些针对内存密集型工作负载进行了优化，等等。但是，你如何为你的项目找到合适的呢？到目前为止，这是最好的猜测，再加上一点试探，看看会有什么结果。

本周[虚拟机选择器工具](https://azure.microsoft.com/en-au/updates/virtual-machines-selector-now-generally-available/)在 GA 发布。告诉该工具你想用虚拟机做什么，你需要多少内存，你更喜欢哪个操作系统，你在哪个地区，以及其他一些偏好，它会为你推荐合适的虚拟机系列和实例。就虚拟机而言，这将为您节省时间和金钱。不过，用完之后别忘了关掉它们。

在我们得到之前，你想了解更多关于使用 Azure 进行云开发的知识吗？查看[本月的免费 ACG 课程](https://acloudguru.com/blog/news/whats-free-at-acg)，包括我们闪亮的新 [AZ-400 DevOps 认证考试课程](https://acloudguru.com/course/az-400-designing-and-implementing-microsoft-devops-solutions)。只需[创建一个免费账户](https://acloudguru.com/pricing)并升级。不需要信用卡！

本周的新闻到此结束。正如我们在云专家团队中所说的，当你的同事告诉你在周二早上早点出现，只是为了让你做一些 Linux 体操和 AWS 俯卧撑时:“寻求，你就会云。”

下周见。继续牛逼吧，云大师们！

* * *

*想跟上万物云？* [*在 YouTube 上订阅一位云专家*](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1) *的每周微软 Azure 新闻(以及其他云提供商的新闻)。你也可以像我们一样关注*[](https://www.facebook.com/acloudguru)**，关注我们的* [*推特*](https://twitter.com/acloudguru) *，或者加入* [*不和谐*](http://discord.gg/acloudguru) *的对话！**