# 魔法豆茎？关于 AWS App Runner ，您需要了解的内容

> 原文：<https://acloudguru.com/blog/engineering/what-you-need-to-know-about-aws-app-runner>

开发应用程序是你创造价值的地方，而不是管理它们的部署方式。与其争论基础设施，为什么不直接写你的代码，让其他东西为你做剩下的工作呢？

多年来，云提供商一直在逐步简化这一过程。随着 App Runner 的发布，AWS 可能为他们的许多客户带来了可量化的飞跃。

## 什么是 AWS App Runner？

App Runner 用于从源代码(Node.js 或 Python)或容器中获取 web 应用程序，并将其部署到 AWS 云中。这是为数不多的一次云提供商凭直觉命名他们的产品(我正看着你， [AWS Proton](https://acloudguru.com/blog/engineering/what-you-need-to-know-about-the-new-aws-proton-service) )。

除了部署之外，它还负责保护您与 HTTPS 的连接，管理您的自定义域，扩展您的应用程序以满足需求，以及缩减应用程序以节省成本。

运行虚拟机、负载平衡器等等都被抽象掉了。[虽然与过去的几年相比，AWS 使这一切变得相对容易，但它仍然需要一些专业知识和时间。有了这个，你就可以在几分钟内编写代码并运行。](https://acloudguru.com/blog/engineering/things-you-should-know-before-using-awss-elasticsearch-service)

## App Runner 是如何工作的？

在幕后，App Builder 的核心是它构建一个[亚马逊 ECS 集群](https://aws.amazon.com/ecs/)并使用 [Fargate](https://aws.amazon.com/fargate/) 来执行你的容器。虽然这不是革命性的，但是任何对 ECS 动手脚的人都会喜欢这种避免它的能力，跳过所有额外的配置，只说“运行这个东西”。

在某些情况下，您会牺牲一些细粒度的控制，比如基于 CPU 和内存的伸缩。但在大多数情况下，你可能不担心这些。这项服务的美妙之处在于，部署代码越快越容易，越好。

App Runner 中一个非常方便的特性是[自动构建](https://docs.aws.amazon.com/apprunner/latest/dg/manage-deploy.html)特性，在这个特性中，您的应用程序可以使用部署到源代码库中的最新版本的代码自动重新构建和部署自己。虽然这在 CI/CD 世界中并不新鲜，但值得注意的是，您不需要担心代码管道或其他工具。只要勾选一个框，一切都会为你实现。

## App Runner 与其他服务相比如何？

App Runner 是不是看起来出奇的熟悉？不仅仅是你。这项服务背后的基本概念深深植根于 AWS 甚至其他云提供商的其他服务中。

### **App Runner vs AWS 弹性豆茎**

过去十年来，AWS Elastic Beanstalk 一直在做类似的事情。虽然在当时是革命性的，但它总是有一些限制，尤其是在复杂的场景中。App Runner 还带来了一些额外的功能，这些功能只是抽象了更多的部署细节。

这两种服务之间的一个关键区别是，虽然 App Runner 和 Elastic Beanstalk 都自动化了部署，但持续的管理是不同的。在 Elastic Beanstalk 中，一旦基础设施部署完毕，您就可以对其进行更多的控制。有时这可能是必要的，但是它也引入了非托管变更的范围。对于 App Runner，服务是完全管理的，消除了最大的管理开销。

### **App Runner vs AWS Copilot**

去年， [AWS Copilot](https://aws.amazon.com/containers/copilot/) 作为新的命令行工具发布，以简化 ECS 部署。虽然它有一个引人注目的利基市场，但缺乏可伸缩性仍有不足之处。(更新于 2011 年 5 月 21 日:AWS 随后发布了 Copilot 的最新版本(1.7.0 ),该版本原生支持 App Runner，并在很大程度上弥补了这一差距。感谢 AWS 计算服务副总裁 Deepak Singh 向我们指出这一点！)其他人也将 App Runner 与[亚马逊 Lightsail](https://acloudguru.com/hands-on-labs/creating-and-interacting-with-a-lightsail-instance) 进行了比较，但你无法获得相同水平的控制。

### **App Runner vs Google Cloud Run**

如果你熟悉 GCP，你不能否认这几乎是曾经强大的[谷歌](https://cloud.google.com/run) [云](https://acloudguru.com/course/google-cloud-run-deep-dive) [跑](https://cloud.google.com/run)的翻版。你是对的。AWS 已经看到了一个出色执行的想法，并说:“我们需要这个”。到目前为止，他们似乎做得很出色，除了一个潜在的重大例外。

## AppRunner 缺少哪些功能？

像所有新服务一样，AWS App Runner 似乎缺少一些有用的功能，这些功能可能会对其采用产生很大影响。

最大的一个不像 Google Cloud Run 没有“缩放至零”选项。这项功能的美妙之处在于，如果你的应用程序没有流量，你根本不用付费，它只会在需要时启动。许多生产应用程序不会关注这一功能，但对于那些很少访问的解决方案，它会将每月 0.05 美元的账单变成 5.00 美元。

一个非常奇怪的遗漏是，虽然基于代码的服务存储库支持 GitHub(谢天谢地！)，它还不支持 AWS 自己的 CodeCommit 服务。公平地说，优先考虑 GitHub 是一个令人难以置信的明智之举，以支持该服务的采用，而不是强迫用户使用 AWS 产品。

虽然存在接口端点以允许 VPC 中的资源访问并部署到 App Runner，但 App Runner 上的应用似乎没有任何方法可以访问 VPC 中的资源。这是否是一个问题很大程度上取决于您的应用程序架构。

AWS 非常善于倾听客户的意见，因此他们取得了成功，如果我们在 re:Invent 2021 或更早的时候看到新功能的繁荣，我不会感到惊讶。

## 什么时候应该使用 App Runner？

App Runner 可以让开发者的事情变得更加容易，尤其是对于不需要强大的定制基础设施的小规模项目。

从另一个角度来看，我与 Wolk Technology 的架构良好的实践主管内尔·沃克进行了交谈，他分享了他的想法:

“我们的许多中小型企业客户使用 Elastic Beanstalk 来支持他们的生产工作负载。对他们中的许多人来说，App Runner 可能是更自然的选择。我们的中小型企业客户希望发展到容器，但内部没有支持它的技术资源。我们迫不及待地想让它在悉尼地区上市，让我们的客户也能参与进来。”

如果 App Runner 团队可以构建一个“扩展到零”的特性，那么开发微服务会变得更加有趣。如果没有，我会请求 AWS 将它改名为“魔豆”。