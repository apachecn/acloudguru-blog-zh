# AWS re:Invent 2021 day 1: Top 3 公告

> 原文：<https://acloudguru.com/blog/engineering/aws-reinvent-2021-day-1-top-3-announcements>

[AWS re:Invent 2021](https://acloudguru.com/blog/tag/reinvent2021) 来了！以下是 re:Invent 第一天发布的几个最重要的公告，以及我们为什么认为它们很棒。

## 1.**亚马逊检查员获得重新启动**待遇

亚马逊[宣布](https://aws.amazon.com/blogs/aws/improved-automated-vulnerability-management-for-cloud-workloads-with-a-new-amazon-inspector/)重新推出亚马逊检查员，这可以追溯到 2015 年。该服务可用于自动化安全评估和管理，并可帮助组织满足部署到 AWS 的工作负载的安全性和合规性要求。

我们对新改进的亚马逊检查员的看法？

这很酷，但可能有点笨重。看起来他们基本上是把 Inspector(现在是 Inspector Classic)打回了原形，然后从零开始想出了一个新的来做人们在企业环境中真正需要的事情，而不会产生额外的摩擦。

有三件事非常突出:

1.  **支持容器图像** —不仅限于 EC2)
2.  **它使用 [AWS SSM 代理](https://aws.amazon.com/systems-manager/)**——不需要安装额外的客户端
3.  **自动扫描** —能够自动检测并部署到符合条件的目标上

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## 2. **亚马逊弹性容器注册中心(ECR)拉通缓存**

周一，亚马逊[宣布](https://aws.amazon.com/blogs/aws/announcing-pull-through-cache-repositories-for-amazon-elastic-container-registry/) 在亚马逊弹性容器注册中心(ECR)中通过缓存仓库支持。

这解决了企业中的另一个安全摩擦点。许多大客户都有严格的规则，比如“你不能使用我们私有系统之外的代码！”因为告诉你的安全团队“安静下来，面对现实！”也许不是最明智的做法，AWS 已经提出了一个容器图像的解决方案。AWS 现在不需要编写脚本并管理它们来更新公共图像的副本，而是自动神奇地做到了这一点。还不错！

另外，AWS 运行起来可能真的不需要任何成本，因为毫无疑问会有数百个`nginx:latest`副本，而他们只需要存储一个。

## **3。AWS 物联网 Greengrass 集成 SSM** 

去年，AWS 推出了 AWS 物联网 Greengrass 2.0，该公司将其描述为“一种开源的边缘运行时和云服务，用于构建、部署和管理设备软件和应用程序。”现在，AWS 已经[推出了](https://aws.amazon.com/blogs/aws/new-securely-manage-your-aws-iot-greengrass-edge-devices-using-aws-systems-manager/)使用 AWS 系统管理器(SSM)安全管理您的 Greengrass edge 设备的能力。

这是一个非常基本的命题:物联网很难管理，所以 AWS 做了 Greengrass。物联网更难大规模管理，因此 AWS 将其与 SSM 集成在一起。

理论上，现在您可以使用相同的工具大规模管理您的服务器和物联网设备。相当牛逼！你已经可以通过各种定制方式做到这一点，但 AWS 再次简化和精简了流程——让客户专注于“让事情做起来很酷”,而不是无差别的繁重工作。

## 跟上 AWS 的一切:发明 2021

查看 [ACG 和 Pluralsight re:Invent 内容中心](https://www.pluralsight.com/reinvent-2021)以了解 re:Invent 2021 的所有信息。

你也可以在推特上关注 ACG，在 T2 关注脸书，在 YouTube 上订阅云专家，了解你能掌握的所有关于 2021 年的更新。

加入我们令人敬畏的 [Discord 社区](https://discord.com/invite/acloudguru),与 AWS 培训架构师和其他志趣相投的阴云密布的人进行数字交流。