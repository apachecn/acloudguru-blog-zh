# 什么是 Terraform &基础设施即代码(IaC)？

> 原文：<https://acloudguru.com/blog/engineering/what-is-terraform-infrastructure-as-code-iac>

如果你刚刚开始从事软件工程，或者你已经工作了很长时间，你可能至少听说过“作为代码的基础设施”和“Terraform”这两个术语。但是它们是什么，为什么它们很重要？

Terraform 是一个基础设施代码(IaC)工具，允许工程师用代码定义他们的软件基础设施。虽然“代码”的概念对工程师来说可能并不新奇；以这种方式提供基础设施的能力是一种强大的抽象，能够大规模管理大型分布式系统。

在本文中，我们将看看什么是 Code 和 Terraform 这样的基础设施，它们如何帮助开发人员的工作，以及如何开始使用它们。

* * *

**[获取 Terraform 备忘单](https://acloudguru.com/blog/engineering/the-ultimate-terraform-cheatsheet)**
*查看排名前十的 Terraform 命令，并在我们的 [Terraform 备忘单](https://acloudguru.com/blog/engineering/the-ultimate-terraform-cheatsheet)中获得您需要的所有基本命令的完整摘要。*

* * *

## **什么是基础设施即代码？**

基础设施即代码是一种使用代码定义和管理基础设施的方式，而不是像点击 UI 或使用命令行这样的手动过程。这意味着您可以像管理应用程序代码一样管理您的基础设施，包括版本控制、自动化和协作。换句话说，作为代码的基础设施是一种使你的基础设施更像软件的方式。

从历史上看，基础设施即代码已经经历了多次迭代，从配置管理工具开始，如 [CFEngine](https://cfengine.com/) 、 [Chef](https://www.chef.io/) 、 [Puppet](https://puppet.com/) 、 [Ansible](https://www.ansible.com/) 和 [Salt](https://docs.saltproject.io/en/latest/topics/states/index.html) 。像 [Cloudformation](https://aws.amazon.com/cloudformation/) 和 [Terraform](https://www.terraform.io/) 这样的新工具采用声明式方法，关注资源的实际供应，而不是现有资源的配置。最新一代的工具专注于使用现有命令式编程语言的功能。 [AWS](https://aws.amazon.com/cdk/) 和 [Terraform](https://github.com/hashicorp/terraform-cdk) 都提供云开发套件(CDK ),而 [Pulumi](https://www.pulumi.com/) 也是使用传统软件工具供应基础设施的流行选项。

## **什么是 Terraform？**

Terraform 是一种用于供应、管理和部署基础设施资源的工具。这是一个用 Golang 编写的开源工具，由 HashiCorp 公司创建。借助 Terraform，您可以跨多个云提供商(AWS、Azure、GCP 等)管理应用的基础设施。–使用单一工具。

要开始使用 Terraform，开发人员只需下载 Terraform 二进制文件，选择将与哪个[提供商/平台](https://developer.hashicorp.com/terraform/language/providers)合作，为那个提供商创建一些[样板配置，然后他们就可以开始创建基础设施代码了。](https://developer.hashicorp.com/terraform/language/providers/configuration)

Terraform 的关键特性之一是它的声明性语法。这意味着你要定义你想要的最终状态，而 Terraform 会找出实现这一目标的最佳方式。与传统编程语言的命令式工作流相比，这可能是思维方式的一点转变——但它能够大规模管理基础设施部署，而无需软件开发中常见的陡峭学习曲线。

使用 Terraform 配置资源的典型工作流程如下:

1.  编写了一些 Terraform 配置，包括提供者定义。
2.  工作目录被初始化(这被称为根模块)。
3.  下载提供者插件。
4.  命令“地形计划”在根模块中运行，生成一个提供资源的建议计划。
5.  如果计划可以接受，则运行“terraform apply”命令并提供资源。

Terraform 在一个[状态文件](https://developer.hashicorp.com/terraform/language/state)中跟踪它所管理的资源的状态。该文件本质上是一个大型 JSON 数据结构，用于跟踪基础设施的变更建议，以及 Terraform 配置之外的实时资源可能发生的带外变更。新的 Terraform 用户通常会在他们的工作站或笔记本电脑上维护一个本地状态文件。在由多名工程师管理基础设施的规模下，状态通常被分解为多个文件，并使用 AWS S3 等服务远程存储。

Terraform 也是“等幂”的，这意味着重复的计划/应用周期不会触发资源的重新部署；只有对现有状态的更改才会反映在新的计划和应用调用中。

现在你已经了解了一点什么是 Terraform，它有什么作用，我们可以开始探索 Terraform 的“为什么”和它提供的好处。

## **terra form 有什么好处？**

利用基础设施作为代码来管理和部署基础设施资源[为开发人员和工程师带来了诸多好处](https://acloudguru.com/blog/engineering/5-things-we-love-about-terraform)。让 Terraform 成为 IaC 的首选工具还能带来额外的好处，让开发人员能够利用易于使用的工具来管理复杂的软件架构。

### **1。Terraform 配置是使用声明性范例编写的。**

理解声明性代码的最好方法是将其与大多数现代编程语言使用的更熟悉的命令式逻辑模式进行比较。

想象一个基本的 Python 程序，它接受用户输入的一系列数字，按升序打印出每个数字，然后返回所有输入的总和。程序员需要按照特定的逻辑顺序编写代码，否则程序会失败。如果程序试图在收到输入之前对所有数字求和，很可能会产生某种异常或错误。如果程序员想让数字按照正确的顺序排序，那就需要在它们被输出之前完成。

在程序的每一部分，程序员都必须明确定义程序执行时的逻辑和逻辑顺序。相反，声明性程序语法意味着程序员只需要“声明”程序的期望结束状态。编译器(在这种情况下是 Terraform 二进制文件)被编程为确定操作路径的最佳顺序，通过该操作路径，它们实现配置中描述的期望的最终状态。这在处理云提供商 API 时特别有用，因为许多云资源在创建之前依赖于其他基础资源的创建。

### **2。哈希公司配置语言(HCL)是一种领域特定语言(DSL)。**

特定于领域的语言是根据特定的用例设计的，专门处理特定应用程序或程序领域的需求和约束。

如果 DSL 的效用看起来不是很明显，那么您应该考虑最著名和最广泛使用的 DSL 之一:HTML。HTML 是一种专注于超文本领域(即互联网)的标记语言。HTML 摒弃了复杂的程序逻辑和语法，专注于内容表示的特定用例。

在 Terraform 的例子中，开发人员只需要学习少量的 HCL 语法，就可以提高工作效率。作为一种 DSL，Terraform 通过抽象出通用语言中固有的复杂性，使开发变得更加容易和高效。这并不是说 Terraform 没有更复杂的逻辑；高级用户可以使用更新的命令式结构，比如 for 循环和 if/then 逻辑。

HCl 被认为是 [JSON 语言](https://www.json.org/json-en.html)的超集，这意味着它共享相似的语法，但也具有 JSON 范围之外的附加特性。

### **3。地形被广泛采用**

当谈到作为代码工具的基础设施时，Terraform 通常被认为是行业标准。随大流并不总是好的建议，但是当涉及到技术实现时，选择一个拥有大型社区、坚实的支持基础和多年寿命的工具是至关重要的。没有人想向涉众和客户解释应用程序关闭是因为代码或平台不再受支持！

广泛采用的另一个好处是社区的集体共享知识。开发和共享最佳实践，并且可以构建支持工具和文档的生态系统。社区支持力量的一个很好的例子是 Github 上的 [awesome-terraform 知识库，这是一个工具、库、文档、博客等的精选列表。](https://github.com/shuaibiyy/awesome-terraform)

### **4。地形使不变性成为可能**

不可变的基础设施使管理复杂的分布式系统变得更容易、更安全，并允许它们更可靠地扩展。“不可变的基础设施”到底是什么意思，Terraform 是如何实现的？

考虑一个假设的场景:开发人员需要部署一些更改来修复生产应用程序。他们在本地创建更改，运行一些测试和林挺来验证更改并检查语法，现在他们已经准备好部署了。然而，要让他们的代码在临时环境中运行，他们必须更改一些配置以指向临时数据库。然后，他们需要让 QA 团队访问临时服务器。在暂存环境中，一切都正常，但是当部署到生产环境时，灾难袭来，应用程序停止提供流量服务，并发生中断。

原代码不好吗？还是舞台上的变化？因为环境和阶段之间的界限很模糊，所以几乎不可能区分。可变基础设施意味着在应用程序或其基础设施的生命周期中的任何时候都可能发生变化。

对于不可变的基础设施，构建、发布和部署阶段是分开的。一旦构建了代码变更，它们就会被打上一个不可变的 release 标签。进一步的更改或修复会导致生成新的标签。开发人员和工程师知道，在本地开发环境中进行的更改在不同的环境和部署阶段中是相同的。[12 因素 app 框架在因素 V](https://12factor.net/build-release-run) 中强调了这一模式。

### **5。Terraform 是模块化的**

模块化是各种语言和系统的一个重要特征。抽象简单接口背后的逻辑和资源是大规模管理复杂性的最佳方式之一。随着 Terraform 部署变得越来越复杂，开发人员可以考虑使用[模块](https://developer.hashicorp.com/terraform/language/modules)将各种资源封装在一个可重用的包中。

一个常见的用例是为其他开发团队提供用于测试和开发的 Kubernetes 集群。通常，在 AWS 这样的云提供商中提供 Kubernetes 集群需要大量样板配置和资源，即使使用托管服务也是如此。使用模块，配置可以隐藏在基本的配置接口后面。开发人员可以导入模块，指定模块作者提供的任何输入，并且他们可以提供完整的堆栈，而不必进行不必要的重复工作。

## 如何使用 Terraform？

尽管入门很简单，但 Terraform 是一个非常强大的基础设施供应工具。对于新用户来说，关键是从小处着手进行基本配置，然后通过代码实现基础设施的完全自动化。

新开发人员应该从简单的东西开始；没有复杂依赖链的一些基本资源。您不需要在第一天就尝试管理您的整个生产应用程序环境:尝试使用 Terraform 来管理存储部署工件的 S3 存储区，或者管理前端网站的 Google DNS 记录。

一旦你适应了，你就可以开始迭代和增加你的 Terraform 使用。第一步是从本地状态移动到带有锁定的远程状态文件。如果国家没有锁定机制，几乎不可能安全地管理有多个用户的大型平台部署。当 Terraform 计划或应用正在运行时，锁可防止其他用户进行可能导致不一致状态或损坏的更改。

现在有多个用户参与 Terraform 配置，您可以开始扩展使用范围，以覆盖越来越多的基础设施资源，包括网络、安全、CDN 等。随着基础设施复杂性的增加，可以考虑将体系结构的某些部分封装在模块中。

最后，作为 CI/CD 策略的一部分，您的团队可以开始使用 Terraform 来调配资源。CI/CD 是一个复杂的话题，我们不会在这里讨论，但是 [GitLab](https://about.gitlab.com/solutions/gitops/) 和 [GitHub](https://acloudguru.com/blog/engineering/how-to-use-github-actions-to-automate-terraform) 都为部署自动化提供了很好的包含电池的解决方案，可以与 Terraform 一起使用。Hashicorp [提供了可靠的](https://developer.hashicorp.com/terraform/tutorials/automation/automate-terraform)文档，专门针对那些考虑自动化其 Terraform 部署的用户。

## **结论**

为什么要在编写应用程序代码时通过点击和手动过程来调配基础架构？像 Terraform 这样的代码工具基础设施意味着基础设施配置可以被纳入相同的开发过程，允许测试、标准化和可伸缩性。现代基础设施即代码生态系统有各种各样的学习和入门资源。

## **想了解更多关于 Terraform 的信息？**

为什么不尝试学习 Hashicorp 认证:Terraform 助理认证？Pluralsight 提供了一个[优秀的证书准备课程](https://www.pluralsight.com/paths/hashicorp-certified-terraform-associate)，该课程会教你所有你需要知道的关于 Terraform 的知识，包括如何在你自己的项目中有效地使用它。这是了解 Terraform 的一个很好的方式，即使你最终没有参加认证考试。

## **查看其他一些伟大的地形资源**

* * *

**关于作者**
*[Mike Vanbuskirk](https://mikevanbuskirk.io/)是一名首席 DevOps 工程师和技术内容创作者。他曾与世界上一些最大的云计算、电子商务和 CDN 平台合作过。他目前的重点是云优先架构和无服务器基础设施。*