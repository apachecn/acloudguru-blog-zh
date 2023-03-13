# 回复:发明 2021: AWS 英雄们押注于我们将会看到什么

> 原文：<https://acloudguru.com/blog/engineering/reinvent-2021-aws-heroes-place-bets-on-what-well-see>

### *一个月球 AWS 区域？53 号公路数据库？在大型演出之前，我们称之为长镜头和确定的事情*

AWS re:Invent 2021 快到了。在《re:Invent 2020 完全虚拟化之后，re:Invent 又回到了拉斯维加斯。本着这种拉斯维加斯精神，我们召集了一个 AWS 英雄小组进行圆桌讨论，打赌我们在 re:Invent 2021 上可能会看到什么(以及我们几乎肯定会*不会*看到什么)。

如果你要亲自或通过虚拟方式参加 re:Invent，请务必阅读我们的[re:Invent 2021](https://acloudguru.com/blog/business/the-ultimate-guide-to-aws-reinvent-2021)终极指南。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

想旁听完整的讨论吗？拉一把椅子，观看免费点播的网络研讨会 [re:Invent 2021:大展前要知道的事情](https://acloudguru.com/content/reinvent-2021-aws-heroes-on-what-to-know-before-the-show-webinar)。

为了简洁、清晰和总体美观，下面的引语已经过编辑。你可以打赌，任何错误都可能是编辑方面的。

## 计算和容器

云专家和 AWS 社区英雄的创始人 Ryan Kroonenburg 分享了他对 re:Invent 2021 的计算和容器的预期。

### **稳操胜券:EC2 实例的扩展和对裸机的支持，EKS 无处不在**

“本月，AWS [宣布](https://aws.amazon.com/blogs/aws/new-ec2-instances-g5-with-nvidia-a10g-tensor-core-gpus/)将 G4 升级到 G5。这些基本上是由 Nvidia 传感器核心 GPU 支持的实例，可为图形密集型和机器学习工作负载提供约 3 倍的性能。但我相信我们会看到其他一些升级，”瑞安说。

“另一个确定的赌注是，如果你[阅读 EKS Anywhere 的文档](https://acloudguru.com/blog/engineering/the-career-changing-art-of-reading-the-docs)，他们说他们将在 2022 年为 EKS Anywhere 提供裸机支持。因此，看到 re:Invent 也宣布了这一点，我不会感到惊讶，”Ryan 说。

随着人们越来越多地迁移到无服务器架构，容器几乎是一种不可避免的罪恶，EKS 和 ECS Anywhere 就是一个很好的例子，让人们在他们所在的地方见面。

我们预计在 re:Invent 2021 上不会出现容器短缺的公告。它们是什么？我们走着瞧。(但手指交叉在地图上，以找出在哪里运行它们。)

### **扯平:升级 EFS 存储**

“在去年的 re:Invent 上，他们升级了 gp3 和 I/o。9 月，AWS 宣布为 EFS 提供智能分层，这与他们为 S3 提供智能分层的方式非常相似，”Ryan 说。"但是他们最近没有为 EFS 做任何性能升级."

### **Longshot:新的月球自动气象站区域**

当然，这不会发生，但它会很酷。如果他们需要任何帮助，Ryan 自愿帮助建立一个月球数据中心。

“我估计到 2030 年月球上会有某种云，”瑞安预测道。

你先在这里听到的。(有人设置了一个提醒，9 年后再来查看这个。)

## 数据库

DVLA 和 AWS Data Hero 的首席架构师 Matt Lewis 对今年 re:Invent 的数据库新闻下了赌注。

### **确信无疑:数据库引擎之间更直接的集成**

“这是我们在过去几年里看到的事情之一，”马特说。

在过去，有很多地方需要编写自定义 Lambda 函数来充当粘合剂。现在已经有所改善，但还有更多的要做。

Matt 说:“我认为减少一些作为开发者必须做的重复步骤是肯定的赌注之一，我们将开始看到更多的公告。”。

### **Even money:带数据 API 的无服务器 Aurora v2**

没有 RDS 代理的奥罗拉所有的美好！

### **long shot:53 号公路数据库**

“我不知道这是否是开玩笑，但你不断听到更多人谈论 53 号公路是一个潜在的数据库。AWS 的服务承诺是 100%左右，你可以在多个字符串中存储多达 4000 个字符的 TXT 记录，”Matt 说。“所以你知道，也许 AWS 会认识到这一点，你也可以在 AWS 控制台的数据库类别中找到 53 号公路。”

会发生吗？为了创建 53 号公路数据库，可能需要 AWS 月球区域。

## 机器学习

这些天来，SageMaker 的事情越来越多。去年我们进行了大量的更新，引入了定制芯片，我们看到[机器学习](https://acloudguru.com/blog/engineering/what-is-machine-learning-as-a-service-mlaas)正在其他服务中实现。

我们的机器学习大师凯莎·威廉姆斯是一位云专家和 AWS 机器学习英雄的首席培训架构师，他提供了以下重新发明的预测——并声明:“老实说，所有这些都是长期预测，所以不要在我身上下注！”

### **确信无疑:亚马逊 CodeGuru 将支持更多语言**

“亚马逊代码大师目前只支持 Java 和 Python，”凯莎说。“我想 AWS 将通过增加新的语言来继续扩展这一领域。”

### **Even money:Amazon Connect 增加了新的机器学习功能**

“去年，AWS 推出了识别来电者的语音 ID、用于更多情感分析的隐形眼镜和智慧。他们刚刚推出了预测拨号功能。凯莎说:“在 2021 年的 re:Invent 大会上，我认为将会有很多关注亚马逊连接和添加更多酷的机器学习功能。“但我们会看到！”

### **Longshot: AWS DeepDrone，一款与亚马逊 SageMaker 集成的自主无人机**

我们是不是已经走投无路了，还是说无人驾驶飞机会超级酷？

“这是我所谓的‘深度玩具’，比如 DeepLens、DeepComposer 和 DeepRacer，”凯莎说。“我想要一架 DeepDrone，一架可以装载我的 SageMaker 模型的自主无人机。听起来会很有趣。”

“这听起来也很危险，”瑞安开玩笑说。“如果我在上面加载我的机器学习模型，那将是极其危险的。”

* * *

[![2021 re:Invent Pre-Show](img/6994ee477a5fa539a7bf90638d62f67e.png)](https://acloudguru.com/content/reinvent-2021-aws-heroes-on-what-to-know-before-the-show-webinar)

*观看 [re:Invent 2021: AWS Heroes 关于展会前应该知道的事情](https://acloudguru.com/content/reinvent-2021-aws-heroes-on-what-to-know-before-the-show-webinar)——关于我们期待什么和我们最期待的主题演讲的大赌注。*

* * *

## 安全性

旁注:其他云提供商最近的安全相关问题会受到多少关注？2021 年提醒我们，安全是我们理所当然的事情(好像我们需要另一个提醒)。

谈到对 AWS 安全相关公告的预测，我们求助于独一无二的 Mark Nunnikhoven，Lacework 杰出的云策略师和 AWS 社区英雄。这是他放加元的地方。

“我对我的赌注感到厌烦，因为今年是安全大扫除年，”马克说。“这就像‘dot’发布一样，你会说，‘在我们真正推进之前，我们必须清理一堆这种东西。’"

### **确信无疑:AWS 安全中心变得更易于使用**

Mark 确信，我们将看到 AWS Security Hub 更新的“一些东西”，包括其 UI 和部署模型的增强，使其更易于使用。

“现在，当您尝试部署它时，它是针对每个地区、每个客户的。是的，你可以自动化其中的一些，但是弄清楚一些数据建模会变得很棘手。因此，让它一键穿越整个组织将是美妙的。但更重要的是，在现在的用户界面中，这是非常基本的。它提供了所有这些发现，这很好:这是一个集中查看所有安全信息的地方。但事情到此为止了。它不会帮助您理解安全信息。比如“嘿，你应该做点什么！”或者，“这两件事是有联系的！"

这可能是扩展机器学习模型的好地方。我们在 GuardDuty 中看到了这一点，但将它放入 AWS 安全中心以在更高的级别上运行会很好。

“这里需要某种形式的帮助，”马克补充道。“什么都行！在这里，任何事情都是有益的！”

### **甚至钱:亚马逊检查员得到了一个亚马逊 Macie 的完全重新启动**

检查员在那里做它的工作，但是它已经被遗忘很久了，需要现代化。马克押注于全面重启，尽管实际上这可能更倾向于长远考虑。

### **long shot:AWS IAM 的新功能使跨账户访问及其风险更易于管理**

“这肯定比月球区域的可能性小，”马克说。“这是我在与团队交流时遇到的最大痛处之一:我很细致，有很多能力。但最大的弱点之一是当你试图跨帐户授予权限和跨帐户使用规则。。。我的远景是，他们将解决这个问题，并使了解这些事情变得更容易:我是否给了这个帐户访问它的权限，它何时发生，以及基于此我的暴露程度是多少？所有的部分都在那里，但他们需要把它们放在一起。”

## 无服务器

无服务器是一种将这些砖块组合在一起的砂浆，尤其是当您将功能视为服务时。当你试图使用现代设计和无服务器架构来构建一个架构良好的框架时，会有很多摩擦。还有很多清理工作需要完成，以消除开发人员体验中的摩擦，并使事情以可扩展和可靠的方式工作。

iRobot 和 AWS 无服务器 Hero 的云机器人研究科学家 Ben Kehoe 对 2022 年的 AWS 做出了以下无服务器预测。

### **确信无疑:在传统计算和无服务器计算之间架起了更多桥梁**

“我认为可以非常肯定地说，我们将会看到一些服务为更少的无服务器计算和数据库等带来更多的无服务器优势。供品。我们还将看到无服务器服务增加功能，使习惯于传统架构的人更容易使用它，”Ben 说。“今天，Lambda 可以成为许多事情的事件源。你不能把这些服务和 FarGate 上运行的东西挂钩。我认为这种差距会继续缩小。”

### **甚至钱:更多地方有第三方集成(目前:EventBridge 和 CloudFormation)**

“我们已经看到 AWS 有兴趣在生态系统的某些部分与第三方更紧密地集成，正如我们在 EventBridge 和 CloudFormation 中看到的那样，”Ben 说。“我认为我们将会看到更多的集成和服务，这些集成和服务旨在消除客户的工作，并使其在 AWS 中更加本地化。”

### **Longshot: AWS 宣布现在将接受“Lambdas”作为有效术语**

“就像乐高坚持说它们不是‘乐高’而是‘乐高积木’一样，AWS 坚持说它们是 Lambda 函数’而不是‘Lambdas’"

我们能从 AWS 官方获得只说“Lambdas”而不是“Lambda functions”的许可吗？可能不会，但会很酷。(不要告诉克里斯·芒恩斯。)

## 跟上 re:发明 2021

关注 AWS 的所有事情:在 Twitter[和](https://twitter.com/acloudguru)[脸书](https://www.facebook.com/acloudguru)、[上关注一位云专家，在 YouTube 上订阅一位云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每日更新，并在 [Discord](http://discord.gg/acloudguru) 上加入对话。如果你想提升 AWS 技能，请查看我们目前的免费课程[！](https://acloudguru.com/blog/news/whats-free-at-acg)