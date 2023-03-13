# AWS 更新 Secrets Manager，Step Functions |云专家

> 原文：<https://acloudguru.com/blog/engineering/aws-updates-sagemaker-secrets-manager-and-step-functions>

本周 AWS 怎么了？在本帖中，我们将为您带来最精彩的 AWS 新闻，包括:

*   pagemaker 获得了大量的更新
*   机密管理器现在支持旋转窗口
*   局部阶跃函数引入了模拟响应
*   亚马逊欺诈检测器现在包括预测解释
*   Amazon Lex 支持交替转录

想知道全部细节吗？请继续阅读了解更多信息！

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## SageMaker 更新综述

SageMaker 仍然是 AWS 的主要关注领域，本周发布了几个更新。

*   SageMaker Autopilot 有助于构建、训练和调整您的模型，它已经有了一些更新。Autopilot 现在支持 [Apache Parquet 文件](https://aws.amazon.com/about-aws/whats-new/2022/01/amazon-sagemaker-autopilot-apache-parquet/)，数据集的[最大大小从](https://aws.amazon.com/about-aws/whats-new/2022/01/amazon-sagemaker-autopilot-datasets-up-to-100-gb/)10GB 增加到 100GB。您还可以向 AWS 支持提出请求，通过 Autopilot 使用更大的数据集。

*   SageMaker Data Wrangler 有助于简化机器学习的数据处理，它还增加了对流行的 [JSON 和 ORC](https://aws.amazon.com/about-aws/whats-new/2022/02/json-orc-data-processing-jobs-amazon-sagemaker-data-wrangler/) 数据格式的支持，以及一些新的转换功能。

*   SageMaker JumpStart 将您连接到流行的机器学习模型集合，现在可以[将他们的端点部署到定制的 VPC 中，并使用定制的 KMS 设置加密他们的数据。对于拥有复杂架构的大型企业客户来说，这些是非常重要的考虑因素。](https://aws.amazon.com/about-aws/whats-new/2022/01/amazon-sagemaker-jumpstart-custom-vpc-kms-settings/)

## AWS Secrets Manager 增加了对旋转窗口的支持

AWS Secrets Manager 现在支持其管理的机密的[旋转窗口](https://aws.amazon.com/about-aws/whats-new/2022/02/aws-secrets-manager-windows/)。

轮换机密对于确保我们的应用程序保持安全至关重要。即使由 Secrets Manager 这样的服务来管理，仍然有妥协的机会。挑战在于，当我们轮换秘密时，并非所有事情都在同一时间发生。使用这些密码的应用程序可能会在短时间内不匹配，从而导致呼叫在轮换期间被拒绝。

轮换窗口允许我们设置特定的时间，以便在预期的维护窗口期间轮换我们的秘密。这意味着如果我们在短时间内确实有问题，我们可以确保它不会影响很多用户。

如果您的解决方案支持，在轮换策略中使用交替密码可以确保更高的可靠性。但是对于只使用一个秘密的解决方案，有一个旋转窗口可以帮助使你的解决方案更可靠。

## 模拟对 AWS 步骤函数的支持

在过去的几个月里，Step 函数得到了很多人的喜爱，现在我们有了最新的更新,发布了对 Step 函数本地模拟的服务集成响应。

去年，AWS 升级了 Step 函数，以支持 200 多种 AWS 服务和数千种 API 操作。在本地测试期间模拟来自这些服务集成的响应的能力意味着您可以在本地开发环境中更全面地测试您的 Step 函数。

模拟响应允许我们模拟与服务集成的交互。现在，这些只能让我们到此为止，而且还有一些限制(比如 Step 函数 Local 不验证模拟响应的格式)。但这确实解决了使用阶跃函数进行开发时存在的差距，总的来说，我希望阶跃函数随着时间的推移只会变得更加强大和流行。

## 亚马逊欺诈检测器预测解释

欺诈检测器收到了一个非常有趣的更新，增加了新的[预测解释](//aws.amazon.com/about-aws/whats-new/2022/01/aws-prediction-explanations-amazon-fraud-detector/)。

像许多[机器学习](https://acloudguru.com/blog/engineering/what-is-machine-learning-as-a-service-mlaas)产品一样，欺诈检测器为您提供了一个结果列表，显示潜在欺诈活动的风险。这很酷，但没有真正的方法来真正理解。。。为什么它被认定为欺诈。这相当于机器问某人一个问题，然后他们回答，“我就是知道。”

包含新的预测解释有助于提供影响预测的特定变量的详细信息。了解预测背后的潜在因素既有助于分析师评估索赔，也有助于架构师制定更主动的对策。这只是亚马逊继续投资于他们的托管机器学习服务的更多证据。

2021 年 6 月 30 日之后生成的车型已经可以使用该功能。如果您的模型是在此之前生成的，您将需要重新训练您的模型以访问此功能。如果你有兴趣探索亚马逊欺诈探测器，请查看 AWS re:Invent 2020 的演示。

## 亚马逊 Lex 多个副本

亚马逊 Lex 发布了一个新功能,它允许对用户的语音输入进行多种转录和信心评分。

我们都有过令人不快的语音界面体验，你说一件事，系统却把它解释成另一件事。

对于构建这些系统的人和使用它们的人来说，这几乎同样令人沮丧。Amazon Lex 的这一新功能的美妙之处在于，它将提供如何转录它的多种建议，以及信心评分。

有了信心评分和替代解释，你可以让你的对话界面更加健壮——或者在不确定的时候要求澄清，或者选择一个更有可能的替代解释。

任何时候你在使用语音界面的时候，花时间改进它以获得更流畅的用户体验总是值得的。如果您使用 Lex 进行语音输入，这可能是一个值得探索的改进。

## 跟上 AWS 的所有事情

想要跟上 AWS 的所有事情？在推特[上关注 ACG](https://twitter.com/acloudguru)和[脸书](https://www.facebook.com/acloudguru)，[在 YouTube 上订阅云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每周 AWS 更新，并在 [Discord](http://discord.gg/acloudguru) 上加入对话。

现在，往前走，学习所有的东西。(为此，请查看我们的[免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)——不需要信用卡！)而且一如既往，继续牛逼，云大师们！