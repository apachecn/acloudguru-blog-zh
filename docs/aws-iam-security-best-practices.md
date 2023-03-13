# AWS IAM:安全最佳实践|云专家

> 原文：<https://acloudguru.com/blog/engineering/aws-iam-security-best-practices>

如果你让任何人描述他们的团队或组织的 AWS 帐户中有什么，你可能会得到相当一致的答案。一些 S3 桶，一些 EC2 实例，一些 RDS 集群。然而，有一个每个人都在使用，但很少有人想到提及的关键服务:AWS 身份和访问管理(IAM)。请他们描述他们的 IAM 部署，您可能会得到各种各样的答案。一些人可能会耸耸肩，一些人可能会清楚地表达精心制定的安全策略，而一些人可能会给出所有的“* * *”。

可悲的是，尽管 IAM 是 AWS 云服务的一个基本部分，但在讨论 AWS 的使用时，它往往只是被顺便考虑一下。有时，混乱和违反直觉的行为会导致组织拥有复杂、难以管理的 IAM 基础设施。这给整个公司及其数字基础设施带来了明显的安全风险。

幸运的是，工程组织可以采取一些简单的步骤来确保他们的 IAM 架构具有更强的安全性。

* * *

**通往更好职业的钥匙**

[立即开始 ACG](https://acloudguru.com/pricing) 通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室来改变你的职业生涯。

* * *

## 我是什么？

在我们深入 IAM 安全最佳实践之前，让我们快速回顾一下 IAM 实际上是什么，以及它如何适应 AWS 服务。如果您想更深入地了解 IAM 的基础知识，[本课程为 IAM 概念提供了很好的介绍](https://acloudguru.com/course/aws-identity-and-access-management-iam-concepts)。

基本上， [IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html) 是一个基于角色的访问控制(RBAC)系统。几乎所有 AWS 服务的访问和授权都是通过 IAM 定义和发布的。与任何 RBAC 一样，IAM 基于角色或身份的概念授予访问权限。通过策略为角色分配权限，以执行各种任务和访问服务。

在 IAM 中，角色有三种主要形式:用户、角色和组。IAM 用户是 AWS 新用户首先会遇到的，因此从那里开始我们的最佳实践是有意义的。

## IAM 安全最佳实践-基础

保护 IAM 不需要复杂的安全措施或复杂的监控系统。您可以立即采取一些基本步骤来显著改善您的 IAM 安全状况。

在上述基础课程的基础上，您可以利用[中级 IAM 课程](https://acloudguru.com/course/introduction-to-identity-and-access-management-iam)进一步了解 IAM 并学习更高级的用法。

### IAM 根用户

IAM 根用户是首先要关注的事情之一。直接借用 [AWS 指南](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html):

我们强烈建议您不要在日常任务中使用 root 用户，即使是管理任务。相反，请遵循最佳实践，仅使用 root 用户来创建您的第一个 IAM 用户。然后安全地锁定根用户凭据，并使用它们来执行少量的帐户和服务管理任务。

root 用户是 AWS 帐户或组织中的顶级身份。它不仅可以完全访问所有服务，还可以控制计费和其他管理功能。将其用于常规任务会使其面临潜在的危害，这将是灾难性的，在多帐户部署中更是如此。

如果您当前使用的是 IAM root 用户，您应该立即:

1.  为管理和技术工作创建一个单独的 IAM 用户。
2.  禁用并删除 root 用户可能拥有的任何凭据对。

根用户与日常访问的进一步逻辑分离可以通过[多个 AWS 帐户、AWS 组织和合并计费](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/consolidated-billing.html)来实现。AWS 提供了关于使用多个帐户的[最佳实践指南](https://aws.amazon.com/organizations/getting-started/best-practices/)，但简单的第一步是在您的主帐户中创建一个 [AWS 组织](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_tutorials_basic.html)，并创建第二个帐户来存放正在使用的实际基础架构和托管服务。

第一个帐户将包含能够访问计费和顶级管理的关键功能的根用户。但是，它不包含基础设施或活动的服务端点，大大减少了潜在的攻击面。

第二个帐户将包含实际的基础架构，但是在出现妥协的情况下，您仍将保留对组织的顶级控制，并且可以与 AWS 支持合作来重新保护您的资源。

### 强制 MFA

遵循减少潜在威胁的主题，任何帐户的 IAM 用户都应该始终启用多因素身份验证(MFA)。 [AWS 支持虚拟和硬件 MFA 令牌](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable.html)，为用户访问提供了关键的额外安全层。可以应用策略来防止在没有有效 MFA 身份验证的情况下访问任何资源，从而在帐户受到威胁的情况下限制爆炸半径。

### 最坏的情况是什么？

那么，如果这些措施没有实施，潜在的风险是什么？不对用户帐户实施 MFA 会使他们更容易受到攻击。如果其中一个用户帐户拥有管理员级别的权限，潜在的损害可能会很严重。

不采取措施保护根用户帐户可能会导致组织的整个 AWS 架构受到损害，这一事件几乎肯定会造成极大的财务和声誉损失。

## IAM 安全最佳实践–高级

好了，我们已经了解了基本情况。现在，让我们来评估一些更高级的保护 IAM 的技术。如果您想了解更多，请查看我们在 IAM 上的高级深度课程。

### 利用 IAM 组

如果您的组织仍然使用 IAM 用户， [IAM 组](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups.html)可以提供一种有用的机制来简化策略创建和分配。简化用户的权限和访问控制可以通过简化管理来提高安全性。可以将这些权限分配给一个“管理员”组，而不是将管理职位分别分配给每个管理员，只需凭借组成员资格就可以授予和撤销访问权限。

### 利用角色和角色假设

[IAM 角色](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use.html)是 IAM 中最强大、最灵活的概念之一。他们与 IAM 用户非常相似，除了一个非常重要的例外，即一个角色可以由多个实体承担，甚至可以同时承担。这提供了一个很好的机制来发布更多临时的、短暂的访问授权，而不用担心长期的访问凭证。

如果像 IAM 用户这样的身份通过角色的信任策略被授予作为[主体的权限，那么它就可以承担该角色。这使得访问模式更加安全，例如将 IAM 用户保持在具有最低权限的帐户中，并允许他们在单独的帐户中承担工作角色。](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_permissions-to-switch.html)

### 实施基于资源的策略

一些 AWS 资源，比如 S3 桶和 SQS 队列，有称为[基于资源的策略](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_identity-vs-resource.html)的特殊策略。与基于身份的 IAM 策略不同，基于资源的策略侧重于底层资源本身。IAM 将同时评估基于身份的策略和基于资源的策略，允许比单独使用其中一种策略更细粒度的访问控制。

### 避免内嵌策略

[内联策略](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#inline-policies)是与给定 IAM 身份直接集成的唯一策略。它们有助于确保只有特定的身份拥有给定的策略，但在大多数情况下，这种情况很少发生。内联策略的广泛使用变得难以管理，并且妨碍了在大量身份之间强制实施同质策略配置和使用。

有效管理复杂的分布式系统的一个核心原则是能够集中变更管理，这通过使用附加到身份的传统托管策略变得容易得多。

### 使用条件值配置策略

IAM 策略的一个组成部分是[条件](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_condition.html)。条件元素可以指定策略处于活动状态的一个(或多个)条件。乍一看，有人想要定义缺少安全策略的情况，这似乎是违反直觉的，但是在作为“默认拒绝”操作的策略评估的上下文中，它为进一步控制访问提供了有效的机制。

例如，IAM 管理员可以创建一个策略，授予对某些资源的访问权限，该策略将包含一个条件块，指定该策略仅在接下来的七天内有效。在七天结束时，该策略将不再适用，IAM 将拒绝对任何未在其他地方授予的资源的访问。这为经常与承包商和第三方合作的组织提供了一个非常有效的工具。

### 最坏的情况是什么？

这些准则侧重于更高级的配置，有助于简化 IAM 管理和策略管理。使用角色和角色假设大大降低了硬编码凭据被广泛访问的风险。不利用其他实践将最终导致 IAM 身份和策略的无序、不可管理的集合，从而使保持 AWS 基础设施安全的旅程更加艰难。

## 保护 IAM 对于 AWS 安全性至关重要

到目前为止，您已经知道，即使是最基本的步骤也可以显著提高 AWS 的安全性。随着越来越多的组织将其软件和数据转移到 AWS 等云平台，确保适当的安全措施和卫生措施比以往任何时候都更加重要。使用这些信息将有助于提高您的 IAM 技能，并提高贵组织的 AWS 安全性。

**关于作者**
*[Mike Vanbuskirk](https://mikevanbuskirk.io/)是一名首席 DevOps 工程师和技术内容创作者。他曾与世界上一些最大的云计算、电子商务和 CDN 平台合作过。他目前的重点是云优先架构和无服务器基础设施。*