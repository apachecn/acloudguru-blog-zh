# 云中的 DevOps 工具——亚马逊网络服务|云专家

> 原文：<https://acloudguru.com/blog/engineering/devops-tools-cloud-amazon-web-services>

将 DevOps 称为 2018 年的一场革命可能是一种伤害。革命已经发生，DevOps 牢牢地扎根于当今信息技术的运行方式中。然而，我们可以谈一谈 DevOps 的发展，这种发展的驱动因素是主要的云供应商。每一个都有各种工具和服务，允许您在云中应用 DevOps 的概念。今天，我们将看看亚马逊网络服务在这个领域提供了什么。通过获得 [AWS DevOps 认证](https://acloudguru.com/course/aws-certified-devops-engineer-professional)掌握您的 DevOps 知识。

## 自动化

除了重新定义完成 IT 工作的方式，消除运营(基础架构和管理)和开发之间的传统分工之外，DevOps 还帮助组织自动执行手动任务并管理复杂的大规模环境。尽管有许多工具可以帮助实现这种自动化(Jenkins、Puppet、Chef、Salt 和 Ansible，仅举几个例子)，但在云环境中的实现过去更“传统”。您通常将软件(社区版或企业版)安装在一个映像上，并按照您在本地部署所有物理或虚拟基础架构时的方式使用它。现在，每个主要的云供应商都在他们的特性集中提供了这些工具。

## 与 AWS 的持续集成和交付

无论您是需要构建、测试和部署您的应用程序源代码，还是仅仅为了安全地存储它，Amazon Web Services 都有许多您可以利用的特性。一些最常见的是:

### AWS 代码管道

这允许您使用您想要的任何过程触发器快速构建、测试和部署应用程序代码。代码部署和测试的自动化意味着您的环境在每次构建时都保持一致。

### AWS 代码构建

这项完全托管的服务将编译、运行和测试您的应用程序代码，并为您提供可部署的包。一旦您设置了所需的功能，它将处理任何所需的配置、扩展和管理。

### AWS 代码部署

简单地说，这将自动将代码部署到您想要的任何实例(云或内部)。这加快了您的组织向您的企业交付附加功能的速度，并避免了与部署相关的典型停机时间。

### AWS CodeStar

如果您只想关注 AWS，CodeStar 可以帮助您在 AWS 服务和实例上开发、构建和部署应用程序。它将允许您的组织在一个地方管理整个生命周期。

## 微服务

如果您的组织在开发运维及持续集成的道路上走得有点远，AWS 还提供微服务来帮助您，包括:

### 自动气象站λ

Lambda 允许你完全不需要部署典型的基础设施就可以运行你的代码。您只需上传您的应用程序代码，其他一切都将根据您指定的使用和缩放规则进行处理。

### 亚马逊 EC2 容器服务(ECS)

如果您正打算使用或已经在使用容器， [Amazon ECS](https://linuxacademy.com/blog/amazon-web-services-2/deploying-a-containerized-flask-application-with-aws-ecs-and-docker/) 将允许您在高度可伸缩的环境中利用 Docker 投资，同时降低管理大型容器化应用程序集群的复杂性(不久也将支持 Kubernetes)。

## 平台即服务

如果您需要混合实现，并且在工具和内部流程方面有大量投资，那么您可以在更传统的平台即服务(PaaS)模型中使用 AWS。将基于 web 的应用程序部署和管理到生产环境已经简化:

### AWS 弹性豆茎

您可以在 Elastic Beanstalk 上轻松地部署和扩展您的应用程序(基于您决定的规则)。该服务支持用 Java 编写的应用程序。NET、Node.js、Ruby、Go、Python、PHP，当然还有 Docker，使用 Apache、IIS 或者 [Nginx](https://linuxacademy.com/blog/devops/announcing-the-nginx-deep-dive/) 这样的标准 web 服务器。

## 结论

DevOps 是如何在 2018 年完成的，就这样。革命结束了，但这并不意味着一切都解决了。这篇文章旨在成为三个讨论的第一个，讨论每个主要的云供应商如何在其环境中接受并帮助促进 DevOps。下周，我们将讨论[微软是如何在 Azure](https://linuxacademy.com/blog/devops/devops-tools-in-the-cloud-microsoft-azure/) 中实现 DevOps 的(不仅仅是针对 Windows 用户)。**请在下面给我们留言，分享您在本地或云中使用 DevOps 的体验！**

### 希望提升您的云计算技能？[探索我们的课程](https://linuxacademy.com/library/type/Course/)并开始您的[7 天免费试用](https://linuxacademy.com/pricing/)以启动您的学习！