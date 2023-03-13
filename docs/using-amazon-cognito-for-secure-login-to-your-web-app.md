# 使用 Amazon Cognito 安全登录您的 web 应用

> 原文：<https://acloudguru.com/blog/engineering/using-amazon-cognito-for-secure-login-to-your-web-app>

在本帖中，我们将讨论 AWS 如何简化授权，以及如何使用 Amazon Cognito 安全登录 web 应用程序。

想象一下:你刚刚找到了一份很棒的新工作。第一天，你一大早就大摇大摆地走进来，完全是一个早起的人。(你不是，但他们还不知道。)你走进你的第一次团队站立会议，仔细地记录下一个即将到来的项目。你很快意识到你已经有了适合自己的工作。

您的团队被选中为访问公司刚刚完成的 web 应用程序的用户构建安全而简单的授权。

你马上就会知道 Amazon Cognito 是你的首选服务，但是你从哪里开始呢？还涉及到什么？幸运的是，你了解我，杰西·阿尔瓦雷斯，我会支持你的。

## 亚马逊 Cognito 是什么？

授权并不像听起来那么令人生畏。事实上，您可以利用六个 AWS 服务来完成这项工作。这些服务中的第一个是 Amazon Cognito。

Amazon Cognito 为您的 web 和移动应用程序处理认证、授权和用户管理。

Cognito 使用用户池和身份池，根据您的规范，通过直接登录或社交登录向用户授予访问权限。这意味着用户可以使用用户名和密码登录，或者通过亚马逊、脸书、谷歌或苹果等第三方登录。

* * *

**[保护您的 AWS 环境](https://get.acloudguru.com/securing-aws-environment-webinar)** 在[这个免费的点播式网络研讨会](https://get.acloudguru.com/securing-aws-environment-webinar)中，您将了解如何从零开始保护复杂的 AWS 环境，并了解如何审计和保护 AWS 帐户。

* * *

## 如何使用 Amazon Cognito 进行安全登录

1.首先，您需要创建一个用户池，并在该用户池下添加一个应用程序客户机，以便利用一个特定的域。您还将使用 Route53 AWS 的 DNS 服务、AWS 证书管理器(ACM)来创建证书、用于文件存储的 S3、EC2 实例或您希望托管应用程序的任何方式，以及 CloudFront (AWS 的 CDN 服务)。

2.一旦创建了用户池，就需要在 Route53 中配置记录。这对于确保无论您选择哪个域——无论是 Amazon 给定的还是自定义的域——都是您的记录所指向的地方至关重要。你需要确保你的 A(别名)记录设置正确。

在 ACM 中创建 SSL 证书非常简单而且非常快。

使用 CloudFront 来利用其边缘位置，并为安全站点附加您的 SSL 证书。你也需要一个 A 级的发行记录。对任何静态内容使用 S3，并确保为此设置了 A 记录。

3.配置承载 web 应用程序的 EC2 实例是这个难题的最后一部分，如果您不熟悉系统管理，这可能会很棘手。当然，这是假设您决定使用 EC2 实例来托管您的应用程序。

您需要在实例上配置和部署您的应用程序，以便成功地利用您在 Amazon Cognito 中设置的所有有用的东西。

4.最后，您需要测试您是否已经正确设置了所有内容，并使用您的域导航到网站。

希望您会看到带有登录按钮的页面，在那里，您可以注册并登录。一旦您成功登录，您就可以与您的好友击掌，享受荣耀！

* * *

## 锁定您的安全技能

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## 了解更多关于 Amazon Cognito 的信息

想了解更多关于如何使用 Amazon Cognito 的信息吗？查看我的新[亚马逊认知入门](https://acloudguru.com/course/introduction-to-amazon-cognito)课程，其中包括一个实践实验室，可以准确完成这项任务。

想免费了解更多关于 AWS 安全的知识吗？[本月的免费 ACG 课程](https://acloudguru.com/blog/news/whats-free-at-acg)提供了以安全为重点的云学习自助餐，包括 [AWS 身份和访问管理(IAM)概念](https://acloudguru.com/course/aws-identity-and-access-management-iam-concepts)、 [AWS 安全要点](https://acloudguru.com/course/aws-security-essentials)和[如何正确保护 S3 桶](https://acloudguru.com/course/how-to-properly-secure-an-s3-bucket)。只需[创建一个免费账户](https://acloudguru.com/pricing)并投入其中。不需要信用卡！

您还可以深入研究以下资源，了解 AWS 安全性:

深呼吸。一步步来。你能行的！如果你想了解更多，你知道在哪里可以找到我！

在 YouTube 上订阅一位云专家的每周更新和各种精彩内容。你也可以在[脸书](https://www.facebook.com/acloudguru)上喜欢我们，在[推特](https://twitter.com/acloudguru)上关注我们，或者在[不和谐](http://discord.gg/acloudguru)上加入对话！继续牛逼吧，云大师们！

* * *

[![](img/aa563ce93b787834c7c648eaec24feaa.png)](https://go.acloudguru.com/Leaders-Cloud-Security-Webinar)

**[看点:领导需要了解哪些关于云安全的知识](https://go.acloudguru.com/Leaders-Cloud-Security-Webinar?ajs_aid=8b2cc73f-c0e0-442b-ba6d-0eb362250ebb)**
你的业务在云端安全吗？答案很大程度上取决于你。观看 Mark Nunnikhoven 的[免费点播网络研讨会](https://go.acloudguru.com/Leaders-Cloud-Security-Webinar)，他将解决云安全的关键问题。