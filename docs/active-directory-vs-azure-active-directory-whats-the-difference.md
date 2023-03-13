# Active Directory vs Azure AD:有什么区别？|云专家

> 原文：<https://acloudguru.com/blog/engineering/active-directory-vs-azure-active-directory-whats-the-difference>

#### Active Directory vs Azure Active Directory:有区别吗？

有很多不同的路径会把你引向 Azure Active Directory (Azure AD)。也许您已经在您的组织中推出了 Office 365。也许你正在将一些虚拟机转移到 Azure 中。或者，您可能正在开发一个完全不会影响您的内部环境的云原生应用程序。

不管是什么原因，你可能会认为 Azure Active Directory 只是运行在组织服务器上的 Active Directory 域服务认证平台的 Microsoft Azure 云版本。确实是。。。但话说回来，也不是。

那么，Active Directory 和 Azure Active Directory 有什么区别呢？让我们来看看细节。

* * *

*想提高您的 Azure Active Directory 技能吗？看看 ACG 为微软 Azure 广告新设的[动手实验室。](https://acloudguru.com/blog/news/a-cloud-guru-expands-hands-on-learning-launches-microsoft-azure-ad-labs)*

* * *

### 认证和授权平台

首先，[活动目录](https://docs.microsoft.com/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview?Wt.mc_id=modinfra-16315)和 [Azure 活动目录](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis?WT.mc_id=modinfra-16315-socuff)都提供认证和授权服务。它们存储用户名和密码(从技术上讲，是加密的密码散列)等信息，用于验证登录者在尝试登录时是否正确地提供了与系统中有效的活动用户相匹配的相同凭据。

它们还充当授权服务。假设您试图访问一个配置为只允许 HR 组成员使用的资源，这些目录系统有一个 HR 组及其成员列表。它比计算机帐户和服务帐户(两者都不是人)的范围要广一点，但是身份验证和授权原则是这些系统的标准功能。

### 身份和访问管理(IAM)

虽然身份验证和授权是 Active Directory 和 Azure AD 的功能，但系统本身也称为 IAM 或身份和访问管理系统。这意味着目录也用于。。。管理人和事物的身份以及管理对其他事物的访问。现在我们正在讨论添加、更改或删除用户帐户，更新组成员，以及用于将用户或组添加到某个事物(无论是文件还是文件夹、云资源还是应用程序)的安全控制中。

### 架构差异

当比较 Active Directory 和 Azure Active Directory 时，这就是相似之处的终点。这些 IAM 系统在幕后是非常不同的。

Active Directory 是 Windows Server 操作系统的一个角色，因此您现在有了一个底层操作系统来安装、更新和管理正常运行时间和性能(无论是物理服务器还是虚拟服务器)。Windows 客户端在其可访问的网络中寻找运行 Active Directory 域服务角色(称为域控制器)的服务器，因此您在不同的位置设置服务器，在彼此之间复制所有身份数据(以及任何更改)。

Active Directory 数据的结构有几个重要部分:目录架构、组织单位和域以及目录林。

*   目录模式是存储什么信息以及它与什么相关的“映射”。例如，我的模式可能包括“电子邮件地址”,每个人都会将其填充为“myemail@myorg.com”。使用 Active Directory，您可以扩展这个模式来添加额外的内容。也许您想添加“出生月份”,这样您就可以查询和庆祝每个在 12 月份生日的人，或者也许您有特定的业务属性，这些属性对于在自定义应用程序中存储和使用非常有用。
*   组织单位允许您指定一个结构，如组织图。您可以分成总部、制造、零售等部门，而不是将每个人都放在一个“用户”ou 中，这样您就可以跨不同的 OU 应用不同的设置或访问，并且可以限制数据复制到哪里，以减少网络流量。例如，将总部的数据复制到制造工厂的服务器上可能没有意义。
*   域和森林是大规模组织和分割身份验证数据的进一步方式。

有了 Azure AD，您无需管理域控制器，无需担心位置之间的数据复制，无需组织单位(但您可以管理组)，也无需森林。其中一个 Azure AD 服务(Azure AD 域服务)也不支持使用架构扩展，即您可能已经添加到内部 Active Directory 环境中的自定义属性。这听起来工作量少了很多(确实如此),但对于拥有复杂的内部环境的组织来说，这也不太灵活，因为他们的定制或第三方应用程序可能依赖于其中的一些配置。

那么，我们从 Azure Active Directory 中得到了什么？本质上，您可以使用作为服务交付的身份平台(IDaaS)，而这仅仅是个开始。微软管理服务的可用性和跨其全球云区域的数据复制。不需要排除故障。

您还将使用 Azure Active Directory 通过 Azure 资源管理器(包括像 Azure CLI 和 PowerShell 这样的工具)来管理对 Azure 中资源的访问。[基于角色的访问控制](https://docs.microsoft.com/azure/role-based-access-control/overview?WT.mc_id=modinfra-16315-socuff)允许您授予组或个人非常细粒度的访问权限，以对 Azure 资源类型或云环境区域(如资源组或订阅)执行操作。

## 额外的云好

使用 Active Directory，登录过程保持在您的公司网络中，而微软对此一无所知。

使用 Azure Active Directory，其云位置允许该目录服务受益于由微软支持的高级安全功能。其中包括:

*   一种基于“[条件的](https://docs.microsoft.com/azure/active-directory/conditional-access/overview?WT.mc_id=modinfra-16315-socuff)”方法，用于在被评估为有风险的登录尝试期间挑战另一种形式的身份验证(MFA)，这种评估是通过组织设置的参数(例如来自您没有员工的未知位置)或微软的分析检测到的行为进行的。
*   [用户能够重置自己的密码](https://docs.microsoft.com/azure/active-directory/authentication/concept-sspr-howitworks?WT.mc_id=modinfra-16315-socuff)，因为我们可以在允许 MFA 之前对其进行质询。
*   [在第三方软件即服务应用](https://docs.microsoft.com/azure/active-directory/app-provisioning/user-provisioning?WT.mc_id=modinfra-16315-socuff)中自动配置新用户，如 Salesforce 和 ServiceNow。有预定义的连接器，Azure AD 支持使用该系统进行跨域身份管理(SCIM)的应用程序。
*   一个[智能锁定](https://docs.microsoft.com/azure/active-directory/authentication/howto-password-smart-lockout?WT.mc_id=modinfra-16315-socuff)系统，可以检测来自合法用户的登录和来自未知来源的登录之间的差异，并可以区别对待它们——锁定不良行为者，同时仍然允许用户登录。

Azure Active Directory 分为免费、高级 1 级和高级 2 级。[并非所有功能在所有层级都可用](https://azure.microsoft.com/pricing/details/active-directory/?WT.mc_id=modinfra-16315-socuff)，有些功能与微软 365 计划捆绑销售。事实上，如果你的组织使用微软 365，它运行在 Azure Active Directory 上作为认证平台。

其中一些功能可以与您的内部 Active Directory 环境集成，如自助密码重置。

Azure Active Directory 还允许来宾帐户，您可以信任来自其他组织或其他身份系统的帐户，这些帐户带有 [Azure AD B2B](https://docs.microsoft.com/azure/active-directory/external-identities/what-is-b2b?WT.mc_id=modinfra-16315-socuff) 或 [Azure AD B2C](https://docs.microsoft.com/azure/active-directory-b2c/overview?WT.mc_id=modinfra-16315-socuff) 。这对于希望用户使用基于 OpenID Connect、OAuth 2.0 或 SAML 的现有社交或组织帐户登录的应用程序开发人员来说至关重要。

### Active Directory 和 Azure Active Directory 一起使用

如果已经有一个活动目录环境，您可以将它与 Azure 活动目录一起运行，以进行云身份验证。这被称为[混合身份](https://docs.microsoft.com/azure/active-directory/hybrid/whatis-hybrid-identity?WT.mc_id=modinfra-16315-socuff)，通常由希望为其用户提供[无缝单点登录](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso?WT.mc_id=modinfra-16315-socuff)流程的组织使用，以便他们可以访问内部和云或微软 365 资源。它还使管理员不必在两个不同的系统中管理身份。

如何构建将取决于您组织的特定需求，包括是否允许将您的身份和密码散列同步到云。为了支持各种合规场景，微软支持[密码哈希同步](https://docs.microsoft.com/azure/active-directory/hybrid/whatis-phs?WT.mc_id=modinfra-16315-socuff)、[穿越认证](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-pta?WT.mc_id=modinfra-16315-socuff)和[联盟](https://docs.microsoft.com/azure/active-directory/hybrid/whatis-fed?WT.mc_id=modinfra-16315-socuff)。

## 结论

云原生组织无需太多复杂即可进入基于云的身份服务，如 Azure Active Directory，但必须从 Windows 服务器环境迁移或继续管理 Windows 服务器环境的技术专家将发现 Azure AD 是一个需要学习的新事物。

任何身份平台更改都需要仔细规划和考虑，尤其是考虑到您当前的特定用途。但是你会发现 Azure Active Directory 的一些优点，包括没有管理服务基础设施的开销。

* * *

#### 关于作者

作为微软的高级云倡导者，Sonia Cuff 与全球技术社区保持联系。Sonia 拥有 20 多年的技术经验，从大型企业和政府到小型企业和合作伙伴，她热衷于改善 IT 运营人员的工作和生活。

* * *

## 提升您的 Azure Active Directory 技能

一位云专家为微软 Azure AD 推出了新的独家[动手实验室。拥有超过 1，600 个基于场景的实验室(还有数百个正在建设中)，云专家是学习云的实用方法。立即免费开始！](https://acloudguru.com/blog/news/a-cloud-guru-expands-hands-on-learning-launches-microsoft-azure-ad-labs)