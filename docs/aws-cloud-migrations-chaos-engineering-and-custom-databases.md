# AWS 云迁移和混沌工程|云专家

> 原文：<https://acloudguru.com/blog/engineering/aws-cloud-migrations-chaos-engineering-and-custom-databases>

本周 AWS 有什么新消息？

*   AWS 迁移中心现在提供迁移策略建议
*   故障注入模拟器现在可以创建点中断
*   AWS SAM Accelerate 提供了一些方便的新功能
*   Amazon RDS Custom for Oracle 正式上市

请继续阅读了解更多信息！

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## 迁移中心和策略建议

当将我们的应用程序从传统的内部解决方案引入云中时，有一个屡试不爽的解决方案通常以默认结束:[提升和转移](https://acloudguru.com/blog/business/what-is-lift-and-shift-cloud-migration)。这很简单，也很有效，但是这远不是最理想的解决方案，并且不能让我们利用云的力量。那我们为什么还要继续做下去呢？

因为有如此多的其他选择，很难全部评估。

在他们关于将应用程序迁移到云的 6 种策略的博客文章中，AWS 提出了许多你的应用程序可以采用的不同途径。自从这个博客在 2016 年发布以来，AWS 现在有十几个工具和服务来帮助迁移您的应用程序。

[云架构师](https://acloudguru.com/blog/engineering/what-is-a-cloud-architect-and-how-do-you-become-one)的角色之一就是促进这些迁移并规划最佳策略。但是，评估每个应用程序、考虑 AWS 可用的工具以及平衡迁移的业务目标需要花费大量时间。这都是在实际进行试运行迁移和转移生产工作负载之前。

[AWS Migration Hub 的战略建议](https://aws.amazon.com/blogs/aws/new-strategy-recommendations-service-helps-streamline-aws-cloud-migration-and-modernization/)使用发现工具来帮助规划您当前的系统，并根据您拥有的应用程序提供建议，说明如何使用 AWS 的服务将其迁移到云中。

还有很多工作要做——复杂的应用程序需要更多的考虑，它没有解决合规性或底层硬件解决方案等其他问题，而且它仍然只能与 AWS 为迁移提供的服务一样好。

但是，如果你正在开始云迁移，并且想要做的不仅仅是提升和转移，那就试试这项服务吧。另外，执行评估是免费的，所以这纯粹是时间投资。查看 [AWS 的博客文章](https://aws.amazon.com/blogs/aws/new-strategy-recommendations-service-helps-streamline-aws-cloud-migration-and-modernization/)了解更多信息！

## AWS 故障注入模拟器和现场中断

正如沃纳·威格尔所说，“任何事情都会失败。”当您使用 EC2 Spot 实例时，中断是服务的一部分。

如果你不熟悉 [EC2 Spot 实例](https://aws.amazon.com/ec2/spot/)，它们是一种以巨大折扣价格购买 EC2 中一些未使用的计算能力的方式——高达按需价格的 90%!但是有一个权衡:当 EC2 的需求增加时，AWS 可能会关闭您的折扣现货实例。这对于数据处理等要求苛刻的可中断工作负载来说非常好，但对于关键基础设施来说却非常糟糕。

当我们构建在现场实例上运行的解决方案时，我们设计它们来承受这些中断。但是很难确切地知道实时发生的事情会如何发生，特别是因为[现场实例中断](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/spot-interruptions.html)的处理方式不同于正常的实例终止。

[故障注入模拟器](https://aws.amazon.com/fis/)解决了这个问题，它让我们在解决方案中创建有意的故障，并观察它们如何响应。随着他们宣布[故障注入模拟器现在支持点中断](https://aws.amazon.com/about-aws/whats-new/2021/10/aws-fault-injection-simulator-spot-interruptions/)，我们可以在我们的工作负载中有意触发点中断，以查看我们的解决方案将如何响应。

如果您在您的生产环境中运行 Spot 实例，这将是值得运行的，以确认您的解决方案按计划工作。您的组织可能已经有了变更管理程序，所以在您按下按钮之前，一定要让人们知道。

故意打破东西会让决策者膝盖发软，所以如果每个人都不那么急切，不要惊讶。但是，作为早期混沌工程的一个好原则，最好是知道停机将要发生，以及它会做什么，而不是等着发现什么时候真正发生故障。

以前从未在现场被打断过？查看 AWS 的这篇文章，关于处理 EC2 现场实例中断的最佳实践。它非常深入，是一个很好的开始。

* * *

*对升级感兴趣，或者从开发和运营开始您的旅程？云专家的 [AWS DevOps](https://acloudguru.com/learning-paths/aws-devops) 学习路径提供适合初学者和高级专家的定制课程！*

* * *

## AWS SAM 加速测试版

[AWS SAM Accelerate](https://aws.amazon.com/blogs/compute/accelerating-serverless-development-with-aws-sam-accelerate/) 已经进入公开预览阶段。这个新的解决方案旨在通过支持增量构建和在 AWS 上运行测试来*加速*(我知道你在那里做了什么，AWS…)无服务器应用程序的部署速度。

对于上下文，AWS SAM 目前有能力在 Docker 容器中本地调用和测试 Lambda 函数。这是非常有用的，使得测试你的解决方案变得更加容易，而不需要把它们推向生产来看它们是否工作。另一方面，Docker 容器并不等同于运行 AWS 本身。

有了这个新功能，AWS SAM Accelerate 使在 AWS 中测试您的应用程序变得更加容易，因此您在测试中看到的将更有效地反映生产情况。随着最近 [Docker 许可的变化](https://acloudguru.com/blog/engineering/docker-desktop-no-longer-free-for-some-businesses)，这对于那些希望摆脱应用程序或者至少降低许可成本的公司来说可能也是一个有用的特性。

增量构建的使用，直接通过 API 而不是 CloudFormation 堆栈工作，以及日志监控的集成，所有这些结合在一起，使 AWS 中无服务器应用程序的开发过程更加顺畅。

有趣的是，在如此渴望在云中开发之后，我们将测试买回本地机器，只是为了再次将它放回云中。

* * *

[**自动化 AWS 成本优化**](https://go.acloudguru.com/AWS-Cost-Optimization-Webinar)
AWS 为您的企业提供了前所未有的价值，但经济高效地使用它可能是一项挑战。在这个[免费点播的网络研讨会](https://go.acloudguru.com/AWS-Cost-Optimization-Webinar)中，您将了解 AWS 成本优化工具和策略的概况。

* * *

## 适用于 Oracle 的亚马逊 RDS 定制

在现代云原生数据库引擎的世界中，考虑到它可能带来的许多挑战，人们为什么仍然使用 Oracle 可能并不清楚。但它确实有很多强大的功能，比如处理交易的方式。就在几年前，当资源受到您购买的硬件的限制时，它的可定制程度是一个主要卖点。

挑战是在云的标准化世界中，高度定制的数据库通常不是本地兼容的，这意味着要么你需要改变你的数据库架构；这是一项非常昂贵且具有挑战性的任务，或者您必须自己在虚拟机上运行它。

随着 [Amazon RDS Custom for Oracle](https://aws.amazon.com/blogs/aws/amazon-rds-custom-for-oracle-new-control-capabilities-in-database-environment/) 的推出，AWS 扩展了将定制引擎版本部署到 RDS 的选项，根据您对 Oracle 部署的需要而构建，为您提供了一些您可能需要的灵活性，同时无需管理另一个 EC2 实例。

尽管我喜欢贬低 Oracle 数据库，但这与 AWS 传统上运行 RDS 的方式有很大的不同。他们认识到，一些客户在一段时间内仍会使用 Oracle，而且许多人根本没有任何改变的计划。但是有了这个新特性，您不需要改变您的数据库架构来利用 RDS 的一些增值。

在定价上， [RDS 定制版](https://aws.amazon.com/rds/custom/pricing/)比你的[典型 RDS 实例](https://aws.amazon.com/rds/oracle/pricing/)稍贵。在 us-east-1 按需运行标准 Oracle RDS 的 m5.4xlarge (16 个 vCPU，64GB RAM)每小时的价格为 1.368 美元，而 RDS Custom 的价格为 1.642 美元，高出约 20%。

如果您正在运行高度定制的 Oracle 数据库，这仍然是非常值得的，并且不要忘记:如果您需要运行一段时间，保留您的容量仍然可以提供巨大的折扣。此外，由于您需要自带许可，您还可以在那里协商折扣，并且可以降低总拥有成本，因为您不必在日常管理上花费太多时间。

### 保持最新状态！

云移动得如此之快。在撰写这篇博客后的一段时间里，*另一个*巨大的声明是由 [Babelfish 为 Aurora PostgreSQL](https://aws.amazon.com/blogs/aws/goodbye-microsoft-sql-server-hello-babelfish/) 发布的。AWS 今年已经发布了超过 1600 项服务公告，甚至在我们到达 [re:Invent 2021](https://acloudguru.com/blog/business/the-ultimate-guide-to-aws-reinvent-2021) 之前，很难跟上时代的步伐。

通过在 [Twitter](https://twitter.com/acloudguru) 和[脸书](https://www.facebook.com/acloudguru)、[上关注我们来保持联系，在 YouTube 上订阅一位云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每周更新(包括本周的 AWS)，并在 [Discord](http://discord.gg/acloudguru) 上加入对话。也可以看看我们的[免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)，每月更新！

现在，往前走，学习所有的东西。一如既往地保持敬畏，云大师们！

* * *

[![](img/aa563ce93b787834c7c648eaec24feaa.png)](https://get.acloudguru.com/securing-aws-environment-webinar)

**[保护您的 AWS 环境](https://get.acloudguru.com/securing-aws-environment-webinar)** 在[这个免费的点播网络研讨会](https://get.acloudguru.com/securing-aws-environment-webinar)中，了解如何从零开始保护复杂的 AWS 环境，并学习如何正确[审计和保护 AWS 帐户](https://acloudguru.com/blog/engineering/how-to-audit-and-secure-an-aws-account)。