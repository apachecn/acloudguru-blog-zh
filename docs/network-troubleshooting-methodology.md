# 网络故障排除方法:快速指南|云专家

> 原文：<https://acloudguru.com/blog/engineering/network-troubleshooting-methodology>

排除网络故障是你能掌握的最重要的技能之一，因为它能让你把你的环境提升到一个新的水平。我喜欢把网络想象成流入更大河流的小溪。

* * *

### **学习网络基础知识**

您是否对网络感兴趣并需要一个起点，或者希望温习基础知识？我们的“[网络基础](https://acloudguru.com/course/networking-foundations)”课程将带您了解基本的网络概念，无需任何先验知识。

* * *

## 我应该从哪里开始网络故障排除过程？

就像一条小溪，你的网络可能会意外或故意堵塞。当你在你的溪流中时，你需要注意大坝或碎片。在您的网络中，安全组、NACLs 和可路由路由器就像水坝和碎片，使水向特定方向流动。大坝，或有意的规则，将水引向有助于电力或灌溉的方向，而碎片，或意外或恶意的规则，可能会意外地阻断水。当您遇到连接问题时，这些是查找问题的第一步。

### 什么是安全组？

安全组控制相对于您的资源的流量方向。例如，如果您有一个需要连接的 EC2 实例，那么您应该为您的 IP 地址的端口 22 或 3309 设置一个规则，以允许您(并且只有您)连接到该资源。

### 什么是 NACLs？

NACLs 是帮助保持您的环境安全的防火墙。它们控制您环境的入站和出站规则，允许流量流入或流出您的环境。

### 什么是路由表？

路由表通过允许您连接到其他 VPC 来控制您环境的流量，这些 VPC 通过网关连接到为您提供端点的其他资源。有两种类型的网关:过境和互联网。中转网关将您的 VPC 连接在一起，因此您可以将内部或其他设备连接到您的云设备。互联网网关允许您连接到互联网。

当您组合这些服务时，您可以确保您的环境安全，同时确保您可以连接到您需要的一切。

## 网络故障排除难吗？

网络是复杂的，并且一直在变化。[诊断网络问题](https://acloudguru.com/blog/engineering/ask-the-experts-10-cloud-migration-challenges)需要多种知识、对细节的精确关注以及出色的解决问题的技巧。一旦你知道在哪里寻找和寻找什么，就很容易完成问题的鉴别诊断。你只需要确保从小处着手，沿着一条清晰的道路前进。

* * *

### **了解更多 AWS 网络连接故障排除技巧**

无论您是解决方案架构师、系统运行工程师还是开发人员，您都有可能在云计算之旅的某个阶段遇到网络连接问题。学习如何[快速识别和解决 AWS](https://acloudguru.com/blog/engineering/top-5-tips-for-troubleshooting-network-connectivity-in-aws) 中的网络问题是一项伟大的技能，将在你的整个职业生涯中为你服务。

* * *

## 网络问题的三个最常见原因是什么？

### 港口关闭了

假设连接没有来自外部的任何问题，您的 NACLs 和安全组控制着通过您的环境的流量。检查您的安全组或 NACLs 中允许您首先连接的规则。在 Windows 设备上，从端口 3389 查找 RDP 规则。在 Linux 设备上，使用您的 IP 地址在端口 22 上查找 SSH 规则。

### 规则不会应用于所有群组

只要您有适当的协议或规则，就很容易连接到您的设备。规则经常被遗漏，因为它们是在控制台的 EC2 部分配置的，需要添加到每个单独的组中。最常见的问题之一是向一个组添加规则，而不向另一个组添加规则。

### 交通被规则堵塞了

另一个你应该注意的连接问题是你的 NACLs 和路由表，它确保只有你想要或需要的流量才被允许进出你的网络。你需要这样的东西，如服务器，如果你是一个或几个网站的主机。您还应该确保您没有多余的规则，这些规则会使您的环境变得更加复杂。

## 在哪里可以获得网络故障排除的更多帮助？

关于网络的 [AWS 白皮书](https://aws.amazon.com/whitepapers/?whitepapers-main.sort-by=item.additionalFields.sortDate&whitepapers-main.sort-order=desc&awsf.whitepapers-content-type=*all&awsf.whitepapers-global-methodology=*all&awsf.whitepapers-tech-category=tech-category%23networking-content-dev&awsf.whitepapers-industries=*all&awsf.whitepapers-business-category=*all)提供了来自 AWS 专家的有价值的深入信息。但他们可能需要一段时间来梳理。对于特定问题的答案，[网络工程堆栈交流](https://networkengineering.stackexchange.com/)是一个网络工程师就网络问题进行合作的论坛。

* * *

### **准备 AWS 认证高级网络-专业 2020 考试**

在本课程中，我们将介绍获得 [AWS 高级网络专业认证](https://acloudguru.com/course/aws-certified-advanced-networking-specialty-2)并成为 AWS 网络专家所需了解的 AWS 网络和相关服务领域