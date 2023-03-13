# 如何通过 AWS 认证 DevOps 工程师-专业考试

> 原文：<https://acloudguru.com/blog/engineering/how-to-pass-the-aws-certified-devops-engineer-professional-exam>

如果你正在考虑参加 AWS 认证 DevOps 工程师-专业认证考试，我在这里帮助你粉碎它！以下是我对如何准备考试的一些建议，以及考试中不同的领域所涵盖的内容。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## 如何通过 AWS 认证考试？

在我们谈论 [DevOps Pro 考试](https://aws.amazon.com/certification/certified-devops-engineer-professional/)之前，这里是我关于参加和通过 AWS 认证考试(或任何认证考试，就此而言)的顶级提示。

1.  快速浏览问题，做好复习标记
    考试开始时总是有些紧张。所以我试着快速行动。我会浏览一个问题的内容，如果我感到有点不确定，我会很快标记它以便复习，然后继续下一个问题。

    当你在考试中前进时，一个问题或答案常常会唤起你对你标记为复习的东西的记忆。我几乎总是发现，我标记为复习的问题在第二次阅读时更容易回答。

2.  **不要先看答案**
    先看那些选择题答案很诱人，但是不要！当我阅读一个问题时，在查看答案之前，我会思考哪些 AWS 服务可能是相关的*。当我看到这些选择时，就很难让我改变主意了。这是筛选和剔除不正确答案的好方法。* 
3.  确定关键词和术语
    我最有效的省时技巧就是使用关键词和术语。场景中提到“实时”了吗？这通常与亚马逊 Kinesis 有关。当你看到那个关键词时，跳到答案并搜索 Kinesis。这样可以快速排除错误答案。

    您是否需要保护 S3 的数据(如个人身份信息)？这让亚马逊玛西尖叫。快速扫描给 Macie 的答案，剔除不提 Macie 的烂苹果。长期储存？意思是冰川。建立用于开发运维的服务列表，研究该服务的服务页面和常见问题，找到关键词和术语，并创建您自己的参考列表。

    本着节省时间的精神，就[参加我的 DevOps Pro 培训课程](https://learn.acloud.guru/course/aws-certified-devops-engineer-pro/overview)！我确保在整个课程中识别关键词和术语。

总的来说，我考试时的主要策略是动作要快。记住，每个问题你只有两分钟多一点的时间。在你知道的问题上节省时间。不要在困难的问题上磨磨蹭蹭。做好复习标记，继续前进！

## AWS 认证 DevOps 工程师-专业考试涵盖哪些内容？

AWS DevOps 认证难吗？如果你了解你的东西就不会。让我们把事情按领域分解，并强调一些粉碎考试的顶级技巧。

### **领域 1: SDLC 自动化**

这个领域主要关注关键的 AWS 开发工具——[AWS 代码提交](https://aws.amazon.com/codecommit/)、 [AWS 代码构建](https://aws.amazon.com/codebuild/)、 [AWS 代码部署](https://docs.aws.amazon.com/codedeploy)和 [AWS 代码管道](https://aws.amazon.com/codepipeline/)。我最喜欢的掌握这个领域的技巧是不要走，而是*运行*到 [AWS 管理控制台](https://aws.amazon.com/console/)，转到 CodePipeline，并开始构建！

这是关键——研究落差！从源阶段开始，展开下拉列表。可以用什么回购？都在下拉列表中。接下来是构建阶段。有哪些选择？点击下拉菜单。哦，对了，CodeBuild 或 Jenkins！等等，它说构建阶段是可选的。然后是部署阶段(也是可选的)。

对于我们可以部署的内容，有许多选项。研究下拉菜单并记住它。使用不同的选项(CloudFormation、CodeDeploy、Elastic Beanstalk 等)进行一些部署。)，而且有戏。

### **域 2:配置管理和基础设施代码**

该领域重点关注 [AWS CloudFormation](https://aws.amazon.com/cloudformation/) 、 [AWS OpsWorks](https://aws.amazon.com/opsworks/) 和 [AWS Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk/) 。理解这些服务做什么，它们的用例，以及何时使用其中一个而不是另外两个是很重要的。

对于这个领域，理解部署方法也很重要，比如蓝/绿部署。对于 CloudFormation，了解助手脚本及其用例。

### **域 3:监控和记录**

这个领域由[亚马逊 CloudWatch](https://aws.amazon.com/cloudwatch/) 和[亚马逊 Kinesis](https://aws.amazon.com/kinesis/) 主导。了解 Kinesis 的四种风格及其各自的用例。记住“实时”这个关键术语！

[EventBridge 是 CloudWatch 事件服务](https://aws.amazon.com/blogs/compute/upgrading-to-amazon-eventbridge-from-amazon-cloudwatch-events/)的演进。但重点还是在事件上。CloudWatch 还没有被弃用， [CloudWatch 警报](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html)还在。所以要做好准备，因为你可能会在考试中同时看到 EventBridge 和 CloudWatch。请将它们视为可互换的。

### **领域 4:政策和标准自动化**

该领域涵盖了执行特定但相对简单的任务的服务。例子有 [AWS 配置](https://aws.amazon.com/config/)、[亚马逊检查员](https://aws.amazon.com/inspector/)、[亚马逊守卫](https://aws.amazon.com/guardduty/)和[亚马逊 Macie](https://aws.amazon.com/macie/) 。了解他们的使用案例！这些可能是考试中容易的分数。并添加一些关键词和术语，如:个人身份信息(PII) = Macie。

如果您看到关键字“audit”或“auditing ”,请开始考虑 AWS 配置。请记住，可信顾问可以提供建议，但是对这些建议做些什么取决于您(您可以从可信顾问自动化中构建自动化)。

AWS 系统管理器类似于 Kinesis，因为它有几种不同的产品。了解每种产品，以及它能为您做什么。

### **领域 5:事故和事件响应**

值得理解的是，域 4 和域 5 之间有一些交叉服务，如 Systems Manager 和 Kinesis。这个领域的一个关键主题是从自动化我们对事故和事件的响应的角度来思考。因此，考虑在自动化中充当连接器和触发器的服务，如[亚马逊 SNS](https://aws.amazon.com/sns) 、 [AWS Lambda](https://aws.amazon.com/lambda/) 、 [CloudWatch Alarms](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html) 和[亚马逊 EventBridge 事件](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-events.html)。

不要忘记混合环境！我们如何从本地服务器获取服务器日志？安装云观察日志代理。我们如何管理本地服务器？安装 SSM 代理。这些是需要学习和理解的事情。

### **领域 6:高可用性、容错和灾难恢复**

这个域名告诉了我们太多东西——我们想要分散我们的资源。我们如何做到这一点？想想多 AZ 服务和技术(自动伸缩、负载平衡)，不要忘记多区域服务(比如 [Amazon DynamoDB 全局表](https://aws.amazon.com/dynamodb/global-tables/))。

谈到灾难恢复，请描绘一个时间表。根据恢复时间目标(RTO ),在时间线上向前推进。我们还能消沉多久？有了恢复点目标(RPO ),在时间线上向后移动。我们能承受多少数据丢失？了解这些问题的解决方案，你就可以开始了。

## **想了解更多关于成为 DevOps 工程师的信息吗？**

这是一个关于如何应对 DevOps 工程师专业考试的快速分析！但是我的最高小费？查看我的新 [AWS 认证 DevOps 工程师-专业](https://learn.acloud.guru/course/aws-certified-devops-engineer-pro/overview)培训课程，包括动手实验和创新图形，以增强视觉学习！

如果你还在寻找更多关于在 DevOps 工作的好处的信息，看看这些好帖子: