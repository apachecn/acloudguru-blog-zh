# 12 月新闻综述:Azure 有什么新特性？

> 原文：<https://acloudguru.com/blog/engineering/december-news-roundup-whats-new-with-azure>

你好，云大师！想知道 Azure 在过去的一个月里发生了什么变化，但没有时间查看标题？我们已经写了一篇文章，提供了你需要知道的所有信息。

## Azure 的 PSRule

本月初，我们采访了来自微软的 Bernie White，他告诉了我们关于 Azure 的 PS rule——一个开源的 IaC 工具，可以帮助提升 Azure 部署。看看下面的聊天吧！

AZ-800 认证现已推出

本月，云专家推出了一门全新的认证课程，名为 [AZ-800 或管理 Windows Server 混合核心基础设施](https://learn.acloud.guru/course/az-800-administering-windows-server-hybrid-core-infrastructure/dashboard)。这是一门很棒的课程，充满了大量的动手实验，数小时有意义的内容，所有这些都是为了教会你 Windows 服务器的来龙去脉。它涵盖了正在向云过渡的企业迫切需要的内容。

如果你有时间，看看吧。有如此多的演示、教程和动手实验，当你完成时，你会真正感觉到你不仅理解了材料，而且已经亲自处理了相当长一段时间的概念。

## 因此，如果你曾经想学习混合动力，让自己从竞争中脱颖而出，在这个月自己打开这个可怕的新课程。

Azure 容器应用的新部署选项

微软宣布了一些部署 Azure 容器应用的新方法。这些特性中的第一个，目前在 preview 中，[允许你仅从源代码](https://azure.microsoft.com/en-au/updates/public-preview-build-and-deploy-to-azure-container-apps-without-a-dockerfile-from-the-azure-cli/)部署 Azure 容器应用。不需要提供 docker 文件或创建容器映像的说明。

这是使用 Azure CLI 中简单的`az container up`命令实现的。

## 在后台，该命令将部署容器应用程序所需的所有资源，如果您将 GitHub 作为源，它甚至会配置连续交付。

还有一个新的部署选项，除了支持这种连续交付的 [GitHub 操作](https://azure.microsoft.com/en-au/updates/public-preview-github-action-to-build-and-deploy-to-azure-container-apps/)，现在还有用于 Azure DevOps 部署 Azure 容器应用的[管道任务。](https://azure.microsoft.com/en-au/updates/public-preview-azure-pipelines-task-to-build-and-deploy-to-azure-container-apps/)

更好的是，所有你喜欢的源代码语言都被支持，包括。NET，Node，PHP，Python，Ruby 和 Go。如果你更喜欢视觉学习，Wayne Hoggett 将演示这些选项。

**Azure Bastion 可共享链接**

微软还在公开预览版中公布了 [Azure Bastion 可共享链接。这项新功能支持通过简单的链接连接到目标虚拟机或虚拟机规模集。有了这个特性，您不再需要提供对 Azure Portal 的访问，就可以使用 HTTPS 向使用 Azure Bastion 的虚拟机或规模集授予远程访问权限。](https://azure.microsoft.com/en-au/updates/azure-bastion-shareable-links/)

这是一个很棒的功能，因为您经常需要提供对虚拟机的临时安全访问，以便软件供应商或开发人员可以为他们在您的虚拟机上运行的应用程序提供支持。你可以在下面看到 Wayne Hoggett 的演示！

Microsoft also announced [Azure Bastion Shareable Links in Public Preview](https://azure.microsoft.com/en-au/updates/azure-bastion-shareable-links/). This new feature enables connectivity to a target VM or VM scale set using a simple link. With this feature you longer need to provide access to the Azure Portal to grant remote access using HTTPS to a VM or scale set using Azure Bastion.

**Azure 免费服务更新为 55+免费服务**

谁不喜欢免费的东西？

微软已经增加了新用户前 12 个月免费的 Azure 服务数量。新服务包括高达 100GB 的本地冗余 Azure 文件和长达 5 小时的直播和点播流媒体服务。

## 微软最近还将一直免费的 Azure 服务数量从大约 40 个增加到超过 55 个。无论您是 Azure 免费试用版还是预付费订阅版，您都将获得这些服务的免费配额。

一些新服务包括 Azure 容器应用的配额，新的人工智能和机器学习服务，如 Metrics Advisor 和扬声器识别，以及与 Web PubSub 的实时通信。

工作负载迁移和现代化的 3 个关键云采用趋势

微软上个月委托对 1200 多名 IT 决策者进行的一项新研究揭示了三个关键的云采用趋势。

尽管全球的商业环境极不确定，但超过 82%的受访者表示，在不确定的商业环境中，云采用计划仍然是战略的一部分。

## 超过 74%的受访企业表示，现代化是数字化转型的一个重点。

超过 63%的受访者表示，混合和多云环境是新常态。

*   Brian Roehm 认为，这与他在社区中听到的一致:云将继续存在，采用率可能会继续增长到饱和，而机器学习等新技术将继续发展壮大。
*   Azure PaaS 服务公司的福雷斯特·TEI
*   继续学习的话题…

[微软最近与 Forrester](https://azure.microsoft.com/en-us/blog/forrester-study-finds-228-percent-roi-when-modernizing-applications-on-azure-paas/) 合作，测量通过利用托管云服务(如 Azure 的平台即服务产品)对传统应用进行现代化改造所带来的真实投资回报。云现代化的最终结果是在三年时间内实现了 228%的投资回报率，这是一个巨大的数字！

## 进一步来说，应用程序现代化包括停止对内部基础架构的投资，并将应用程序迁移到托管服务(如 Azure App Service)上运行，而不是简单地移植到基于云的虚拟机上。

投资回报数字是根据许多因素计算出来的，包括:

无需购买现场基础设施，节省了成本

降低管理成本

提高开发应用程序的效率

1.  扩展应用的正常运行时间延长

2.  通过以前所未有的速度将应用推向市场来节省时间

3.  总的来说，使用本地应用程序的相同规模的团队能够通过托管 Azure 服务更快、更有效地运行，让他们专注于更有价值的任务，而不是管理基础架构，并且正常运行时间也更长。

4.  这就是 Azure 月份的所有头条新闻！

5.  想每周了解 Azure 新闻吗？

本周 Azure 是关于 Azure 的每周新闻综述。加入我们的专家主持人，因为他们涵盖了你需要知道的关于过去一周发展的一切，保持简短、有趣和信息丰富。

无论您是刚刚开始您的云之旅，还是您已经了解自己的东西，每个人都有适合自己的东西！

## Want to keep on top of Azure News each week?

[Azure This Week](https://www.youtube.com/playlist?list=PLI1_CQcV71RmnrRBgJNlI1yY_WiOWIXov) is your weekly news roundup for all things Azure. Join our expert hosts as they cover everything you need to know about the past week’s developments, keeping it short, fun and informative. 

Whether you’re just beginning your cloud journey, or you know your stuff, there’s something for everyone!