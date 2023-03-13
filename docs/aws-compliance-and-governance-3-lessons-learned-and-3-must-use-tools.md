# AWS 合规性和治理:3 个必须使用的工具|云专家

> 原文：<https://acloudguru.com/blog/engineering/aws-compliance-and-governance-3-lessons-learned-and-3-must-use-tools>

在本帖中，我们将讨论 AWS 中的治理和合规性，以及亚马逊提供的服务和工具，以简化 AWS 帐户和环境的设置和维护治理和合规性。

每天都有越来越多的企业采用 AWS 云作为其运营的一部分。为什么他们不会呢？从只需点击几下按钮即可使用代码部署基础设施，到自动扩展您的基础设施以满足流量需求，AWS 提供了数量惊人的使用案例和应用程序来简化业务运营。

随着向云的过渡的继续和技术世界的发展，保护您的数据和云基础架构变得越来越重要。

加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## Accelerate your career

我们都看过新闻故事、视频和社交媒体帖子，其中一家公司遭到黑客攻击，成千上万人的凭据或个人信息被泄露。

[Get started with ACG](https://acloudguru.com/pricing) and transform your career with courses and real hands-on labs in AWS, Microsoft Azure, Google Cloud, and beyond.

IT 行业的领导者、组织和法律法规已经建立了许多标准和合规性框架，以帮助提供有关如何保护您的云的指导方针，从而避免和降低此类情况的风险。

* * *

因此，这里有一个大问题:**亚马逊提供了哪些服务和工具来简化设置和维护 AWS 帐户和环境的治理和合规性？**

We’ve all seen the news stories, videos, and social media posts where a company has been hacked and thousands of people’s credentials or personal information has been leaked.

我的目标是在我的新[AWS 课程](https://acloudguru.com/course/introduction-to-governance-and-compliance-on-aws)的治理和遵从性介绍中回答这个问题(以及更多问题)！但与此同时，我想和你分享我学到的关于 AWS 的治理和合规性的三件事，你可能会发现它们是有益的。

Leaders, organizations, and legal legislation in the IT industry have established a number of standards and compliance frameworks to help provide guidelines on how to secure your cloud to avoid and reduce the risk of these kinds of situations. 

这里有三个经验教训和三个必须使用的工具来帮助 AWS 上的合规性和治理。

相关资源

1.熟悉如何审查和调查您的 AWS 帐户中的变更

众所周知，如果您在 AWS 环境中工作，在某些时候您需要调查谁或什么对给定的 AWS 帐户进行了更改(无论是新员工还是恶意黑客。但愿是前者。。。)

这是一项非常重要的技能，首先想到的服务可能是 CloudTrail。

什么是 AWS CloudTrail？

**AWS CloudTrail** 是一项持续跟踪和记录用户活动的服务。从您在 shell 中运行的命令到 AWS 控制台中的点击，CloudTrail 都会记录下来！下图详细说明了这项有用的服务是如何工作的:

* * *

### *花絮*:在 CloudTrail 之上，您还可以使用 **AWS Config** 来监控和查看资源上的配置变化，这些变化不会从 API 调用的细节中捕获。下面的图表有助于形象化配置的工作方式:

2.不要努力工作，聪明地与 AWS 组织合作

* * *

如果您只使用一个 AWS 帐户，管理该帐户可能非常简单，但现实是大多数企业(尤其是大型企业)都有许多 AWS 帐户。

## 1\. Get comfortable with how to review and investigate changes in your AWS Accounts

保护和实施 50 多个帐户的政策是一项艰巨的任务，不适合胆小的人。不要让我开始账单混乱。好消息是有一种服务可以让你更容易处理这些事情。我说的是 **AWS 组织**。

It’s no secret that if you’re working on AWS environments, at some point you’re going to need to investigate who or what made changes on a given AWS account (and whether it’s the new hire or a malicious hacker. Fingers crossed it’s the former . . .)

This is a very important skill to have, and the first go-to service that would probably come to mind is CloudTrail. 

### **观看:如何保护您的 AWS 环境**
在这个[免费点播网络研讨会](https://get.acloudguru.com/securing-aws-environment-webinar)中，您将了解如何将复杂的 AWS 环境从零保护到安全保护。

什么是 AWS 组织？

通过 AWS 组织，您可以将 AWS 帐户逻辑分组到组织单位(简称 ou)中。

**AWS CloudTrail** is a service that constantly tracks and logs user activity. From the commands you run from your shell to the clicks in the AWS console, CloudTrail logs it all! Below is a diagram that elaborates on how this useful service works:

假设这 50 个客户中有 10 个是发展客户。您可以创建一个开发 ou，并将这 10 个客户放在一个开发 OU 下。

*Bonus Tidbit*: On top of CloudTrail, you can also use **AWS Config** to monitor and view configuration changes on resources that wouldn’t be captured from the details of an API call. Here’s a diagram to help visualize how Config functions:

开发帐户和生产帐户之间的策略和限制很可能会有所不同。

## 2\. Don’t work hard, work smart with AWS Organizations

对于一个开发帐户来说，不太可能需要运行像 U-9tb1 实例类型这样庞大的实例。事实上，大多数公司试图在开发账户上节省成本，并使用 t3.micro 这样的实例类型。

If you only work on a single AWS account, managing that account is probably pretty straightforward, but the reality is most businesses (especially large enterprises) have numerous AWS accounts. 

使用如下所示的服务控制策略(SCP ),您可以将该策略附加到开发 ou，并限制所有开发帐户只能在单个变更上使用 t3.micro 实例:![](img/7ae70fd3284a71eb4d722a5067118f54.png)

Securing and implementing policies on 50+ accounts is a daunting task not for the faint of heart. And don’t get me started on the billing mayhem. Well, the good news is that there is a service that makes all of this easier for you to deal with. I’m talking about **AWS Organizations**. 

别以为我会忘记账单的混乱。

* * *

我这么问你:当你和你的家人带着为每个人支付餐费的意图出去餐馆时，你没有要求服务员或女服务员分摊账单并用同一张卡为每个人付款，对吗？那么，为什么企业要为他们的云做同样的事情呢？

**Watch: How to Secure Your AWS Environment**
In this [free, on-demand webinar](https://get.acloudguru.com/securing-aws-environment-webinar), get a breakdown of taking complex AWS environments from zero to secure.

AWS Organizations 通过整合账单提供了完美的解决方案，可以轻松跟踪您的支出，通过合并您帐户的使用情况为您节省一点资金，最棒的是，这一切都在一张账单上。

3.利用 AWS 安全中心锁定安全性

* * *

什么是 AWS 安全中心？

当您谈论在您的环境中设置和管理安全性或合规性时，AWS Security Hub 是必备的服务之一。

### What is AWS Organizations?

您可以启用安全中心服务中提供的几个标准。一旦您启用了所需的标准，Security Hub 就会执行繁重的安全检查，并从 Inspector、GuardDuty、Macie 等其他服务中提取信息，然后获取结果并在一个全面的视图中向您呈现结果。从那里，您将有一个您可以采取的行动列表，以更好地锁定和保护您的环境。

With AWS Organizations you can logically group AWS accounts into organizational units (or OUs for short). 

还有许多其他的治理和法规遵从性服务。想了解关于 AWS 的治理和合规性的更多信息吗？来参加我的新[AWS 治理和合规性简介](https://acloudguru.com/course/introduction-to-governance-and-compliance-on-aws)课程，让我们开始学习吧！

So, let’s say out of those 50 accounts 10 are development accounts. You can create a development OU and place those 10 accounts under the one development OU. 

免费提升您的云学习水平

The policies and restrictions you put in place will more than likely differ between a development account and a production account.

您知道吗，您可以免费访问每月一次的云专家课程集？现在你知道了！看看 ACG 有什么免费的。

For a development account, it’s highly unlikely that you would need to run a juggernaut of an instance like the U-9tb1 instance type. In fact, most companies try to be cost-efficient on development accounts and use instance types like the t3.micro. 

[注册 ACG 免费计划](https://acloudguru.com/pricing)(不需要信用卡)，今天就提升你的学习水平。

With a Service Control Policy (SCP)  like the one below, you can attach the policy to the development OU and restrict all the development accounts to only be able to use t3.micro instances on a single change:![](img/7ae70fd3284a71eb4d722a5067118f54.png)

在 10 月份，你的免费帐户可以让你访问一系列安全相关的课程，包括 [AWS 身份和访问管理(IAM)概念](https://acloudguru.com/course/aws-identity-and-access-management-iam-concepts)、[云安全基础](https://acloudguru.com/course/Cloud-Security-Fundamentals)、 [Kubernetes 安全](https://acloudguru.com/course/kubernetes-security)，以及 Azure 安全简介

Don’t think for a second I forget about that billing mayhem either. 

*想跟上 AWS 的一切？[在 YouTube 上订阅云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每周亚马逊新闻和 AWS 公告。你也可以在[脸书](https://www.facebook.com/acloudguru)上喜欢 ACG，在 [Twitter](https://twitter.com/acloudguru) 上关注我们，或者在 [Discord](http://discord.gg/acloudguru) 上加入对话！*

Let me ask you this: when you go out to a restaurant with your family with the intention of paying for everyone’s meal, you don’t ask the waiter or waitress to split the bill and pay for each person with the same card, right? So why would a business do the same for their cloud? 

AWS Organizations offers the perfect solution to this with consolidating billing that makes it easy to track your spend, save you a little money by combining usage across your accounts, and the best part, it’s all on one bill. 

## 3\. Lock down on security with AWS Security Hub

### What is AWS Security Hub?

AWS Security Hub is one of the must-have services when you are talking about setting up and managing security or compliance in your environments. 

There are several standards offered within the Security Hub service that you can enable. Once you have the standards you need enabled, Security Hub does the heavy lifting of running security checks and pulling information from other services like Inspector, GuardDuty, Macie, and much more, then takes the results and presents the findings to you in a single comprehensive view. From there, you will have your list of actions you can take to better lockdown and secure your environment. 

There are many other services for governance and compliance. Want to learn more about governance and compliance on AWS? Come join me in my new [introduction to Governance and Compliance on AWS](https://acloudguru.com/course/introduction-to-governance-and-compliance-on-aws) course and let’s get to learning!

### Level up your cloud learning for free

Did you know that you can access a monthly rotating collection of A Cloud Guru courses for free? Well, now you know! Check out [what’s free at ACG](https://acloudguru.com/blog/news/whats-free-at-acg).

[Sign up for an ACG Free Plan](https://acloudguru.com/pricing) (no credit card required) and level up your learning today.

In the month of October, your free account gets you access to a collection of security-related courses, including [AWS Identity and Access Management (IAM) Concepts](https://acloudguru.com/course/aws-identity-and-access-management-iam-concepts), [Cloud Security Fundamentals](https://acloudguru.com/course/Cloud-Security-Fundamentals), [Kubernetes Security](https://acloudguru.com/course/kubernetes-security), and an [Introduction to Azure Security](https://acloudguru.com/course/introduction-to-azure-security)

*Want to keep up with all things AWS? [Subscribe to A Cloud Guru](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1) on YouTube for weekly Amazon news and AWS announcements. You can also like ACG on [Facebook](https://www.facebook.com/acloudguru), follow us on [Twitter](https://twitter.com/acloudguru), or join the conversation on [Discord](http://discord.gg/acloudguru)!*