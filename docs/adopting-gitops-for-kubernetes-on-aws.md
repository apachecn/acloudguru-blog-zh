# 在 AWS 中采用 GitHub Kubernetes 的技巧

> 原文：<https://acloudguru.com/blog/engineering/adopting-gitops-for-kubernetes-on-aws>

上周，我有幸参加了在线的 [AWS EMEA 峰会。容器是峰会的一个大主题，议程上最受欢迎的话题之一是](https://aws.amazon.com/events/summits/online/emea/) [Kubernetes GitOps on AWS](https://github.com/jasonumiker/k8s-plus-aws-gitops) 与 Jason Umiker。

那么什么是 GitOps，为什么它对试图在 AWS 上运行 Kubernetes 的企业来说如此重要？

## 什么是 GitOps？

现代软件开发实践集中在三个主要活动上:

1.  使用 Git 等工具进行源代码管理
2.  使用 Jenkins 或 CodeBuild 等工具自动构建和测试应用
3.  使用 CodeDeploy 等工具实现自动化代码部署

这些活动通常组合在一起作为[持续集成管道](/blog/business/brazeal-how-your-org-predicts-your-ci/cd-pipeline)，其中构建服务监控 Git repo 并自动触发构建以响应源代码中的变化。

将自动化的理念带到下一个层次，持续部署的实践通过在新代码成功通过构建和测试阶段后立即自动部署新代码，进一步扩展了管道。

CI/CD 相结合的方法处理流程中的每一个步骤，从提交代码变更的那一刻起，一直到部署，其巨大优势是您的应用程序可以在任何环境中工作，无论是开发、集成、试运行还是生产环境！

GitOps 利用这些久经考验的原则，允许我们将相同的理念应用于处理基础设施代码(IaC)的变更。如果基础设施是作为代码来管理的，那么为什么不将代码存储在 Git 这样的源代码控制系统中，并在每次提交更改时自动触发对基础设施的更新呢？

## 为什么要使用 GitOps？

工作负载向云的[迁移大大加快了基础设施即代码作为资源调配方法的采用。像](https://acloudguru.com/blog/business/what-is-cloud-migration) [CloudFormation](https://acloudguru.com/course/mastering-aws-cloudformation) 和 AWS Cloud Development Kit (CDK)这样的工具允许你使用熟悉的编程语言，如 JSON 和 YAML，以及 Python、Java 和. Net 来编码、建模和提供云资源

Git 是许多开发人员已经在使用的工具，因此让运营和基础设施团队也参与进来是有意义的，这样每个人都可以从管理代码的一致、简化和高效的工作实践中受益。

## gitops kublantes integration

Kubernetes 支持创建、更新和删除对象的声明式方法。这意味着 Kubernetes 中所需的对象状态可以由配置文件定义。Kubernetes 部署、pods 和负载平衡器之类的服务都可以定义为代码，理想情况下，这些代码应该受到版本控制，并存储在合适的源代码存储库中，如 Git。

像 CodePipeline 和 Flux CD 这样的工具可以被配置为注意到 Git 存储库中的变化，并采取措施触发对 AWS 基础设施的更新。

[Flux CD](https://fluxcd.io/) 是一个简单的实用程序，运行在您的 Kubernetes 集群上。每次您想要更新您的应用程序时，Flux CD 会定期从您的 Git 存储库中提取代码更改并为您应用这些更改，而不是手动运行类似 的命令。

默认情况下，Git 拉取频率设置为 5 分钟，但是您可以使用以下命令告诉 Flux 立即同步更改:Flux CTL sync–k8s-FWD-ns Flux

## 针对 AWS 中的 Kubernetes 工作负载采用 GitOps 的 5 个技巧

现在我们已经有了一些背景知识，让我们来浏览一些技巧，以便在您的 Kubernetes 部署工作流中充分利用 GitOps。

### 1。使用 Git 作为你的真理来源

使用 Git，你可以跟踪代码变更的全部历史。这意味着您将了解谁做出了更改，他们更改了什么，他们何时做出了更改，为什么需要更改，以及谁批准了更改。当然，这意味着确保人们在提交变更时包含适当的评论是非常重要的，引用与功能请求或 bug 相关的标签也是很好的实践。

### 2。每个环境使用一个 Git 分支

合并到分支的变更可以触发相应环境中的部署。您还可以考虑每个开发人员都有他们自己的分支，这样他们可以独立地迭代他们自己的变更，并且在准备好的时候将变更合并到开发或集成环境中，并根据其他人的变更进行测试，最终在准备好发布到生产环境时合并到生产分支中。

### 3。实践适当的变更管理

在你的拉式请求机制中，对每一项变更都要实施同行评审。如果你把你的生产环境想象成一座城堡，那么让 Git 成为你的吊桥。强制所有变更通过 Git 中的同行评审过程，并配置您的管道，以确保所有变更在发布到生产之前都通过了集成测试。这样，只有成功测试的更改才能进入 prod，确保您的应用程序可以在任何环境下工作。

### 4。用 Git 回滚

使用 Git，你需要做的唯一一件事就是恢复到之前的提交！例如，您可以使用类似于 git revert HEAD 的命令来回滚最新的更改并返回到之前的提交。

### 5。自动化一切

当然，最终目标是让一切自动化，这样 Git repo 中的任何变化都会被检测到，并触发相应环境的更新。Flux CD 是一个工具，它监视您指定的所有容器映像存储库，检测新映像，触发部署，并自动更新您的 Kubernetes 集群所需的运行配置。所以它基本上确保了 Kubernetes 集群的状态与您在 Git 中提供的配置相匹配。

对于 Kubernetes 之外的任何资源，如 RDS 数据库或 EC2 实例，您可以使用 CodePipeline 来自动触发使用 CloudFormation 应用的更改。

### 使用 GitOps 管理 Kubernetes】

在 AWS 中使用 GitOps 方法来管理您的 Kubernetes 基础设施是一个自然的选择。

你的应用可以在任何环境下运行。

您的开发和运营团队使用相同的工具。

你掌控着你的环境，你了解每一项变革的“批准者、批准内容、批准原因、批准时间和批准人”。此外，您还可以在需要时回滚到已知且可信的早期状态！

### 想要更多的食物吗？