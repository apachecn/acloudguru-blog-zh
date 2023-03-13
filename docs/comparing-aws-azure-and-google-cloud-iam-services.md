# 比较 AWS、Azure 和 Google Cloud IAM 服务

> 原文：<https://acloudguru.com/blog/engineering/comparing-aws-azure-and-google-cloud-iam-services>

## **AWS IAM vs GCP IAM vs 微软 Azure IAM**

#### TL；速度三角形定位法(dead reckoning)

比较三大云提供商通常意味着深入研究最新和最棒的计算节点，或者哪个平台拥有性能最好的 [NoSQL 数据库](https://acloudguru.com/blog/engineering/comparing-cloud-nosql-databases-dynamodb-vs-cosmos-db-vs-cloud-datastore-and-bigtable)。

作为“服务”经常被忽略的一点是如何处理给定云资源的访问和授权。强大的安全控制对于任何拥有云的组织来说都是至关重要的元素，访问管理也不例外。

本文将看看[亚马逊网络服务(AWS)](https://acloudguru.com/course/aws-iam-identity-and-access-management-deep-dive) 、[谷歌云](https://acloudguru.com/course/google-cloud-identity-and-access-management-iam-deep-dive)和[微软 Azure](https://acloudguru.com/course/identity-and-access-management-for-azure) 的身份和访问管理(IAM)服务，并提供一些有用的云 IAM 对比图表。三家云提供商进入；一篇博文离开。让我们开始吧！

* * *

有兴趣升级或开始云安全之旅吗？云专家的 [AWS 安全学习路径](https://acloudguru.com/learning-paths/aws-security)提供适合初学者和高级专家的定制课程！

* * *

## 我是什么？

我是什么？每个云提供商都使用“IAM”这个名字来描述他们围绕管理云资源的访问和授权的服务和 API 集合。Azure 在某种程度上是一个例外:IAM 一般用来描述 [Azure Active Directory](https://acloudguru.com/blog/engineering/active-directory-vs-azure-active-directory-whats-the-difference) 的特性。

在探索每个提供商的功能特性之前，了解问题域以及这些服务旨在为客户解决什么是有帮助的。

* * *

**Azure “IAM” generally refers to identity services provided via Azure Active Directory*

* * *

## 我是做什么用的？

#### Azure IAM、AWS IAM 和 GCP IAM 是做什么的？

那么我能解决什么呢？一个有用的起点是“最小特权”的概念最小权限原则(PLOP)是一个信息安全概念，它有效地规定了给定系统或资源的任何用户都只应被授予成功执行给定任务所需的最低权限和访问权限。

在云服务的背景下思考这个问题，PLOP 可以应用于几乎任何资源。存储对象、计算节点、数据库和日志记录仪表板等都包含潜在的敏感关键数据。所有员工和用户都应该对这些资源拥有相同的、广泛的访问权限吗？根据 PLOP 的说法，答案是否定的。满足大多数合规性框架的最低要求也意味着组织必须表明他们正在执行 PLOP，云资源也不例外。

云平台如何为客户提供一种高效、可扩展的方式来执行 PLOP？为每个服务或资源管理单独的访问和授权控制将很快成为一场逻辑噩梦，并且除了非常小的部署之外，不可扩展。通过各自的 IAM 产品，每个云提供商都提供统一的集中式服务来管理访问和授权。

* * *

[**获得痛苦的云词典**](https://get.acloudguru.com/cloud-dictionary-of-pain)
说云不一定要努力。我们分析了数百万份回复，找出了最容易让学生出错的术语和概念。在本[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)中，您将找到一些最令人头疼的云术语的简洁定义

* * *

## AWS、Azure 和 GCP IAM 定价和服务限制

对于三大巨头中的每一个，除了一点点例外，IAM 服务都被认为是基础的，并且是作为正常帐户使用的免费服务提供的。Azure 的 Active Directory IAM 产品是一个例外，它需要一个单独产品的订阅或许可证来解锁免费层。

对于 AWS 和 GCP 来说，一些关键的区别在于每个平台如何定义配额和服务限制。

就 AWS 而言,“配额”和“限额”可以互换。有些配额可以通过请求增加，而有些配额是固定值，不能增加。另一方面，GCP 将配额定义为可以增加的东西，而限额则不能。进一步扩展如何处理配额和限额的差异:GCP 通过“项目”定义一些配额和限额，而 AWS 中的逻辑边界总是在 AWS 帐户内。Azure 利用“限制”来指定可以扩展的限制/配额，以及不能扩展的限制/配额。在 Azure 的情况下，还有一个区别，即客户可以访问的服务层限制了某些限制和功能。此处描述了[个定价等级。对于 Azure Active Directory，没有可以通过请求扩展的限制——它们都是固定的。](https://azure.microsoft.com/en-us/pricing/details/active-directory/)

[本页](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-quotas.html)描述了 AWS IAM 的配额。GCP 的配额和限制可以在这里找到[。对于 Azure AD，这里描述的限制是](https://cloud.google.com/iam/quotas)。尽管每个服务在哪些值是固定的或者可以扩展方面做出不同的选择，但是有一些等效的资源限制至少有助于提供一个高级别的比较:

* * *

| 资源/提供商 | 限额/配额 | 可展开的 | 最大限制 |
| --- | --- | --- | --- |
| **角色** | – | – | – |
| 自动警报系统 | 1000/账户 | 是 | 5000 |
| GCP | 300/组织，300/项目 | 不 | 不适用的 |
| 蔚蓝的 | 30 个角色/组织 | 不 | 不适用的 |
| **组** | – | – | – |
| 自动警报系统 | 300/账户 | 是 | 500 |
| GCP | 250/政策 | 不 | 不适用的 |
| 蔚蓝的 | 5000/账户 | 不 | 不适用的 |
| **用户** | – | – | – |
| 自动警报系统 | 5000/账户 | 不 | 不适用的 |
| GCP | 无限制* | 不适用的 | 不适用的 |
| 蔚蓝的 | 50000 个对象/目录 | 是 | 取决于定价层级 |
| **实例配置文件/服务帐户** | 自动警报系统 | 1000/账户 | 是 |
| 5000 | GCP | 100 | 是 |
| 未规定的 | 蔚蓝的 | 50000 个对象/目录 | 是 |
| 取决于定价层级 | 表中的值强调了每个提供商在技术架构和目标客户统计方面的一些基本差异。例如，Google Cloud 依靠 Google groups 和 Google account infrastructure 来进行用户管理，而 AWS 是一个独立的 AWS 帐户。由于其企业焦点，Azure 依赖于 Active Directory，将用户视为传统的 Active Directory 对象，并对总对象数量进行限制。 | 下一节将深入探讨每个提供商的 IAM 产品的特性，包括等效特性和尺寸的比较和对比。 | [**2021 年云状态网上研讨会**](https://go.acloudguru.com/state-of-the-cloud-webinar) 没人能预测未来，但我们请了一组非常聪明的云专家来试试。Jassy 升任亚马逊 CEO 对 AWS 来说意味着什么？今年是[多云](https://acloudguru.com/blog/business/aws-just-went-multi-cloud-and-its-only-the-beginning)之年吗？我们生动活泼、未经过滤的小组在今年的[免费点播网上研讨会](https://go.acloudguru.com/state-of-the-cloud-webinar)中发表了意见。 |

**Google users/groups are managed as part of their workspaces, and generally have different constraints* 

* * *

IAM 功能比较

IAM 的核心是管理访问和授权。每个提供商都有一个相似的目标:为其基于云的资源和服务提供一种健壮的、可扩展的方式来管理访问和授权。

* * *

[![StateOfCloudLearning](img/4a5b6e79dda96f47004b14767f756ace.png)](https://go.acloudguru.com/state-of-the-cloud-webinar)

这三个提供者中的每一个都实现了一个[基于角色的访问控制(RBAC)](https://csrc.nist.gov/glossary/term/RBAC) 系统的变体。用户承担“角色”，角色通常是访问和授权策略的预定义分组，定义了他们可以访问和不可以访问哪些资源。

* * *

## 每个提供商如何处理用户管理、配额和逻辑组织的各个方面是客户体验不同的地方。AWS 和 GCP 都有云优先的重点，而 Azure 的企业根源在围绕 Azure IAM/AD 的技术行话和设计模型中显而易见。

逻辑组织

在任何 IAM 系统中，对于给定的用户或服务实体，总会有逻辑边界和操作域。AWS、GCP 和 Azure 对此的处理略有不同。

下表描述了每个提供商及其“基本组织域”，该术语将用于描述围绕其构建限制和配额的基本组织结构，以及用户可能经常与之交互的最常见的逻辑边界:

### 供应者

基本组织领域

自动警报系统

* * *

| 账户 | GCP |
| --- | --- |
| 项目 | 蔚蓝的 |
| 组织 | 对于 AWS，配额/限额和访问界限通常属于一个帐户。虽然许多组织通常会维护多个 AWS 帐户，这些帐户在一个统一的计费和管理帐户下累计，但 API 和服务限制仍然适用于每个帐户。访问和授权策略通常仅适用于该特定帐户内的资源和服务，除非使用特定的跨帐户角色机制进行定义。 |
| 在 GCP，组织可以充当逻辑边界，但最常见的组织模型是“项目”客户可以在一个项目下部署他们所有的 Google 云资源，或者他们可以选择创建单独的项目，根据最有意义的模式将资源组织到逻辑分组中。IAM 可以用来定义每个项目的访问和授权。 | 在 Azure 中，基本单元是活动目录组织。在企业和公司 IT 部门工作过的工程师会很快熟悉术语和惯例。Active Directory 植根于最终用户计算，它的大部分设计都源于此。Azure 云产品仍然依赖于一个有效的活动目录系统来发布对用户和其他实体的访问。 |

* * *

*深入了解 IAM(身份和访问管理？ACG 有涵盖 Azur e 的 [IAM、](https://acloudguru.com/course/identity-and-access-management-for-azure) [GCP IAM](https://acloudguru.com/course/google-cloud-identity-and-access-management-iam-deep-dive) 和 [AWS IAM](https://acloudguru.com/course/aws-iam-identity-and-access-management-deep-dive) 的课程。免费开始！*

用户/组

交互式(人工)用户访问将是云服务最常见的使用模式之一。工程师需要部署服务和配置资源，分析师可能需要访问仪表板或分析数据集，业务管理员可能需要访问计费 API 和服务。

* * *

[![Level the playing field blog](img/b000e3bcc11d237fd09c6a5ceb8f9e5a.png)](https://acloudguru.com/pricing)

下表比较了 IAM 用户上的每个提供者及其各自的能力，查看了用户帐户的主要源目录，用户帐户是否可以启用非交互式访问，以及组是否可以用于应用 IAM 策略:

* * *

### 供应者

主要用户目录

非交互式访问是可能的

* * *

| 组 | 自动警报系统 | 账户 | 是 |
| --- | --- | --- | --- |
| 是 | GCP | 变化 | 需要单独的服务帐户 |
| 是 | 蔚蓝的 | 变化 | 需要单独的服务主体 |
| 是 | 谷歌维护着一个相当多样化的服务范围，用户身份可以来源于这些服务。组织通常会使用谷歌套件用户帐户来定义 GCP 资源的用户，而个人谷歌帐户也可以用于身份。对于非交互式凭据访问，GCP 要求定义单独的服务帐户。 | 亚马逊将 IAM 用户绑定到一个特定的 AWS 账户。可以授予特定的角色和权限，允许访问独立 AWS 帐户中的资源，但通常单个 IAM 用户的访问权限仅限于帐户级别。 | 虽然组织通常会将 root 用户身份分配给其组织树中没有资源调配的顶级帐户，但个人用户实际上可以使用其 Amazon.com 帐户作为 AWS 帐户的 root 用户身份。与 GCP 和 Azure 不同，AWS 不区分“服务帐户”和普通 IAM 用户:可以启用配置选项以仅允许非交互式访问，并且可以将固定凭据分配给任何 IAM 用户。 |

* * *

Azure 显然依赖于 Active Directory 进行用户帐户和身份管理。普遍的预期是，正在向云过渡的微软客户将已经拥有活动目录解决方案的内部许可，并且将在未来转向混合解决方案。然而，用户帐户也可以来自其他 Azure 和微软产品，如 GitHub、Windows Live 和 Office 365。

每个提供商为用户帐户提供组，允许逻辑组织和策略应用。不必将策略附加到每个用户帐户，可以创建像“开发”或“管理员”这样的组，并附加正确的访问和授权策略，之后可以根据需要在组中添加和删除用户。

***[修复 5 个常见的 AWS IAM 错误](https://acloudguru.com/blog/engineering/fixing-5-common-aws-iam-errors)**
在[这篇凯莎·威廉姆斯的博文](https://acloudguru.com/blog/engineering/fixing-5-common-aws-iam-errors)中深入了解 5 个常见的 AWS IAM 错误的原因和解决方法。*

角色

在任何 IAM 系统中，角色都是一个强大的概念。在 RBAC 中，默认情况下，用户身份没有对给定资源的访问权限或授权。通过某种身份验证机制，用户帐户将“承担”一个角色，并且伴随着这种承担而来的是与该角色相关联的所有访问和授权策略。

* * *

在某些情况下，经过一段预定的时间(通常是可配置的)后，用户将被要求再次进行角色验证。否则，他们的令牌将过期，用户-角色关系将终止，直到重新进行身份验证。一些角色分配会持续到手动撤销。

* * *

### 下表比较了给定平台可用的最大角色数和角色会话长度:

资源/提供商

限额/配额

可展开的

* * *

| 最大限制 | **角色** | – | – |
| --- | --- | --- | --- |
| – | 自动警报系统 | 是 | 5000/账户 |
| GCP |  | 不 | 不适用的 |
| 蔚蓝的 |  | 不 | 不适用的 |
| **角色会话持续时间** | – | – | – |
| 自动警报系统 | – | 是 | 12 小时 |
| GCP |  | 是 | 12 小时(需要 OAuth 2.0) |
| 天蓝色* |  | 是 | 模糊的 |
| IAM 角色是 AWS 中的主要身份机制，在实体需要使用权限的各种用例中使用。IAM 策略被称为“信任策略”,用于控制允许哪些主体承担角色。在这种情况下，主体通常指任何可能需要承担角色的身份，如用户或服务。 | 交互式 IAM 用户可以扮演角色来执行任何需要的操作。特殊角色(称为“实例配置文件”)可以附加到 EC2 计算实例，从而消除了在该实例上运行的任何应用程序的硬编码凭据需求。如果任何用户或服务需要访问另一个 AWS 帐户中的资源，可以将跨帐户角色访问配置为仅对第二个帐户中所需的资源和服务授予细粒度的权限。 | GCP 在处理角色的方式上与 AWS 有些不同。在 IAM 服务推出之前，GCP 的基本角色是“所有者”、“编辑”和“查看者”通过 IAM 服务，他们可以提供预定义和自定义的角色。与 AWS 不同，GCP 角色在交互式和非交互式访问之间不可互换:用户主体承担交互式访问的角色，该角色不能委派给非交互式用户，相反，服务帐户必须是非交互式访问和角色承担的承担主体。 | Azure 的角色模型比 AWS 更接近 GCP。Azure 既提供了预定义的角色，也提供了创建自定义角色的能力。与 GCP 类似，角色由用户和服务主体分别承担，分别用于交互式和非交互式访问。内置角色具有预定义的策略，而自定义角色具有与角色定义内联编写的用户定义的策略。 |

**Managing role session duration requires Azure Privileged Identity Manager, which requires an Azure AD Premium license* 

* * *

下一节将更深入地讨论策略配置的相似之处和不同之处。

**[云迁移:角色扮演游戏](https://get.acloudguru.com/cloud-migration-role-playing-game-webinar)** 成功的云迁移活动需要策略、知识和一点即兴表演——有点像龙与地下城&的游戏。加入这个独特的角色扮演练习，让专家小组成员通过真实的云迁移场景进行游戏。

策略/配置

在 IAM 服务中，策略是给定身份在访问和授权方面可以做什么和不可以做什么的实际定义。提供者在如何编写和利用策略方面有一些共同点，但也有一些显著的差异。

需要注意的一个关键相似之处是:所有三个提供者都利用 JSON 语言进行策略定义。虽然围绕必须“编写”JSON 的用户体验存在不同意见，但它为策略定义提供了一致的、被广泛接受的模型，并且可以轻松集成第三方工具用于林挺和自动化。

* * *

[![Cloud Adventure](img/a312d94930ad6b6293401f6bb5f5286d.png)](https://get.acloudguru.com/cloud-migration-role-playing-game-webinar)

下表提供了一些额外的功能比较:

* * *

### 资源/提供商

限额/配额

可展开的

最大限制

* * *

| **附保单** | – | – | – |
| --- | --- | --- | --- |
| 自动警报系统 | 10/用户、角色或组 | 是 | 20/用户、角色或组 |
| GCP | 每个角色绑定 1500 个用户或 250 个组 | 不 | 不适用的 |
| 蔚蓝的 | 每个订阅 2000 个资源角色分配，每个管理组 500 个角色分配 | 不 | 不适用的 |
| **保单长度** | – | – | – |
| 自动警报系统 | 6144 个字符/托管策略* | 不 | 不适用的 |
| GCP | 64KB 总大小，包括标题、描述和权限名称** | 不 | 不适用的 |
| 蔚蓝的 | 无限制*** | 不 | 不适用的 |
| Azure 不认为策略文档是独立于角色身份的资源:它们直接与角色一起定义，称为“角色定义”然后，将角色直接分配给用户、组或服务主体。 | 在 Azure 中，策略分为四个层次:管理组、订阅、资源组和资源。通常，每一级都是一个更广泛的访问定义。管理组级别的定义将分配所有内容，而资源级别只允许访问特定的命名资源。 | 如表格注释中所述，GCP 实际上不允许创建自定义策略。策略是根据各种 GCP 资源和服务预定义的，并且策略在策略绑定中附加到用户、组和服务帐户。如果需要多个权限范围，可以将多个策略绑定到一个实体。根据使用情况，预定义的策略可能就足够了，或者可能需要自定义绑定。但是，无论哪种情况，客户都依赖于预定义的策略和权限范围。 | AWS IAM 策略通常在整个 AWS 生态系统中有更广泛的用例集，并且在创建策略定义时有更多的自由度。AWS IAM 有多种策略类型:基于身份的策略、基于资源的策略、权限边界、组织 scp、ACL 和会话策略。 |

**AWS also lets users define “inline policies” that are directly attached to a role, user, or group. User policy size cannot exceed 2048 characters, role policy size cannot exceed 10240 characters, and group policy size cannot exceed 5120 characters*

***GCP does not allow true custom policies, rather a list of pre-defined resource policies bound to identities*
 ****Azure has no listed limit for policy size, just a fixed limit on role assignments*

* * *

最常用的策略是基于身份的:这些是附加到传统 IAM 实体的典型策略对象，如角色和 [AWS 资源组](https://acloudguru.com/hands-on-labs/using-aws-tags-and-resource-groups-2) s。基于资源的策略是针对 S3 存储桶之类的东西定义的。 [AWS 策略生成器](https://acloudguru.com/hands-on-labs/preventing-deletion-of-an-amazon-s3-bucket-using-a-resource-based-p)是一个工具，它使您能够创建控制对 AWS 资源的访问的策略。其他策略类型有更细粒度的应用，但身份和资源策略是客户花费最多时间的地方。

需要创建策略来控制对 Amazon Web Services (AWS)产品和资源的访问，比如使用基于资源的策略来防止删除 Amazon S3 存储桶

一句话:AWS、Azure 和 GCP 哪个更好？

那么在这场 IAM 对决中，哪个平台“赢”了呢？老实说，这是一个三方平局。有点虎头蛇尾？也许吧，但是每个提供商的 IAM 都是为最适合他们各自提供的服务和资源而设计的。

希望选择云提供商的组织可能不会花太多时间来评估 IAM 功能。他们转而关注哪家供应商拥有最合适、价格最优的产品组合。

* * *

通过 Azure 对企业和混合部署的关注，更传统的企业 IT 环境可能会更容易过渡到云。

## 希望部署高度可用的面向 web 的基础设施的组织需要仔细评估哪些产品最适合他们的用例。例如，希望利用托管 Kubernetes 的组织通常希望给 GCP 一个强大的外观，而那些寻求强大的无服务器产品的组织可能会选择 AWS 更成熟的产品。

归根结底，选择 IAM 更多的是选择哪个提供商的产品最符合他们的基础架构和扩展目标。

关于作者

*   *[迈克·范布斯柯克](https://mikevanbuskirk.io/)是首席 DevOps 工程师和技术内容创作者。他曾与世界上一些最大的云计算、电子商务和 CDN 平台合作过。他目前的重点是云优先架构和无服务器基础设施。*
*   Organizations looking to deploy highly-available web-facing infrastructure will need to closely evaluate which offerings best fit their use case. For example, organizations looking to utilize managed Kubernetes will generally want to give a strong look to GCP, while those looking for a robust serverless offering will likely choose AWS’s more mature offering.

At the end of the day, choosing IAM is more about choosing which provider’s product offerings align the closest with their infrastructure and scaling goals.

##### About the Author

*[Mike Vanbuskirk](https://mikevanbuskirk.io/) is a Lead DevOps engineer and technical content creator. He’s worked with some of the largest cloud, e-commerce, and CDN platforms in the world. His current focus is cloud-first architecture and serverless infrastructure.*