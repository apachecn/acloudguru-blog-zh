# Terraform 1.0 版本对您来说意味着什么？

> 原文：<https://acloudguru.com/blog/engineering/what-does-the-terraform-1-0-release-mean-for-you>

Terraform 是我们复杂部署和多云架构饮食中的现代主食，其采用率每天都在增加。那么，当 HashiCorp 宣布他们将推出 1.0 版本时，这对我们这些用户来说意味着什么呢？

## 什么是 Terraform？

[HashiCorp Terraform](https://www.terraform.io/) 是一款基础设施即代码(IaC)工具。简单地说，它允许您编写一个配置文件，解释您需要为一个解决方案设置的所有基础设施，Terraform 指出如何将它们组合在一起。无论是在 AWS 中提供负载平衡器，在 Linux 服务器上安装软件包，还是在 Azure 中提供数据仓库解决方案，Terraform 都可以做到。

你可能也熟悉其他 IaC 工具，尤其是云中的工具，比如 [AWS CloudFormation](https://acloudguru.com/course/introduction-to-aws-cloudformation) ，或者 [Azure 的 ARM 模板](https://acloudguru.com/course/build-and-deploy-azure-templates)。Terraform 的设计完全不受云的限制，因此您可以使用相同的项目跨多个平台部署您的基础架构。有了活跃的开发人员社区，您可以使用任意数量的允许 Terraform 跨多个系统提供服务的提供商。你甚至可以用它从多米诺骨牌上订购比萨饼。

Terraform 是开源软件，可以轻松下载并在您的服务器上运行，或者通过 HashiCorp 的商业产品与 [Terraform Cloud](https://www.terraform.io/cloud) 一起运行。

[![Terraform Cheatsheet](img/079f543cc60333160171f62053f9585d.png)](https://acloudguru.com/blog/engineering/the-ultimate-terraform-cheatsheet)

*Don’t run in terror from Terraform! Download our [Ultimate Terraform Cheat Sheet](https://acloudguru.com/blog/engineering/the-ultimate-terraform-cheatsheet) now.*

## 没有新功能

等等，什么？没错。典型地，一个主要的软件版本发布会遇到许多新的闪亮的特性需要探索。哈希公司采取了更加冷静的方法。

Terraform v1.0.0 的最新版本包含大量小补丁、稳定性修复和其他例行更新，但没有显著的增加。事实上，Hashicorp 已经宣布，所有 1.0.x 版本都将纯粹是为了解决现有的 bug，进行小的更新。任何新特性都将在未来计划的次要版本 1.1.0 中出现。

那么…这个版本有什么特别之处呢？

## 成熟的里程碑

开发人员将 1.0 版本视为一种完成状态，在这种状态下，它的特性和稳定性被认为已经可以普遍使用了。每个供应商对待 v1 里程碑的方式都不一样，Hashicorp 也不例外。当他们在 2017 年发布 HashiCorp Packer v1.0 时，HashiCorp 描述了他们认为的“ [A HashiCorp 1.0](https://www.hashicorp.com/blog/packer-1-0#a-hashicorp-1-0) ”，他们现在用它来定义 Terraform v1.0 的发布:

*   广泛部署
*   主要用例得到理解和很好的支持
*   定义良好的用户体验
*   该产品的技术架构是成熟和稳定的

拥有超过 1 亿次下载、120，000 名 Terraform Cloud 用户、1，500 名开发贡献者、100，000 名 Terraform 学习网站月用户以及 1，000 多家各种技术平台的不同提供商，Hashicorp 有理由判断他们已经达到了标准。这个决定背后的意义比简单的技术更新更有意义。

事实上，它与正在进行的 HashiCorp 会议一致， [HashiConf](https://hashiconf.com/) (特殊名称)也不是巧合。

## 确定的发布寿命

像大多数开源软件一样，保持版本同步是一项挑战，Terraform 也不例外。任何人都不喜欢通过更新来维护受支持的部署并完成关键修复的生产噩梦。

在他们的博客文章“[宣布 HashiCorp Terraform 1.0 正式上市](https://www.hashicorp.com/blog/announcing-hashicorp-terraform-1-0-general-availability)”中，HashiCorp 承诺所有 Terraform v1.x 版本的维护期至少为 18 个月。在此期间，HashiCorp 将针对该次要版本发布更多补丁修复程序。对于任何在生产中运行 Terraform 的人来说，这是一个好消息，因为他们知道他们至少有一年的时间对其 Terraform 基础设施进行重大升级。

这在实践中如何将需要一些时间来观察。提供者的变更仍然受到各自开发人员的支配，但是在必要时在提供者需求中指定版本可以减轻任何问题。

## 地形的未来

Terraform 并不完美，仍有很大的改进空间。对于许多简单的部署，其他 IaC 工具可能更好。但是，如果您的解决方案或跨多个平台的部署需要一定程度的复杂性，Terraform 仍然是无可争议的领导者。

自 Terraform 最初的概念被提出以来的 10 多年里，通过在许多技术平台上的广泛发展，从小型创业公司到财富 500 强公司的客户的采用，一直到复杂的多云解决方案相对正常的时代的数百万用户，Terraform 已经开辟了一条道路，并继续引领前进的方向。

如果你是一名系统管理员、云工程师、DevOps 专家或基础设施架构师，Terraform 几乎肯定是你职业生涯未来的一部分。毫不奇怪，这仍然是我们在 ACG 最常搜索的话题之一。

祝贺 HashiCorp 的团队，项目的贡献者，以及众多提供者的开发者，是他们让 Terraform 成为如此强大的引擎！

*准备好进入 Terraform 的下一步了吗？今天就开始我们的 [Hashicorp 认证 Terraform 助理课程](https://acloudguru.com/course/hashicorp-certified-terraform-associate)！*