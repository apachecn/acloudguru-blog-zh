# AWS 网络连接故障排除的 5 大技巧

> 原文：<https://acloudguru.com/blog/engineering/top-5-tips-for-troubleshooting-network-connectivity-in-aws>

使用 AWS 时需要学习的最有用的技能之一是如何解决网络连接问题。无论您是[解决方案架构师](https://acloudguru.com/course/aws-certified-solutions-architect-associate-saa-c02)、[系统运行工程师](https://acloudguru.com/course/aws-certified-sysops-administrator-associate-8Lkj)，还是[开发人员](https://acloudguru.com/course/aws-certified-developer-associate)，您都有可能在云之旅的某个时候遇到网络连接问题。学习如何在 AWS 中快速识别和解决网络问题是一项伟大的技能，将在你的整个职业生涯中很好地为你服务。

以下是我一路走来学到的 5 大技巧。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

1.有条不紊

VPC 可能非常复杂，因此在排除网络连接问题时，最好有条不紊地进行。

## VPC 中的任何组件都可能配置错误，并且可能是连接问题的潜在原因。

考虑这样一个场景，您有一个 EC2 实例需要执行一个 **yum update** ，但是该命令失败了，因为该实例无法访问互联网。

在解决此类问题时，创建一个显示 VPC 配置的图表会有所帮助，如上图所示。这将帮助您识别网络流量的来源(实例)和目的地(internet)之间的所有组件。

Consider a scenario where you have an EC2 instance that needs to perform a **yum update**, but the command fails because the instance is not able to reach the internet. 

![Slide from Hands-on AWS troubleshooting course showing methodical approach to potential network connectivity issue](img/3c9d730c22c5a8070557be148fe0320c.png)

2.确定网络连接问题的可能原因

一旦确定了所有涉及的组件，就可以系统地检查每个组件的配置，以确定问题的原因。

## 有时，它有助于确定可能导致您正在经历的问题的原因。在处理无法连接到互联网的情况时，以下是一些可能起作用的潜在原因示例:

实例运行状况

实例配置

*   子网配置
*   安全组或网络 ACL 配置
*   路由表配置
*   互联网或 NAT 网关配置
*   请求配置和协议
*   有了详尽的列表，您就可以检查每个组件的配置，以确定根本原因。淘汰的过程！
*   *从这些 [10 个有趣的动手项目开始构建你的云计算技能，学习 AWS](https://acloudguru.com/blog/engineering/10-fun-hands-on-projects-to-learn-aws) 。*

由内而外地工作

* * *

我的建议是由内而外的工作。从实例到流量的源或目的地，反之亦然，只要对您有意义。检查每个组件的配置中是否存在任何会阻止网络通信的内容。

* * *

### 因此，在这种情况下，我将首先检查实例的配置，然后是安全组，然后是网络 ACL、路由表、NAT 网关，最后是请求本身。如果任何组件配置不正确，请修复并重新测试。

3.走捷径

跳出框框思考！或者，看看盒子里已经有的东西。如果您有一个可以比较的工作配置示例，这有时可能是找到网络连接问题根本原因的快捷方式。比较这两种配置，如果您发现了它们之间的差异，那么您可能已经找到了根本原因。

4.启用 VPC 流日志

## 流量日志捕获与试图进出 VPC 的网络流量相关的数据。它们可以很容易地从 VPC 控制台启用，也可以为单个弹性网络接口(Eni)启用。

您可以配置您的流日志来记录接受的、拒绝的或所有网络流量，并且您可以将日志发送到 S3，或者通过将它们交付到 CloudWatch 来合并它们。这是确定您的请求是否被您的网络配置阻止的好方法。

![Slide from Hands-on AWS troubleshooting course showing working configuration shortcut to potential network connectivity issue](img/4197c626211097fd13be21ab8e3a70c4.png)

下面是一个流日志条目的示例，它清楚地显示尝试的 SSH 连接被拒绝:

## 5.如果所有这些都失败了，使用 VPC 可达性分析器

[VPC 可达性分析器](https://docs.aws.amazon.com/vpc/latest/reachability/what-is-reachability-analyzer.html)是一个很棒的工具，它使你能够分析网络路径并确定它是否可达。如果路径不可达，它将提供原因的解释。因此，这是帮助识别网络中导致连通性问题的错误配置的一种非常好的方法。

要使用该工具，您只需提供流量源、目的地、协议和可选的目的地端口。可达性分析器将执行分析并报告路径是否可达。如果路径不可达，它会告诉您哪个组件阻塞了流量，这样您就可以调查并解决问题。在下面的示例中，可达性分析器已经识别出导致流量被阻塞的安全组。

*从 AWS VPC 可达性分析仪控制台*

![Slide from Hands-on AWS troubleshooting course showing example VPC flow log entry](img/adbd50ae4b694c26599fa8027ae490b3.png)

## 网络故障排除是一项需要开发的令人敬畏的技能，它会一次又一次地派上用场。当然，本文只是触及了您在使用 AWS 时可能遇到的问题的表面。

想了解更多关于 AWS 故障排除的一般信息吗？我们刚刚推出了一门全新的课程，考察 IAM、Lambda、S3、CloudFormation 以及网络故障排除的最佳实践。要更深入地了解这些其他故障排除主题，请查看[AWS 故障排除](https://learn.acloud.guru/course/hands-on-aws-troubleshooting/overview)。

To use the tool, you simply provide the traffic source, destination, protocol, and optionally a destination port. Reachability Analyzer will perform the analysis and report whether the path is reachable or not. If the path is not reachable, it’ll tell you which component is blocking the traffic, so you can investigate and fix the problem. In our example below, Reachability Analyzer has identified the security group that is causing the traffic to be blocked. 

![AWS VPC Reachability Analyzer Console](img/37359866a803b9063e5cb334b594b4f4.png "AWS VPC Reachability Analyzer Console")

*From AWS VPC Reachability Analyzer Console*

Network troubleshooting is an awesome skill to develop, which comes in handy time and time again. Of course, this article just scratches the surface of the kind of issues you might encounter when working with AWS. 

Want to learn more about troubleshooting AWS in general? We’ve just launched a brand new course which examines best practices for troubleshooting IAM, Lambda, S3, CloudFormation, as well as Networking. To get a deeper dive into these other troubleshooting topics, check out [Hands-On AWS Troubleshooting](https://learn.acloud.guru/course/hands-on-aws-troubleshooting/overview).