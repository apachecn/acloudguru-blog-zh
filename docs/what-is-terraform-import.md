# 什么是 Terraform import，为什么你不应该使用它(但无论如何要如何做)

> 原文：<https://acloudguru.com/blog/engineering/what-is-terraform-import>

在本帖中，我们将讨论“地形导入”,它的用途，为什么你*可能*不应该使用它。。。但是无论如何你可以使用它(因为我们不是你的老板)。请继续阅读！

* * *

**加速您的云计算职业生涯**

云专家让你轻松(也很棒)提升你的云事业——即使你对技术完全陌生。查看 [ACG 目前的免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)或[立即开始](https://acloudguru.com/pricing)免费试用。

* * *

## “terraform import”是做什么用的？

Terraform 是一个流行的开源工具，用于管理各种基础设施代码(IaC)，包括 T2 的云平台和 T4 的本地解决方案。(在这篇文章中，我们只谈论云管理，作为一个云专家和所有人)。

它允许您将虚拟机、数据库和网络配置等资源定义为 Terraform 代码。然后，Terraform 将这些代码转化为云中的资源。当你听迪士尼卡拉 ok 的时候，看着你的整个系统旋转起来，这是一种非常酷的感觉(或者这只是我的感觉)

![](img/32163ace62f91487ceedd63f2c97f436.png)

(What it feels like when you run `terraform apply`)

Terraform 用于创建资源和更新已由 Terraform 创建的资源——它非常擅长这一点。然而，当大多数地方第一次开始使用 Terraform 时，他们有一些手动创建的基础设施，如网络、身份和访问管理等都是常见的例子。在全新的云环境中，他们需要在其他许多事情完成之前启动并运行。

因此，通常，随着组织将越来越多的基础设施转移到 IaC，有人会问他们如何使用 Terraform 来管理那些没有被定义为 Terraform 的资源。这就是“地形导入”命令的用武之地。

“terraform import”允许您定位已经存在的资源，并将其映射到您在代码中定义的资源。

* * *

**[获取 Terraform 备忘单](https://acloudguru.com/blog/engineering/the-ultimate-terraform-cheatsheet)**
*查看排名前十的 Terraform 命令，并在我们的 [Terraform 备忘单](https://acloudguru.com/blog/engineering/the-ultimate-terraform-cheatsheet)中获得您需要的所有基本命令的完整摘要。*

* * *

## **为什么不用**`地形导入`**` ？**

避免使用“terraform import”的原因是非常实际的:这很难做到正确，尤其是对于更复杂的资源。

Terraform 旨在创建资源并管理其创建的资源。导入功能可以工作，但是在这个过程中，设置很容易被更改。

鉴于我们的使用案例是尝试导入相当基础的基础架构(网络和 IAM ),这为环境的深远中断带来了非常高的风险。如果您在导入期间中断 SSO 集成，这将影响使用该身份提供者访问环境的所有用户。同样，如果更改了网络设置，可能会导致整个 VPC 失去连接。

由于这类环境的大多数管理者不愿意接受这种风险，因此使用 Terraform 从头开始创建并行资源通常更有效，一旦配置正确，就开始逐步迁移到 terra form 资源。

例如，创建新的 VPC 和子资源，而不是导入 VPC、所有关联的子网、防火墙规则、ACL 和所有其他内容。经过地形改造的 VPC 启动并运行后，您就可以迁移虚拟机了。如果虚拟机也进行了地形改造，则应该更新 VPC 属性并重新应用。

当然，现实生活很少那么整洁，但这是一个在两个选项中选择不那么凌乱的例子。

* * *

**[为什么我们如此热爱 Terraform？](https://acloudguru.com/blog/engineering/5-things-we-love-about-terraform)**
*如果热爱这个 IaC 工具是错误的，我们就不想成为正确的。以下是我们喜欢 Terraform 的 5 个理由。*

* * *

## **如何使用 ****【地形导入】**** ？**

如果我的论点没有打动你，你决定进口现有资源是一条出路——谁知道呢，环境是王道，很可能是环境束缚了你的手脚——那么祝你好运。

运行 import 命令时，需要提供两个参数:代码中定义的资源的 Terraform 表达式，以及要导入的资源的唯一标识符。

这取决于您想要导入的资源类型，通常是名称或 id。您可以查看特定资源类型的 Terraform 文档。然后，Terraform 将云中的资源与您在代码块中定义的资源进行匹配。

但是，您需要将资源的属性与代码中描述的一致起来。一旦您更新了代码中的属性以匹配配置，您就可以运行“terraform plan”来查找您没有捕捉到的所有不匹配的属性。

一旦计划命令报告没有进行任何更改，您可以运行“terraform apply”。

在这一点上，Terraform 掌握了主动权。即使应用程序不做任何更改，对于像网络这样的核心服务来说，也可能会有许多依赖项经历服务中断。如果[出了问题](https://learn.acloud.guru/course/hands-on-troubleshooting-with-terraform/overview)，祝你好运。

但是，如果什么都没发生，那么恭喜你！您已成功将现有资源导入 Terraform management。你现在可以通过运行“terraform apply”来进行更改——此外，你还可以告诉我，我让它听起来比实际情况更糟糕。

## 了解更多关于 Terraform 的信息

想了解更多关于 Terraform 的高级用例吗？看看我的新课程，[GCP 的高级地形。如果你喜欢 Terraform，并对用 Terraform 在 GCP 构建更大、更好的解决方案感到兴奋，那么这个课程就是为你准备的。](https://learn.acloud.guru/course/advanced-terraform-with-gcp)

*   我们将介绍如何使用模块、输出、局部变量等来提升 Terraform 代码，从而创建健壮的动态解决方案。
*   然后，我们看看 Terraform 函数，让你的代码更加灵活，这样你就可以一次编写，多次应用。
*   接下来，我们对其进行测试，在完整的 CI/CD 管道中自动化您的 Terraform 代码，以从单个代码库支持多种环境。
*   最后，我们会见了 HashiCorp 家族，并了解了其他一些 DevOps 和云管理工具，它们可以确保您的 Terraformed Google Cloud 尽可能做到最好！

准备好开始了吗？[今天就注册免费试用](https://acloudguru.com/pricing)！