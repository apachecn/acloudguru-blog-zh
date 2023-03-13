# 我的五大 Azure 混合云技术

> 原文：<https://acloudguru.com/blog/engineering/my-top-5-azure-hybrid-cloud-technologies>

在这篇文章中，我回顾并排列了我的五大 Azure 混合云技术。我还解释了如何根据您的用例来最好地使用它们。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

# Azure 混合云技术

三大云提供商有很多相似之处，但我认为微软 Azure 占优势的一个领域是混合计算。有一系列 Azure 混合云服务旨在让您在跨云和内部、甚至跨多个云提供商工作时更加轻松。

所以，在这里我向你展示了我的五大 Azure 混合云技术。

现在我有一个挑战给你。读了这篇文章，如果你没有“哼，我不知道”的时候，我会很惊讶。如果你真的有这样的时刻，把这篇文章分享给你的社交网络，加上“今天我学会了”，这样其他人也能学会。

我们成交了吗？太好了，我们跳进去吧！

## 5.Azure 广告连接

如果你的公司像大多数公司一样，使用活动目录域服务(AD DS)管理他们的身份，你无疑会知道 [Azure AD Connect](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/whatis-azure-ad-connect) 。它允许你将你的 AD DS 身份同步到[Azure Active Directory](https://azure.microsoft.com/en-au/services/active-directory/)(Azure AD)。

Azure AD Connect 包括对一系列同步和身份验证选项的支持。它非常灵活——您可以选择要同步的内容以及您的用户如何进行身份验证。如果需要，您甚至可以将所有身份验证保存在本地。

安装和配置 Azure AD Connect 的过程在过去几年中有了显著的改进。现在，设置和管理比以往任何时候都更容易。Azure AD 还提供了比以往更多的选项来帮助您配置混合身份。随着 Azure AD Connect 云同步的引入，您现在可以通过高可用性或在多个断开的 AD DS 林之间实现这一点。

在内部 AD DS 环境和 Azure AD 之间同步您的身份被称为混合身份。混合身份带来了巨大的好处。这些优势包括:

*   用户可以使用相同的用户名和密码登录您的内部应用和云应用。
*   您可以通过多因素身份验证和密码健康检查来保护您的身份，防止危险的登录。
*   如果需要，用户可以使用自助密码重置来重置其密码。
*   您可以控制对敏感应用程序的访问。这有助于您使用条件访问实现更严格的安全控制。

现在你可能会想。韦恩，这些我都知道了。

好的，但是您是否知道您还可以允许您的用户使用他们的 AD DS 凭据登录到断开连接的虚拟网络上的 Azure 虚拟机？这甚至支持条件访问和多因素身份验证。等等，什么？是的，[它确实是](https://docs.microsoft.com/azure/active-directory/devices/howto-vm-sign-in-azure-ad-windows)。

现在，您可以停止在未加入 AD DS 域的虚拟机上共享或重用凭据。

## 4.Azure 广告应用程序代理

Azure AD 身份验证非常适合诞生在云中的应用程序，这些应用程序旨在支持 Azure AD 支持的身份验证选项。但是，所有不支持这种功能的应用程序怎么办呢？

如果你的公司已经存在了一段时间，他们可能有一大堆这样的应用程序。不仅如此，这些应用程序可能会与内部网络上的其他应用程序和服务紧密集成。

升级、替换或迁移这些应用程序可能不是简单的“按一下开关”。这是否意味着你被困在虚拟专用网络(VPN)连接中？不会吧！ [Azure AD 应用程序代理](https://docs.microsoft.com/en-us/azure/active-directory/app-proxy/)允许您在任何地方、任何设备上远程访问您的传统 web 应用程序。

它也很容易设置。您只需要在您的内部网络上部署一个或多个应用程序代理连接器，然后在 Azure AD 中添加应用程序配置。就是这样。不需要特殊的防火墙配置或反向代理。

好吧，你已经知道了，是吗？好的，您知道您的后端应用程序不需要在本地运行，也不需要在 Windows Server 上运行，甚至不需要使用互联网信息服务(IIS)吗？您的后端应用程序几乎可以是任何 web 应用程序。

好吧，以防你已经知道，你知道你可以使用 Azure AD 应用程序代理为不支持 AD DS 身份验证的应用程序提供单点登录(SSO)吗？

没错，您可以为使用简单用户名和密码组合的应用程序配置[基于密码的认证](https://docs.microsoft.com/en-us/azure/active-directory/app-proxy/application-proxy-configure-single-sign-on-password-vaulting)，而无需与需要访问的用户共享这些凭证。

整洁，对不对？

## 3.Azure 文件

当你部署 Azure 存储帐户时，你可以访问 Azure Blobs、Azure 表、Azure 存储队列和 [Azure 文件](https://docs.microsoft.com/en-us/azure/storage/files/storage-files-introduction)。Blobs、表和队列都很好，但是 Azure Files 很特别。Azure Files 允许您使用网络文件系统(NFS)和服务器消息块(SMB)等熟悉的协议来访问 Azure 存储。

这样做的好处是，您可以将现有的文件服务器作为服务迁移到平台，而无需更改任何应用程序。这样做的问题是，当您从内部访问时，访问云中的存储会比较慢。

Azure files 包括 [Azure File Sync](https://docs.microsoft.com/en-us/azure/storage/file-sync/file-sync-deployment-guide?tabs=azure-portal%2Cproactive-portal) ，它允许您在 Azure Files 共享和本地 Windows 服务器之间同步数据。您可以将此功能用于多种用途。但我最喜欢的功能是使用 Azure 文件同步进行灾难恢复，这一点乍一看并不明显。

在服务器出现故障的情况下，您可以快速启动另一个文件服务器，安装 Azure 文件同步代理，从 Azure 文件下载名称空间，并几乎立即提供对数据的访问。如果你以前从未尝试过，它会非常快。因为您只下载名称空间(实际上是文件存根)，所以您可以立即访问所有数据，而无需等待完全恢复。

你可能已经知道了，但是你知道你也可以[给你的 Azure 文件共享](https://docs.microsoft.com/en-us/azure/backup/azure-file-share-backup-overview)拍快照吗？这为您提供了时间点恢复，而不会消耗文件共享或服务器上的额外磁盘空间。太好了。

## 2.Azure 自动化

哦，现在我们开始真正的好东西。排名第二的是 Azure Automation。Azure Automation 是 Azure 提供的经常被忽视的自动化、配置和更新管理工具箱。

它是为混合动力而从头开始构建的。Azure Automation 中的一切都在 Azure 和内部提供相同的功能。一切。

如果你没有使用[Azure Automation Update Management](https://docs.microsoft.com/en-us/azure/automation/update-management/overview)来自动化你的微软补丁部署，你真的应该看看。

Azure Automation 真正强大的地方在于它与其他 Azure 服务的集成。自动化更新管理的一个真正常见的反对理由是“如果”。如果我们的域控制器不能正确启动怎么办？如果 SQL 服务器不能正常启动怎么办？

你有几个选择来确保这不会是一个问题。你可以运行 Azure Automation [前置和后置脚本](https://docs.microsoft.com/en-us/azure/automation/update-management/pre-post-scripts)作为你更新计划的一部分。这些 runbooks 的问题是它们只能在 Azure 中运行。但是你知道你可以从这些 run book 调用其他 run book 吗？您还可以调用 runbook 在称为混合工作者的设备上运行。是的，您可以使用一个脚本来检查 Active Directory，并在补丁部署后检查您的 SQL Servers，以确保它们可用。

或者，你也可以将它与 [Azure Monitor alerts](https://docs.microsoft.com/en-us/azure/azure-monitor/alerts/action-groups#action-specific-information) 集成在一起。在这里，您可以使用古老的 80/20 规则，用广泛的脚本处理 80%的最常见问题，这些脚本检查服务启动之类的事情，还有 20%的脚本专注于您真正关键的应用程序，并对这些应用程序进行真正具体的检查。

不知不觉中，您的补丁将永远是最新的，不会再有任何问题。因此，您可以花更多时间为公司创造价值，而不是一直开着灯。

## 1.天蓝色电弧

我们成功了。在我最喜欢的五大 Azure 混合云中排名第一。你听说过[天蓝色弧光](https://azure.microsoft.com/en-au/services/azure-arc/)吧？Azure Arc 将 Azure 管理平面(有时称为控制平面)扩展到 Azure 外部的工作负载，无论是内部还是其他云中。真的很整洁。

控制面板为您的工作负载提供基于角色的访问控制和管理功能。这意味着您可以像管理 Azure 虚拟机一样管理和监控本地服务器。

Azure Arc 的一个我最喜欢的特性是当你将它与 [Azure Monitor Log Analytics](https://docs.microsoft.com/en-us/azure/azure-monitor/logs/log-analytics-overview) 集成时。为了帮助减轻中央 IT 团队的管理和监控负担，您可以将这项工作分配给工作负载团队。

当您将服务器装载到 Azure Arc 中时，服务器会获得一个 Azure 资源 ID。如果您使用基于 Azure 角色的访问控制(RBAC)授予工作负载团队对 Azure Arc 服务器的读取权限，那么您可以在 Log Analytics 工作区上使用[资源上下文模式](https://docs.microsoft.com/en-us/azure/azure-monitor/logs/manage-access?tabs=portal#access-control-mode)来授予工作负载团队对他们需要的日志的访问权限，而不授予对整个工作区的访问权限。

对于任何想要从云采用框架中实施[分散运营](https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/operating-model/compare#decentralized-operations)运营模式的公司来说，这都是必须的。

## 顶级 Azure 混合云技术摘要

我们进展如何——你有没有那种“啊，我不知道”的时刻？确保你与你的网络分享你所学到的，这样其他人也可以学习！

如果你有兴趣了解更多关于 Azure 混合云技术的知识，尤其是在使用 Windows Server 时，请务必查看我的最新课程， [AZ-800:管理 Windows Server 混合核心基础设施](https://acloudguru.com/course/az-800-administering-windows-server-hybrid-core-infrastructure)。这不仅能让你为考试做好准备，而且我还分享了很多在现实生活中帮助你的技巧和窍门。

![why should i get azure](img/3ee87ddb6a81b5631ab6555721b8b023.png)

*想了解更多关于 Azure 认证的信息？*
*查看我们的* *[Azure 认证和学习路径。](https://acloudguru.com/azure-cloud-training)*