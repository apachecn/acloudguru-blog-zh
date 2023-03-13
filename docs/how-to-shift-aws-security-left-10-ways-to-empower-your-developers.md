# 如何将 AWS 安全性左移:增强开发人员能力的 10 种方法

> 原文：<https://acloudguru.com/blog/business/how-to-shift-aws-security-left-10-ways-to-empower-your-developers>

*在这篇文章中， [](https://acloudguru.com/blog/engineering/what-is-a-cloud-architect-and-how-do-you-become-one) [【唐·麦咭】](https://twitter.com/DonMagee)——资深[云架构师](https://acloudguru.com/blog/engineering/what-is-a-cloud-architect-and-how-do-you-become-one)、杰出的安全工程师和 [Stedi](https://www.stedi.com/) 的云安全负责人——分享了一些重要的左倾安全策略和围绕构建更好的安全态势所吸取的经验教训。此内容基于 d on 的[保护您的 AWS 环境](https://get.acloudguru.com/securing-aws-environment-webinar?) ACG 网络研讨会。任何错误都是编辑的责任。*

你可以尽你所能[减少你的爆炸半径](https://acloudguru.com/blog/engineering/ransomware-and-aws-6-ways-to-reduce-your-blast-radius)，[确保合规](https://acloudguru.com/blog/business/compliance-is-cumbersome-but-cloud-can-help)，[保护你的环境](https://acloudguru.com/blog/engineering/12-aws-config-rules-that-every-account-should-have)。但是提高安全性的最好方法之一是帮助开发者做出正确的选择和可靠的 IT 培训项目

让开发者做出正确选择的最好方法是让正确的选择变得更容易——让正确的方法比错误的方法更容易。通过这种方式，你可以授权给你的开发者，并在你的 AWS 环境中把 [AWS 安全](https://acloudguru.com/learning-paths/aws-security)转移到左边。

* * *

#### 保护您的 AWS 环境

在这个[免费点播的网络研讨会](https://get.acloudguru.com/securing-aws-environment-webinar)中，唐·麦咭给出了复杂 AWS 环境从零到安全的详细分解。

* * *

## 提高 DevOps 安全性的左移策略

为什么要授权给你的开发者？因为集中管理导致开发人员参与和部署的减少。

我们不希望安全团队接管开发人员的部分工作，或者为他们制定规则。这降低了开发人员的速度，也让他们的工作更加困难。

相反，要找到让开发人员的生活更轻松的工具。目标是停止集中化，确保开发人员成为流程的一部分。你可以通过给团队直接反馈来实现这一点。

开发者能自己做决定的时候是最好的。不要只是说“不”。要透明地说明正在做什么以及为什么要做。然后，审核结果，并根据需要进行重定向。

* * *

*云安全是您关心的问题吗？凭借 [AWS 安全认证](https://acloudguru.com/course/aws-certified-security-specialty)，您的团队将具备阿宁级别的安全技能，并为任何复杂的 AWS 项目做好准备。*

* * *

### 1.使用云层防护

[CloudFormation Guard](https://github.com/aws-cloudformation/cloudformation-guard) 易于使用，允许你编写规则(有点类似于 [AWS 配置](https://acloudguru.com/blog/engineering/12-aws-config-rules-that-every-account-should-have))。工程师可以在本地或在 [CI/CD](https://acloudguru.com/course/implementing-a-full-ci-cd-pipeline) 流程中运行 CloudFormation Guard。

*   允许工程师在本地或管道中检查合规性
*   符合 [AWS 配置](https://acloudguru.com/blog/engineering/12-aws-config-rules-that-every-account-should-have)规则
*   可以自动生成某些类型的规则

### 2.提供参考示例

*   使用默认安全配置构建公共资源的 IaC 模板
*   将模块用于更复杂的项目，如 VPC

在 Stedi，他们建立了许多可供工程师参考的例子。这包括最常见的 10 种错误配置以及如何修复它们。

### 3.调查边界权限

边界权限对工程师可以创建的 IAM 角色进行限制。

这些边界权限本质上是一个“不能做”的策略，必须附加到您在团队中扮演的任何角色上。所以你可以说，“你可以扮演任何你想扮演的角色。。。只要附上这个边界许可。”

这些权限可以是你知道你不希望你的工程师进入的所有事情——比如创建可以具有管理员访问权限的角色。你相信你的员工会做正确的事情，但你可以帮助确保他们不会意外地做错事。

### 4.使用 scp 通过限制 EC2 实例大小或禁止区域来防止错误

在最后一点的基础上，您可以使用 scp 更进一步。

在 Stedi，所有的拒绝都被传送到 Slack，这样工程师就可以看到什么时候出了问题。这样，他们就不必说，“我无法部署。这是怎么回事？”他们可以在频道中看到，“哦，我刚刚试图在 EU-西部 2 部署，这是一个禁止的区域。”他们可以看到他们在错误的地区，然后改变它。

### 5.确保开发人员在其部署中内置警报

我们希望确保开发者为他们的系统和健康建立警报。他们要对他们负责。所以才是 [DevOps](https://acloudguru.com/learning-paths/aws-devops) 。但是任何投入生产的系统都需要是可观察的。

### 6.看看 AWS 之外的安全性

这里涉及的内容很多，但是这里有一个需要考虑的事情的快速列表。

*   使用秘密检测工具
*   为机密管理、加密和部署工具等敏感事物提供通用路径
*   以代码的形式管理一切，即使这意味着构建自己的资源提供者
*   在[owasp.org](https://owasp.org/)回顾 OWASP 前 10 名
*   对所有员工进行安全意识培训
*   使用 AWS 组织划分敏感系统
*   利用第三方云安全工具
*   利用第三方评估
*   建立一个漏洞管理程序

### 7.**从写文档开始**

那么你从哪里开始呢？你从写作开始。如果你不能解释它并得到认同，你很可能无法建造它。写下你将如何实现安全并建立安全——控制，一切。

亚马逊有一些很好的例子，比如他们的 [PR/FAQ 流程](https://aws.amazon.com/blogs/opensource/working-backwards-the-story-behind-the-aws-cloud-development-kit/)以及他们的一页和六页。你也可以找到这方面的视频。试试看——这很有效！

### 8.**将所有基础设施排除在管理账户之外**

管理帐户中没有基础架构。没有！

### 9.**使用组织结构**

[org-](https://github.com/org-formation/org-formation-cli) [formation](https://github.com/org-formation/org-formation-cli) 可能是管理 AWS 账户的最大的开源软件。看看吧！

*   标准化的关键基础设施和账户创建
*   实施最低安全策略
*   允许 Stedi 在不到 10 分钟的时间内提供完全合规的新帐户

### 10.使用云安全态势管理(CSPM)

使用 CSPM。Config 与此类似。但是有很多第三方、开源和付费的选择。这将为您提供审核日志和对所有资源、合规性规则的全面了解，以及对关键问题的自动补救。

## 保护 AWS 环境需要记住的规则

*   记住:你不能保护你看不见的东西。
*   默认情况下减少公共访问。
*   在配置或你喜欢的 CSPM 中建立规则。
*   直接向您的工程师获取反馈。
*   信任，但要核实。
*   为任何规模的运营效率而设计。
*   构建具有随时间自我改进的组件的系统。
*   不要采取非常措施。
*   仅针对当前需求构建。
*   建造非凡的东西。

* * *

## **改变职业，改变企业**

学得更快。动作快点。利用我们的课程和真正的技术以及 AWS、Microsoft Azure、Google Cloud 等领域的 [IT 实践实验室](https://acloudguru.com/platform/labs)转变您的团队。