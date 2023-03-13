# 以持续的弹性拥抱失败

> 原文：<https://acloudguru.com/blog/engineering/embracing-failure-with-continuous-resilience>

上周，我有幸参加了 AWS 伦敦峰会。议程上最受欢迎的话题之一是与韦利斯瓦·博雅的持续弹性会谈。以下是我对“持续弹性”的了解，以及它如何应用于 AWS 云中的构建。

* * *

**通往更好职业的钥匙**

[立即开始 ACG](https://acloudguru.com/pricing) 通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室来改变你的职业生涯。

* * *

## 为什么弹性很重要？

在我们生活的快节奏世界中，成功的企业依靠弹性软件的闪电般快速交付来实现其竞争优势。适者生存取决于你能多快适应并将你的产品和服务推向市场。

但是对软件配置的频繁更改也带来了潜在的风险，可能会破坏应用程序，降低服务质量，并最终失去客户。传统上，IT 和工程团队花费了大量的时间和资源来尝试防止此类中断。当我作为一名 SysOps 管理员工作时，后来作为一名解决方案架构师，这当然是我努力争取的事情。没有人愿意因为一个坏了的应用程序而在半夜被吵醒。或者因管理不善的服务中断而遭受声誉损害。

### 在构建弹性系统时，我们如何将失败转化为优势？

与其试图构建永远不会失败的系统，为什么不专注于设计和构建在不可避免的事情发生时能够快速、自动恢复的系统呢？如果我们预期系统会失败，我们可以创建精通处理失败场景的团队。这反过来又让我们能够自由地进行频繁的软件变更，因为我们知道我们的应用程序会快速恢复，我们的团队知道如何处理危机。

### 引入持续弹性

不幸的是，在它里面东西会坏掉。硬件最终肯定会坏掉。人们也会打碎东西——我们也是人！任何从事过 SysOps 或 DevOps 工作的人都有故事可讲。从简单地在错误的服务器上运行命令，到我最喜欢的关于一个系统管理员删除了 SSH 软件的故事…从服务器上我们只能使用 SSH 连接！我们都会犯错误，但是我们如何从中学习和成长比纠结于错误要有趣得多。

通过应用 DevOps 思想来构建我们系统的弹性，我们可以随着我们系统的增长和变化保持并不断提高弹性。

在他们的书*实践中的弹性工程*中，Erik Hollnagel 等人确定了在致力于持续弹性时需要开发的四种基本能力:

1.  预期
2.  监视
3.  反应
4.  学问

![](img/aa8e7f7315a2342056bb284f89752fab.png)

## 构建 AWS:实现持续弹性的四大支柱

我们可以在自己的环境中做些什么来预测潜在的故障，有效地监控我们的系统，对事件做出适当的响应，并从我们的故障中吸取教训？让我们在 AWS 的上下文中检查这四种功能。

### 1.预期

这里有一些很好的实践，可以让你预见到失败。

1.  引入代码评审来提高你的代码质量。你可以通过[亚马逊代码专家](https://aws.amazon.com/codeguru/)来自动化代码审查。该工具使用机器学习来审查和推荐改进，以优化代码质量。
2.  使用面向失败的方法设计应用程序。想象可能会出错的地方，并设计能够适应您所确定的场景的系统。对于具有许多相互通信的组件的分布式系统，使用为您的应用程序设置的适当超时限制，然后配置带有回退和抖动的重试，以便随机化重试之间的延迟。
3.  使用安全的部署实践。不可变部署包括将变更部署到与生产完全分离的全新环境中。这涉及到生产系统的零停机，当新环境准备好进行实时通信时，使用 [Route 53](https://aws.amazon.com/route53/) 将请求路由到新环境。如果需要回滚，只需更新 Route53，使其指向原始环境。AWS CodeDeploy 是一个很棒的工具，可以帮助您以这种方式自动化部署。Canary 部署是安全地推出您的更改的另一种方式。例如，您可以使用 CodeDeploy 进行部署，然后使用 Route53 或应用负载平衡器将一小部分(比如说 5%的客户流量)路由到您的新应用，并在将所有流量切换到新环境之前为少量用户进行生产测试。
4.  通过减小事件的爆炸半径来限制故障的影响。所谓的基于单元的架构是基于服务的多个实例，这些实例彼此独立运行，因此一个单元的故障不会导致另一个单元的故障。考虑基于微服务的架构、依赖于 Lambda 函数的多次调用的无服务器系统，甚至是由负载平衡、计算和数据库服务组成的烟囱式架构，它们作为一个单元独立于其他单元运行，如下图所示。

![](img/e0d48d27eab2cef4dfde0205a1fb4f24.png)

*Use a cell-based architecture to limit the blast radius of failures.*

### 2.监视

这里有一些很好的监控实践，可以帮助您识别故障。

1.  **使用日志、指标和跟踪观察您的应用**。这将帮助您在故障发生时识别故障，并执行根本原因分析。
2.  **使用 AWS 监控工具。**例如， [Amazon CloudWatch](https://aws.amazon.com/cloudwatch/) 使您能够监控应用程序日志中的错误和警告并设置警报，并且会就 CPU 利用率等时间点数字指标向您发出警报。 [AWS X-Ray](https://aws.amazon.com/xray/) 非常适合对分布式应用程序进行故障排除，实际上可以在请求通过系统的不同组件时对其进行跟踪。x 射线也是了解系统中存在延迟和瓶颈的一个很好的工具。
3.  **配置警报。**在执行 canary 部署时，配置您将在生产中使用的相同警报和指标，以便在您的新 canary 环境中出现任何部署失败时发出警报。

![](img/1030b1a96c23c57e38fadb1e240c7401.png)

*Resilience Engineering in Practice by Erik Hollnagel, Jean Paries, David D. Woods, John Wreathall *

### 3.反应

自适应能力实验室(Adaptive Capacity Labs)的联合创始人 John Allspaw(事故分析专家)表示，“能够从故障中快速恢复比减少故障次数更重要。”

这里有一些应对失败的好方法。

1.  **建立自动化机制**让您的系统快速恢复。
2.  设计事件驱动的架构，自动响应您环境中的事件。例如，您可以使用 [AWS Config](https://aws.amazon.com/config/) 来监控 S3 存储桶的权限。然后，您可以配置一个 [Amazon EventBridge](https://aws.amazon.com/eventbridge/) 规则，如果 bucket 上的访问权限发生更改，该规则将触发，然后调用单独的 Lambda 函数来更正权限并发送 SNS 通知。

### 4.学问

这里有一些从失败中学习的好方法。

1.  **重点理解问题。**在可能的情况下，实施变革，利用自动化推动持续改进。这将有助于防止同样的事情再次发生。
2.  **执行错误纠正(COE)。**这类似于事后分析，团队检查发生了什么、影响、促成因素、经验教训和纠正措施。
3.  **实施混沌工程。**这包括将压力和失败注入到应用程序中，以暴露盲点，观察系统行为，并作为一个迭代过程进行改进。像 [AWS 故障注入模拟器](https://aws.amazon.com/fis/)这样的工具使得以可控的方式破坏你的系统变得非常容易。它使用预定义的模板，例如，在 EC2 实例上运行 CPU 压力，甚至关闭该实例以查看您的系统如何响应。如果你想尝试一个动手项目，我有一个关于混沌工程的视频。

拥抱失败

拥抱失败是运行复杂 IT 系统不可避免的一个方面。转向持续的弹性听起来是一个自然的选择。通过预测潜在的故障，对我们的系统实施有效的监控，对事件做出适当的响应，并从我们的故障中吸取教训，我们都可以希望设计出在不可避免的情况发生时能够快速、自动恢复的系统。

## 如果您想了解更多关于这里提到的任何 AWS 工具的信息，请查看以下课程。

Embracing failure is an inevitable aspect of running complex IT systems. And moving toward continuous resilience sounds like a natural choice. By anticipating potential failures, implementing effective monitoring of our systems, responding appropriately to events, and learning from our failures, we can all hope to design systems that are capable of fast, automated recovery when the inevitable happens.

If you’d like to learn more about any of the AWS tools mentioned here, check out the following courses.