# 如何解决 3 个常见的 Azure AD Connect 错误

> 原文：<https://acloudguru.com/blog/engineering/how-to-troubleshoot-3-common-azure-ad-connect-errors>

在你的科技职业生涯中，你可能会听到类似这样的话:“我们希望利用云和我们现有的基础设施。我们如何做到这一点？”

有几种不同的方法可以使用微软 Azure 来帮助实现这个目标，但在我看来，Azure AD Connect 是最有用的方法之一。该服务使您能够将内部身份与 Azure 同步。

在这篇文章中，我们将探讨如何解决 Azure AD Connect 可能不时出现的一些问题。

## 什么是 Azure AD Connect？

Azure AD Connect 使您能够将本地身份与 Azure 同步，以创建一个单一的混合身份。我们为什么要这么做？

好吧，除非你喜欢你的终端用户在他们不记得他们的两个或三个帐户中的哪一个是用来访问云应用程序还是本地应用程序时对你大喊大叫，这是非常有用的！

*[好奇 Active Directory 和 Azure AD 的区别？](https://acloudguru.com/blog/engineering/active-directory-vs-azure-active-directory-whats-the-difference)*

## Azure AD Connect 故障诊断

首先，让我描述一下我们所处的情况和环境。你在一家蓬勃发展的电动汽车公司 Beep-Beep Incorporated 担任云工程师。

您已经在主 Windows Active Directory 域控制器上实施了带有直通身份验证的 Azure AD Connect，并且它已经将您的内部部署身份同步到 Azure Active Directory 几周了，没有出现任何问题。

然而，就像 IT 世界中的大多数事情一样，它在某个时候肯定会崩溃。

所以，让我们开始深入研究，看看你在使用 Azure AD Connect 时可能遇到的一些错误，如何对其进行故障排除，以及这些错误的修复方法！

* * *

[**获得痛苦的云词典**](https://get.acloudguru.com/cloud-dictionary-of-pain)
说云不一定要努力。我们分析了数以百万计的回复，找出了最容易让人犯错的概念。抓住这个[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)获取一些最痛苦的云术语的简洁定义。

* * *

### 错误# 1–同步帐户问题

上周，哔哔公司的安全团队要求所有域用户帐户密码重置。他们要求系统管理员执行这些更改，在密码重置后，一切都运行顺利。或者看起来是这样…

今天早上，您试图在内部域上为一名新员工创建一个用户帐户。不幸的是，它没有出现在 Azure AD 中。你的终端用户仍然可以通过 Azure 门户登录，所以这似乎是一个同步问题。我们来看看吧！

在对 AD connect 问题进行故障诊断时，我喜欢检查的第一个地方是 Azure 门户，所以现在让我们检查一下。

嗯，Azure AD Connect 主页上没有报告任何问题。让我们检查 AD Connect 运行状况页面中的同步错误。

那里也没有运气！如果门户未能报告错误，下一个最佳检查位置是安装了 AD Connect 代理的 Active Directory 域控制器上的 AD Connect Sync 服务管理器。

啊哈！我们终于看到了一些没有启动凭证的错误，所以让我们打开其中的一个，看看我们是否能找到更多的信息。

这就是:由于凭证无效，身份验证失败。太好了，现在我们知道到底是什么问题了！

但是等等，你可能会说，什么账号，哪些凭证是无效的？

这是一个很好的问题。在 Azure AD connect 的安装过程中，默认情况下，它会创建一个新的 Active Directory 帐户，AD connect 使用该帐户连接并同步到 Active Directory 林。这里有一个指向 MS 文档的链接，以获取更多信息:[https://docs . Microsoft . com/en-us/azure/active-directory/hybrid/how-to-connect-install-custom # connect-your-directory](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-install-custom#connect-your-directories)

有了这些知识，系统管理员似乎更新了该帐户的密码(在我们的例子中，该帐户名为 MSOL_2abd5ac8a8dd ),但没有意识到它也需要在 AD Connect 设置中更新。让我们继续更新密码，以便我们可以再次开始同步！

转到同步服务管理器中的连接器选项卡，双击活动目录域服务连接器。在打开的“属性”窗口中，选择左侧窗格中的“连接到 Active Directory 林”选项，最后，在“密码”框中键入系统管理员使用的更新密码，然后单击“确定”。

干得好。现在，如果您再次检查同步服务管理器，您应该看到全面成功！

* * *

*想提高您的 Azure Active Directory 技能吗？看看 ACG 为微软 Azure 广告新设的[动手实验室。](https://acloudguru.com/blog/news/a-cloud-guru-expands-hands-on-learning-launches-microsoft-azure-ad-labs)*

* * *

### 错误 2——服务问题

哔哔公司又过了一周，当你周一早上到达时，你会收到服务台技术团队发来的一系列电子邮件和通知。您的最终用户报告，当他们尝试使用混合身份登录 Azure 时，会收到一条登录失败的错误消息。呀！

周五登录还好好的，现在，周一早上，一切都坏了。周末发生了什么？你记得域控制器在周日晚上被打了补丁并重启了，所以也许这与此有关？

是时候喝杯咖啡，上车，开始故障排除了！首先，我们将在进入 VM 之前检查 Azure 门户的错误。在我们深入进行故障排除之前，检查 Azure 是否有中断也是一个好主意:[https://status.azure.com/en-us/status](https://status.azure.com/en-us/status)

主 AD connect 页面上没有报告任何问题，Azure 也没有[中断。让我们检查并查看 Azure AD Connect 健康门户是否显示任何同步问题。](https://acloudguru.com/blog/engineering/what-happened-with-microsoft-azures-active-directory-and-dns-outages)

这里也没有错误。和上次一样，下一站是同步服务管理器应用程序中的域控制器。

嗯，这里也没有显示任何错误…当你到了这个阶段，你仍然没有看到任何错误，最好的检查点是广告连接服务，然后是 Windows 事件查看器。

让我们通过 Win key + R 和打字服务打开 Windows 服务。我们将检查并确保 AD Connect 服务正在运行。

嘿，身份验证代理服务没有运行！让我们右键单击那个家伙并启动它。

好消息。启动该服务后，您要求您的最终用户再次尝试登录，他们报告说他们现在可以访问 Azure 了！

那么，为什么这项服务会导致用户登录问题呢？

在这种情况下，AD Connect 通过传递身份验证进行设置。当用户尝试登录时，它将直接根据您的 Active Directory 域验证他们的密码。如果您的域控制器上的身份验证代理服务关闭，AD Connect 将无法对您的域进行身份验证，并且不会发生任何用户登录。

### 错误# 3-属性错误

哔哔公司又过了几个星期没有发生任何事故，但是现在又出现了另一个问题！今天早些时候，您要求系统管理员为新员工玛丽·安德森创建一个用户帐户。

不幸的是，她的用户帐户还没有显示在 Azure AD 中，并且她的帐户已经创建了几个小时。是时候排除故障了！

同样，主页上没有问题，所以现在是时候前往广告连接同步健康页面。

啊哦。看起来我们有一个数据验证失败！让我们点击那个框并进行调查。我还想提到的是[微软有很好的关于 AD connect](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/tshoot-connect-sync-errors#identitydatavalidationfailed) 故障排除的文档。

但是，为了获得完整的故障排除体验，我们将按照逻辑、渐进的顺序继续前进。

看起来我们的问题是你要求系统管理员创建的用户帐户，所以这就解释了为什么我们还没有在 Azure AD 中看到它。让我们点击玛丽·安德森的名字在这里，并看到更多关于错误的细节。

![](img/97bc435a95ad6d894992a13b5faccee3.png)

太好了。让我们把这个分解一下，看看我们有什么。在描述下，我们看到她的帐户未能同步，因为属性不符合验证要求。不幸的是，在 property 部分下，属性被列为 N/A…那么，哪个属性没有满足验证要求呢？(如果您已经能够识别问题，将获得加分！)

由于门户中没有更多信息，让我们进入我们的 VM，看看是否能发现任何错误。

我们的第一站是拉起我们值得信赖的广告连接同步服务管理器。看起来我们有一个错误要查看！让我们仔细看看，看看它是否能帮助我们缩小属性范围。

在那里！第一句话:`the attribute [userPrincipalName], is not valid`。我们看到有问题的属性是`userPrincipalName`，它是该用户的登录名。

有了这些知识，让我们看看 Mary 在 Active Directory 中的帐户，看看她的登录名有什么问题。

啊哈！她的用户名中有一个 Azure AD connect 不支持的`&`。(当创建包含`&`的帐户时，Active Directory 也不会警告您。)

这很好，但是我怎么知道不支持`&`字符呢？[微软有关于各种属性允许和不允许的文档](https://docs.microsoft.com/en-us/microsoft-365/enterprise/prepare-for-directory-synchronization?view=o365-worldwide#2-directory-object-and-attribute-preparation)。因此，如果我们打开文档，向下滚动到用户主体名称部分，我们会看到有几个无效字符，例如:& < > * +和其他字符。

(这是另一个证明阅读文档的[职业改变艺术的案例](https://acloudguru.com/blog/engineering/the-career-changing-art-of-reading-the-docs)。)

现在我们知道了应该避免哪些字符，让我们继续删除`&`，保留 Mary 的登录名为`MaryAnderson`。单击“属性”选项卡底部的“确定”后，我们可以通过同步服务管理器启动同步，或者等待大约每 30 分钟开始一次同步。

同步发生后，我们看到 Mary 的用户帐户现在显示在 Azure AD 中，我们不再有任何数据验证失败！

干得好，我的朋友！

## 摘要

保持 Beep-Beep Incorporated 运行及其用户满意的伟大工作！在这篇文章中，我们看到了 Azure AD Connect 可能出现的几个不同的问题，这些错误看起来像什么，如何对它们进行故障排除，以及如何修复它们。

如果你想更多地了解混合环境，以及如何利用 Azure AD Connect 等 Azure 服务来支持你的组织，请查看我的课程[Azure 上的混合环境简介](https://acloudguru.com/course/introduction-to-hybrid-environments-on-azure)。在这篇文章中，我介绍了几种有助于混合环境场景的 Azure 服务。

* * *

## **提升您的云计算事业。**

加入[云专家](https://acloudguru.com/pricing)并获得课程、动手实验、测验和学习路径，这些将带你一步一步地从新手成为你所选择的云领域的专家。获得 [7 天免费试用](https://acloudguru.com/pricing)或查看我们的[免费课程](https://acloudguru.com/blog/news/whats-free-at-acg-may-2021)。