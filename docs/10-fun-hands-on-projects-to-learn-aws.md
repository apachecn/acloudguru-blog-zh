# 学习 AWS 的 10 个有趣的动手项目

> 原文：<https://acloudguru.com/blog/engineering/10-fun-hands-on-projects-to-learn-aws>

学习 AWS 最好的方法就是使用提供的服务来构建真实世界的应用程序。我是“边做边学”的强烈支持者，所以我整理了 10 个不同难度的有趣项目，它们将帮助[启动你的云计算生涯](https://acloudguru.com/blog/engineering/jump-start-your-cloud-career)。

对于每个项目，我都列出了先决条件、使用的服务，并提供了一个在线教程的链接。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## 1.在亚马逊 S3 上推出一个静态网站

在亚马逊 S3 上部署你的静态网站是一个划算的解决方案，通常比传统的托管服务提供商更便宜。几年前我把我的网站迁移到了亚马逊 S3，从那以后我一直在省钱！这是一个超级有趣的项目 AWS 新手，并向您介绍几个核心服务，如亚马逊 S3 和亚马逊 CloudFront。

您将创建一个 Amazon S3 存储桶来保存您的静态网站文件，并创建一个 Amazon CloudFront 分发包来为您的网站提供全球服务。亚马逊 Route 53 会管理你的域名，AWS 证书管理器会提供有效的 SSL/TLS 证书。

**使用的服务**

*   亚马逊 S3
*   亚马逊云锋
*   亚马逊 53 号公路
*   AWS 证书管理器 r

**先决条件**

你需要一些东西来开始这个项目:

*   由 HTML、CSS、JavaScript 等组成的静态网站。文件。

要开始，查看这个[在线教程](https://docs.aws.amazon.com/AmazonS3/latest/userguide/website-hosting-custom-domain-walkthrough.html)。

## 2.使用 CloudFormation 启动 Amazon EC2 Web 服务器

CloudFormation 是我最喜欢的服务之一。当您有多个资源要部署时，您会很快意识到这个过程是多么的乏味和耗时，尤其是当您有多个环境时(例如，开发、测试和生产)。

CloudFormation 允许您使用[基础设施即代码(IaC)](https://acloudguru.com/blog/tag/infrastructure-as-code) 大规模、更加一致和高效地部署资源。这个有趣的项目允许您使用 JSON 或 YAML 编写一个 CloudFormation 模板，在 Amazon EC2 实例上建立一个 web 服务器。

**使用的服务**

*   亚马逊云形成
*   亚马逊 EC2
*   亚马逊 VPC(和子组件)

**先决条件**

你需要一些东西来开始这个项目:

要开始，查看这个[在线教程](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/working-with-templates-cfn-designer-walkthrough-createbasicwebserver.html)。

## 3.将 CI/CD 管道添加到 Amazon S3 存储桶

[持续集成和持续交付(CI/CD)](https://acloudguru.com/course/implementing-a-full-ci-cd-pipeline) 自动化软件交付管道中的步骤。

如果没有自动构建和部署，我们将如何生活？我记得由于需要手工劳动和稳定性风险，一个季度只能部署一次代码的日子！这个项目是一个在 AWS 上引入 [CI/CD 的有趣项目。当代码签入时，您将自动将网站更改部署到生产环境中。另外，你可以使用你在亚马逊 S3 项目的**发布一个静态网站中创建的 S3 桶作为一个起点。**](https://acloudguru.com/blog/engineering/automating-ci-cd-with-aws-codepipeline)

**使用的服务**

*   亚马逊 S3
*   AWS 代码管道
*   AWS CodeStar

**先决条件**

你需要一些东西来开始这个项目:

*   静态网站
*   静态网站代码已签入 GitHub

要开始，查看这个[在线教程](https://docs.aws.amazon.com/prescriptive-guidance/latest/patterns/automate-static-website-deployment-to-amazon-s3.html)。

## 4.使用 AWS Lambda 将 Amazon CloudWatch 指标发布到 CSV 文件

CloudWatch 与大多数服务相集成，使用指标来发布有关系统性能的详细信息。指标是发送到 Cloudwatch 的时间序列数据。

我喜欢这个项目，因为它使用了另一个我最喜欢的服务， [AWS Lambda](https://acloudguru.com/hands-on-labs/creating-a-simple-aws-lambda-function) 。由于我们使用 Lambda，这个项目确实需要一点编码经验，所以它不适合绝对的初学者。只要你熟悉 Lambda 支持的一种编程语言，你就会很乐意亲自动手。

**使用的服务**

*   亚马逊云观察
*   自动气象站λ
*   AWS CLI

**先决条件**

你需要一些东西来开始这个项目:

*   安装在本地计算机上的 AWS CLI
*   文字编辑器

要开始，查看这个[在线教程](https://docs.aws.amazon.com/prescriptive-guidance/latest/patterns/publish-amazon-cloudwatch-metrics-to-a-csv-file.html)。

* * *

[**看点:解决“没有经验”的云招聘问题**](https://get.acloudguru.com/solving-no-experience-cloud-problem-webinar)
没有工作是得不到经验的。但是谁会雇佣没有经验的你呢？谜题！[观看这一免费的点播网络研讨会](https://get.acloudguru.com/solving-no-experience-cloud-problem-webinar)，进行关于云计算职业发展的小组讨论，并获得您的第一份云计算工作。

* * *

## 5.使用亚马逊 SageMaker 训练和部署机器学习模型

如果你对机器学习很好奇，但不知道从哪里开始，试试[亚马逊 SageMaker](https://acloudguru.com/blog/engineering/how-to-build-a-netflix-style-recommendation-engine-with-amazon-sagemaker) 。SageMaker 提供“机器学习即服务(MLaaS)”，并在您的机器学习之旅中与您见面。SageMaker 甚至为非编码人员提供“无编码”计算机视觉选项。对于这个有趣的动手项目，您将训练一个机器学习模型来预测消费者行为。这个项目使用的是 [Python](https://acloudguru.com/course/introduction-to-python-development) 编程语言，所以熟悉计算机编程会有帮助。

**使用的服务**

**先决条件**

你需要一些东西来开始这个项目:

*   用于训练的数据集
*   熟悉 Python

要开始，查看这个[在线教程](https://aws.amazon.com/getting-started/hands-on/build-train-deploy-machine-learning-model-sagemaker/)。

## 6.使用 Amazon Translate 和 Amazon Lex 创建一个翻译语言的聊天机器人

我爱 AWS 提供的高级 [AI 服务。这些服务使用预先训练的机器学习模型，允许您轻松地将智能集成到现有的应用程序中。](https://acloudguru.com/blog/engineering/what-is-machine-learning-as-a-service-mlaas)

如果你从未玩过 Amazon Translate 或 Amazon Lex，那你就要享受特殊待遇了。在这个动手项目中，您将构建一个执行语言翻译的对话界面。如果这个项目听起来不酷，我不知道哪个项目会酷！您还将接触到其他服务，如 AWS Lambda、AWS CloudFormation、Amazon CloudFront 等等。

**使用的服务**

*   亚马逊 Lex
*   亚马逊翻译
*   AWS Lamda
*   自动气象站云形成
*   亚马逊云锋
*   亚马逊的姐夫

**先决条件**

你需要一些东西来开始这个项目:

*   用于训练的数据集
*   熟悉 Python

要开始，查看这个[在线教程](https://aws.amazon.com/blogs/machine-learning/create-a-translator-chatbot-using-amazon-translate-and-amazon-lex/)。

## 7.使用 AWS Amplify 部署一个简单 React Web 应用程序

AWS Amplify 帮助你在 AWS 上构建全栈 web 应用，是我新宠的服务！

借助 Amplify，我能够在不到两周的时间内使用 Amazon Cognito 部署 React 应用程序进行用户身份验证，使用 AWS AppSync 部署 GraphQL 用于 API 层，使用 Amazon Aurora 部署数据库，使用 AmazonS3/Amazon CloudFront 部署存储和内容交付！你可以在这里查看那个项目[，在这里](https://youtu.be/Xi6tDqctLsY)查看[。](https://www.salaryoverflow.com/)

在这个动手项目中，您将使用 [DynamoDB](https://acloudguru.com/course/amazon-dynamodb-deep-dive) ，而不是 Aurora，并在 50 分钟内部署应用程序！

**使用的服务**

*   AWS 放大器
*   亚马逊认知
*   亚马逊 DynamoDB
*   AWS AppSync
*   亚马逊 S3
*   亚马逊云锋

**先决条件**

你需要一些东西来开始这个项目:

*   节点. js
*   GitHub / Git
*   文字编辑器

要开始，查看这个[在线教程](https://aws.amazon.com/getting-started/hands-on/build-react-app-amplify-graphql/)。

## 8.创建一个 Alexa 技能，使用 AWS Lambda 和 DynamoDB 提供学习技巧

当我刚开始学习 AWS 时，Alexa 技能是我开发的第一批应用程序之一。如果你不知道，大多数 Alexa 技能运行在 AWS 生态系统上。我发现 Alexa 技能开发是对云和人工智能的温和介绍。

在这个有趣的实践教程中，你将建立一个由 AWS Lambda 函数和 DynamoDB 表支持的 Alexa 技能，以提供有用的学习技巧。

**使用的服务**

*   Alexa 技能工具包(询问)
*   自动气象站λ
*   亚马逊 DynamoDB

**先决条件**

你需要一些东西来开始这个项目。

*   亚马逊开发者门户网站上的一个账户
*   一个 DynamoDB 表，里面有你最喜欢的学习技巧
*   回声设备是一个不错的选择，但不是必需的

要开始，请查看此[在线文档](https://developer.amazon.com/en-US/docs/alexa/custom-skills/steps-to-build-a-custom-skill.html)。

## 9.使用亚马逊 Rekognition、AWS Lambda 和亚马逊 S3 识别名人

我一直很喜欢玩 Amazon Rekognition。当他们发布名人识别功能时，我迫不及待地想尝试一下。您知道名人可以联系 AWS 支持来选择退出吗？我想知道我如何能选择加入？😂

在这个有趣的动手项目中，当图像上传到亚马逊 S3 桶时，您将触发 Lambda 函数。你的 Lambda 函数然后将调用[recognize 名人 API](https://docs.aws.amazon.com/rekognition/latest/dg/API_RecognizeCelebrities.html) 来识别照片中的人！

**使用的服务**

*   亚马逊 S3
*   自动气象站λ
*   亚马逊索赔案

**先决条件**

你需要一些东西来开始这个项目:

要开始，请查看此[在线文档](https://docs.aws.amazon.com/rekognition/latest/dg/celebrities-procedure-image.html)。

## 10.在 Amazon EC2 上托管一个专用的 Jenkins 服务器

谁不喜欢“进入”EC2 实例并到处玩呢？我实际上已经在 EC2 实例上安装了 Jenkins，并将其连接到 Alexa 技能，通过语音部署我的代码。你可以在这里查看那个项目[，在这里](https://www.jenkins.io/blog/2019/02/26/jenkins-alexa-voice-controlled-cicd/)查看[。](https://developer.amazon.com/blogs/alexa/post/465a7f49-a938-45ad-a6db-58933317c4e3/hear-it-from-a-skill-builder-alexa-jenkins-say-hello-to-voice-controlled-ci-cd)

在这个动手项目中，您将启动一个 EC2 实例，并在其上配置 [Jenkins](https://acloudguru.com/course/learn-jenkins-by-doing) 。这个项目会让你接触到 EC2 和安全。

**使用的服务**

*   亚马逊 EC2
*   亚马逊 VPC(和子组件)

**先决条件**

你需要一些东西来开始这个项目。

*   EC2 密钥对
*   SSH 客户端或 PuTTY

要开始，查看这个[在线教程](https://www.jenkins.io/doc/tutorials/tutorial-for-installing-jenkins-on-AWS/)。

* * *

[![](img/aa563ce93b787834c7c648eaec24feaa.png)](https://get.acloudguru.com/securing-aws-environment-webinar)

**[保护您的 AWS 环境](https://get.acloudguru.com/securing-aws-environment-webinar)** 在[这个免费的点播网络研讨会](https://get.acloudguru.com/securing-aws-environment-webinar)中，了解如何从零开始保护复杂的 AWS 环境，并学习如何正确[审计和保护 AWS 帐户](https://acloudguru.com/blog/engineering/how-to-audit-and-secure-an-aws-account)。

* * *

## 后续步骤

如果你在完成这些项目时有任何问题，请前往 [ACG 不和谐频道](https://discord.com/invite/acloudguru)找我。

在开始之前，我建议您使用 AWS 免费层计划。免费层计划将减少您在 AWS 上构建时可能产生的任何费用。此外，一旦你完成一个项目，不要忘记清理你不再使用的任何资源，这样你就不会产生费用。

完成这些项目后，你会有一个很好的作品集来展示你的才华。

另一种与他人分享你的才能的方法是写一篇关于你所学到的经验的博客。我相信其他人会很想知道你的旅程，包括我自己。此外，考虑申请加入 [AWS 社区建设者](https://aws.amazon.com/developer/community/community-builders/)计划。AWS 社区建设者为 AWS 爱好者提供技术资源、指导和交流机会。

你需要额外的有趣的项目想法吗？查看 [#CloudGuruChallenge:选择你的挑战大组合](https://acloudguru.com/blog/engineering/cloudguruchallenge-the-choose-your-challenge-mega-mix)。那么，你还在等什么？我们来建吧！