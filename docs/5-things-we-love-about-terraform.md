# 我们喜欢 Terraform 的 5 点

> 原文：<https://acloudguru.com/blog/engineering/5-things-we-love-about-terraform>

为了纪念情人节，我认为给地球写一封“情书”听起来很合适。Terraform 远非完美(什么关系？)，带有各种有趣的锋利边缘，可以在最糟糕的时候割伤自己。但总的来说，Terraform 是大规模管理基础设施的一场革命。那么 Terraform 成为我们在 2021 年搜索次数最多的话题也就不足为奇了。在这篇文章中，我将分享我们喜欢 Terraform 的五点。

* * *

**加速您的云计算职业生涯**

云专家让你轻松(也很棒)提升你的云事业——即使你对技术完全陌生。查看 [ACG 目前的免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)或[立即开始](https://acloudguru.com/pricing)免费试用。

* * *

当然，如果没有历史悠久的浪漫建议专栏，任何以情人节为主题的文章都是不完整的:

*亲爱的特里，*

**长期读者，第一次写进来。我束手无策，不知道该怎么办。我对我的云基础架构又爱又恨，我认为这种爱正在消退。别误会，云基础设施很棒；我可以要求它提供 100 个实例，它会毫不犹豫地完成。(试着问问您的裸机数据中心吧！)**

***问题是，只是失控了。我的云基础架构乱七八糟。我花了一整天点击用户界面来设置负载平衡器，我有以指环王角色命名的实例，我很确定我们的实习生刚刚删除了我们的产品 VPC。救命啊！！！***

***–在匹兹堡手动调配***

**幸运的是还有希望议员，如果你只是读下去。–毛圈形式**

* * *

***在我们的 [Terraform 备忘单](https://acloudguru.com/blog/engineering/the-ultimate-terraform-cheatsheet)中，查看十大 Terraform 命令，并获得您需要的所有基本命令的完整摘要，以充分利用这一直观的 IaC 工具。***

* * *

## **1.声明你想要的，剩下的由 Terraform 完成**

**Terraform 的一大特点是它使用声明性逻辑来完成目标，而不是命令性的。虽然这听起来像是一个简单的语义区别，但对用户体验的影响是巨大的，这是一个主要的卖点。**

**“声明性”到底是什么意思？**

**声明式编程意味着无论是谁编写代码，都要声明他们希望程序的最终状态是什么，编译器使用自己的逻辑来确定达到该状态的最佳路径。程序员不必担心实现。**

**与命令式编程形成对比；在大多数通用语言中，如 [Python](https://acloudguru.com/blog/tag/python) ，程序员需要明确定义实现和达到期望状态所需的逻辑。**

**在 Terraform 的上下文中，[声明是关于像基础设施组件](https://www.terraform.io/language#about-the-terraform-language)这样的资源。**

**这就是 Terraform 的吸引力所在。用户不必学习一门逻辑约定过于复杂的新编程语言。他们可以简单地定义他们希望在云基础设施中看到的资源，Terraform 将自动确定应用逻辑和部署资源的正确顺序。Terraform 使用的语言 [HCL](https://github.com/hashicorp/hcl) 非常接近 JSON，这也有所帮助。**

* * *

**[**读作:云状，地形，还是 CDK？AWS 上的 IAC 指南**](https://acloudguru.com/blog/engineering/cloudformation-terraform-or-cdk-guide-to-iac-on-aws) *概述 AWS 中可用的 IaC 工具，以及如何在它们之间进行选择。***

* * *

## **2.避免尴尬的代码遭遇远程状态**

**这是一个经典的尴尬故事:两个工程师同时对同一个资源库进行更改，但没有任何东西被完全或正确地应用，接着就是一场闹剧！实际上，更像是生产中断和与 CTO 的不愉快对话。Terraform 如何帮助避免这些“尴尬的遭遇”？**

**首先，了解 Terraform 如何“了解”您的云基础架构是有帮助的。**

**它以[状态](https://www.terraform.io/language/state)存储关于它管理的资源的数据，这在基本层面上只是一个包含大型 JSON blob 的文件，其中包含 Terraform 管理的每个资源的元数据。通常，这些文件位于工程师工作站的本地。然而，当您有大型部署和需要部署和改变基础设施的几个工程师时，这确实不能很好地扩展。进入远程状态。**

**Terraform 有能力集成各种[后端](https://www.terraform.io/language/settings/backends)，提供[远程状态管理](https://www.terraform.io/language/state/remote)。通过几行配置，Terraform 部署可以设置为利用共享状态文件。为了防止上述冲突问题，远程状态后端还可以提供锁定功能。如果一个工程师[正在将变更部署到 Terraform 工作区](https://acloudguru.com/hands-on-labs/troubleshooting-a-terraform-deployment)，其他工程师将被阻止做出他们自己的变更或计划，直到最初的变更完成。**

## **3.遵守十二要素标准**

**任何构建分布式系统和部署现代应用基础设施的人可能至少听说过[十二要素](https://12factor.net/)。这 12 个因素为开发、部署和维护应用程序的最佳实践列出了一套指导原则。Terraform 提供的功能可以帮助工程团队更好地遵循这些原则。**

* * *

***查看 Kubernetes 中的[十二因素应用，了解 Kubernetes 如何帮助实现十二因素应用方法的应用设计标准。](https://acloudguru.com/blog/engineering/twelve-factor-apps-in-kubernetes)***

* * *

### **I–代码库**

**[这个因素陈述了](https://12factor.net/codebase):“一个在修订控制中跟踪的代码库，多个部署。”**

**利用 Terraform 意味着您的基础设施是用代码定义的，这些代码可以通过版本控制来提交和跟踪。现代应用程序架构通常无法分离基础设施和工作负载；使用代码来定义这两者是任何一种可伸缩性的要求。**

### **III–配置**

**[该因素表示](https://12factor.net/config):“在环境中存储配置。”**

**我们将通过引入一些其他工具来稍微欺骗一下这个工具。Terraform 能够通过传递一个 tfvars 文件读入[环境变量。使用一些模板逻辑和大多数 CI/CD 系统，您可以使用](https://www.terraform.io/language/values/variables#variable-definitions-tfvars-files)[模块](https://www.terraform.io/language/modules/develop)编写一次 Terraform 代码，并为不同的环境传递环境变量，如 QA、staging 和 prod。**

### **x–开发/生产平价**

**[该因素陈述](https://12factor.net/dev-prod-parity):“尽可能保持开发、试运行和生产的相似性。”**

**许多有助于因子 III 的特性在这里重叠。为不同的环境保持独立的定义几乎总是会导致配置漂移，并且保持这些环境之间的同质性对于保持发布速度是绝对关键的。在模块中定义应用程序基础架构，并为命名和规模变化公开某些变量，可以实现强大的自动化，这有助于实施所需的奇偶校验。**

## **4.将所有内容整合到一个代码库下**

**最近有很多关于云不可知论者或进行[多云](https://acloudguru.com/blog/business/aws-just-went-multi-cloud-and-its-only-the-beginning)部署的讨论。如果一个组织决定要同时在 AWS 和 GCP 工作，Terraform 是一个很好的工具。**

**但是，如果你不看大型云提供商，你会发现有大量其他服务和工具可以实现基础设施的几乎完全的端到端自动化。**

**例如，一个组织可以在 [AWS](https://registry.terraform.io/providers/hashicorp/aws/latest) 上部署其大部分计算工作负载，在 [Github](https://registry.terraform.io/providers/integrations/github/latest) 上部署代码库，通过 [Datadog](https://registry.terraform.io/providers/DataDog/datadog/latest) 部署监控，通过[page duty](https://registry.terraform.io/providers/PagerDuty/pagerduty/latest)部署事件管理配置。对于大多数工程团队来说，这构成了运行一个非常强大的应用程序堆栈所需的大部分云资源和服务，现在一切都可以用代码进行配置和管理。**

* * *

**[**Watch: Kubernetes + Azure，哈希公司之道**](https://acloudguru.com/content/kubernetes-azure-the-hashicorp-way)
*你有没有想过创建一种标准化的方式来部署你的应用，以及如何安全地这样做？在 Azure 上使用 HashiCorp 堆栈是一个很好的起点！在这个[免费点播的网络研讨会](https://acloudguru.com/content/kubernetes-azure-the-hashicorp-way)中了解更多信息。***

* * *

## **5.繁荣的生态系统意味着丰富的资源**

**[Terraform 今年就八岁了](https://www.hashicorp.com/resources/the-story-of-hashicorp-terraform-with-mitchell-hashimoto)。最初的开源项目在八年内取得了显著的增长和社区采用。这种势头创造了一个奇妙的第三方工具和学习资源生态系统。Terraform 的新用户有很多选择来学习关于基础设施作为代码的最佳实践。**

**Terraform 的发展使 hashi corp(Terraform 的创造者)能够为分布式系统建立一个完整的现代工具产品线，该系统具有与 terra form 的一流集成支持。Consul 和 Vault 分别是用于服务发现和秘密管理的最强大的工具。Hashicorp 还推出了 [Terraform Cloud](https://cloud.hashicorp.com/products/terraform) ，为 Terraform 部署和支持提供包含电池的托管服务选项。**

**第三方生态系统同样强大。令人敬畏的 Terraform 维护着一个书籍、教程、博客文章、工具、模块等的列表。新用户有大量的材料可以学习，也有一个活跃的社区可以参与。**

## **Terraform:有很多值得爱的地方**

**Terraform 并不完美，但有很多值得爱的地方。就像任何关系一样，你必须接受好的和坏的。希望本文表明选择 Terraform 作为 IaC(基础设施即代码)工具是不会出错的。**

**我也对未来充满期待。为了实现这一点，像 [CDK](https://github.com/hashicorp/terraform-cdk) 和[普鲁米](https://www.pulumi.com/)这样的工具将 IaC 带回命令式逻辑，允许开发人员完全使用他们选择的编程语言，将基础设施逻辑作为模块或库导入。这种新的范例潜在地提供了一些非常强大的抽象，并且可以极大地提高开发人员的生产力。**

**即便如此，我可能还是会更多地使用 Terraform，我希望它继续成长和成熟，成为基础设施管理的首选。**

### **你会喜欢的技能发展**

**想提升你的地形和开发技能吗？查看我们的 [Terraform 培训](https://acloudguru.com/training-library/terraform-training)或[顶尖开发人员技能和技术(以及如何学习)](https://acloudguru.com/blog/engineering/to-succeed-in-devops-careers-level-up-these-skills)。你还可以看到[这个月在 ACG](https://acloudguru.com/blog/news/whats-free-at-acg) 有什么是免费的。**

**通过在 [Twitter 上关注*ACG*](https://twitter.com/acloudguru)*和[脸书](https://www.facebook.com/acloudguru)，[订阅 YouTube 上的云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)，或者加入我们棒极了的 [Discord 社区](https://discord.com/invite/acloudguru)中的云对话，来了解所有关于云的事情。***

*****关于作者**
*[Mike Vanbuskirk](https://mikevanbuskirk.io/)是一名首席 DevOps 工程师和技术内容创作者。他曾与世界上一些最大的云计算、电子商务和 CDN 平台合作过。他目前的重点是云优先架构和无服务器基础设施。****