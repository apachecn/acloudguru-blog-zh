# Amazon EC2 密钥对的新管理功能%

> 原文：<https://acloudguru.com/blog/engineering/new-management-features-for-amazon-ec2-key-pairs>

AWS 本周有什么新消息？嗯，Amazon EC2 有很多更新，EC2 密钥对获得了新的管理功能和对 NitroTMP 和 EUFI 安全引导的支持。此外，CloudWatch Events 现在可以接收亚马逊机器图像生成的通知，AWS EMEA 峰会在线注册已经开放。让我们开始吧！

* * *

**通往更好职业的钥匙**

[立即开始 ACG](https://acloudguru.com/pricing) 通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室来改变你的职业生涯。

* * *

## **亚马逊 EC2 密钥对的新管理特性**

亚马逊弹性计算云(Amazon EC2)最近获得了一些新的管理功能。

由一个公钥和一个私钥组成的[密钥对](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-keypair.html)是一对安全凭证，用于在连接到 EC2 实例时证明您的身份。使用 AWS 控制台或 CLI，您现在可以查看在您的 AWS 帐户中创建的所有密钥对的*的创建日期和公钥材料。以前，您只能查看密钥对及其分配的标签的列表。有了这项新功能，您可以审核密钥创建日期，并根据公司政策轮换密钥。*

除此之外，您现在还可以使用 [CloudFormation 模板](https://aws.amazon.com/cloudformation/resources/templates/)创建和删除密钥对。

## **EC2 支持 NitroTPM**

AWS Nitro 系统是下一代 EC2 实例的底层平台。其中的一个关键特性是 NitroTPM，这是一个可信的平台模块。这代表了专用的、独立的加密处理器的国际标准，该加密处理器被设计来执行加密操作，例如在硬件级生成、存储和控制对加密密钥的访问。

[这项技术现已可用于运行在 NitroTPM 支持的虚拟机管理程序上的 EC2 实例。这允许基于 Nitro 的 EC2 实例生成、存储和使用加密密钥，甚至不需要访问它们。它还使用 TPM 的唯一 RSA 密钥处理平台设备身份验证，该密钥被烧录到物理硬件中。](https://aws.amazon.com/about-aws/whats-new/2022/05/amazon-ec2-nitrotpm-uefi-secure-boot/)

这对于具有非常特殊的安全性要求的工作负载来说非常好，到目前为止，这些要求只能通过在您自己的硬件上运行工作负载来满足。

## **EC2 支持 UEFI 安全启动**

统一可扩展固件接口(UEFI)是另一个行业标准规范，这次是针对处理操作系统和平台固件之间通信的软件接口。

安全引导是一项功能，它使用数字签名来验证在 EC2 实例上引导和运行的软件的完整性。如果签名验证失败，它甚至会暂停启动过程，比如恶意行为者更改或篡改软件。

要开始使用，请查看 [UEFI 安全启动用户指南](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/uefi-secure-boot.html)。

## **亚马逊 CloudWatch 事件支持 AMI 状态变化**

在更多的 EC2 新闻中， [EC2 现在可以向 CloudWatch Events](https://aws.amazon.com/about-aws/whats-new/2022/05/amazon-ec2-cloudwatch-events-support-amazon-machine-images/) 发送各种 Amazon 机器映像(AMI)状态更改的通知，比如 AMI 的创建、注册和注销。

为什么这很方便？因为它允许您基于这些事件启动进一步的操作，比如触发 Lambda 自动启动一个使用新 AMI 的新实例，或者发出一个关于现有 AMI 注销的 SNS 通知。

## **在线注册 AWS EMEA 峰会**

AWS EMEA 峰会在线现已开放注册，该峰会将于 6 月 29 日举行。这个免费活动是听取 AWS 专家意见和参与分组会议、演示和研讨会的好方法。我为之激动！

### **跟上 AWS 的一切**

在 YouTube 上订阅一位云专家的每周 AWS 新闻(以及其他云提供商的新闻)。你也可以在[脸书](https://www.facebook.com/acloudguru)上喜欢我们，在[推特](https://twitter.com/acloudguru)上关注我们，或者在[不和谐](http://discord.gg/acloudguru)上加入对话！