# re:Invent 2021: AWS 全力投入机器学习

> 原文：<https://acloudguru.com/blog/engineering/reinvent-2021-aws-goes-all-in-on-machine-learning>

你好，云大师们！我是 Scott Pletcher，在 [AWS re:Invent 2021](https://acloudguru.com/blog/tag/reinvent2021) 从拉斯韦加斯为您报道，在这里，我与 AWS 高级开发人员倡导者[班卓·奥巴约米](https://twitter.com/banjtheman)在一起。在这篇文章中，我们将讨论来自 re:Invent 周三的重大新闻，以及所有机器学习新闻的综述。

请继续阅读所有适合发布的 ML 和数据新闻！

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

为了简洁、清晰和令人惊叹，我们对这段对话进行了编辑。任何错误大概都是(OK。。。肯定地)在编辑的部分上。

## DynamoDB 非频繁访问表

**Scott** : 周三的主题是数据、机器学习和人工智能。

我认为非常有趣的一个公告是 [DynamoDB 非频繁访问表](https://aws.amazon.com/blogs/aws/new-dynamodb-table-class-save-up-to-60-in-your-dynamodb-costs/)。这类似于不经常访问的 S3 或 EFS。你用得越少，你付的钱就越少。他们在主题演讲中举了一个很好的例子，一个社交媒体应用程序如何利用五年前的照片。您不会每天都访问它，但是当您访问它时，您会希望它很快出现。因此，我很高兴看到客户可以利用这一新的数据库层做些什么。

## pagemaker 地面真相加

接下来，一个令我好奇的消息是 [SageMaker 地面真相加](https://aws.amazon.com/blogs/aws/announcing-amazon-sagemaker-ground-truth-plus/)。

**班卓琴:**更好！

斯科特:是的，我想是的。是啊，加上一个"加号"就行了。

因此，SageMaker Ground Truth 是一项服务，客户可以使用它来帮助清理和分类数据，然后再将其用于机器学习目的，这非常重要。

“另外”,我想意味着一些，一些数据可能需要特殊技能来量化和分类，这些数据现在将被发送给具有这些特殊技能的人。是这样吗？

是的，你需要像主题专家、中小企业那样，真正深入挖掘这些数据分类问题，这可能是一个正常人无法分类的。因此，让这些专家帮助进行分类是非常好的。

## pagemaker 无服务器推理

斯科特:太棒了。另外一件有趣的事情， [SageMaker 无服务器推论](https://aws.amazon.com/about-aws/whats-new/2021/12/amazon-sagemaker-serverless-inference/)。现在，通常当您部署推理基础设施时，您必须将其部署在本质上是 EC2 的基础设施上，对吗？这有望让我们不用做任何事情就能部署它。

是的，我喜欢无服务器的东西，因为你不用担心服务器。因此，有兴趣看看我们如何实际使用推理，而不必担心构建 EC2 实例。

斯科特:是的。我的一个问题是，什么是预热时间，嗯，调用这些推论。那会。

班卓琴(Banjo):是的，一旦你接触并弹奏它，那将会很有趣。

## 亚马逊 Kendra 体验构建器

**斯科特**:确实。接下来:[亚马逊 Kendra 体验构建器](https://aws.amazon.com/about-aws/whats-new/2021/12/amazon-kendra-experience-builder-search-analytics-dashboard-custom-document-enrichment/)。当然，Amazon Kendra 是一个搜索引擎，它被设计用于企业组织来帮助查找文档。

是的，所以有了 Experience Builder，你可以获得端到端的低代码、无代码的工作流，你可以用它来构建你自己的真正的私人搜索、数据库、仪表板，而不必使用定制代码。因此，我们非常期待看到客户将通过这种新体验来构建什么。

## 亚马逊 Lex 自动聊天机器人设计器

斯科特:这是个大问题。我们能让聊天机器人不那么令人失望吗？这对我来说是个大问题。很明显，亚马逊正在尝试，因为他们已经宣布[亚马逊 Lex 聊天机器人设计师](https://aws.amazon.com/about-aws/whats-new/2021/12/amazon-lex-automated-chatbox-designer/)。这里的想法是，它有助于建立聊天机器人，并使它们更好。

聊天机器人，通过聊天机器人总是一条艰难的学习曲线。希望通过这种简化的体验，您可以获得一些意图，并了解是什么调用了这些不同的意图，从而使构建聊天机器人体验变得更加容易，而不是必须自己遍历所有代码。

## pagemaker 工作室实验室

**Banjo:** 我对 [SageMaker Studio Lab](https://aws.amazon.com/blogs/aws/now-in-preview-amazon-sagemaker-studio-lab-a-free-service-to-learn-and-experiment-with-ml/) 感到非常兴奋，因为你可以在没有账户的情况下旋转 [Jupyter 笔记本](https://acloudguru.com/course/introduction-to-jupyter-notebooks)——只需要一个电子邮件地址，你就可以准备好部署 SageMaker，你可以到处玩，测试机器学习工作负载。当你准备好了，你可以把它移植到 SageMaker Studio。因此，我真的很兴奋，这将有助于搭载更多的客户，让他们可以体验机器学习和制作很酷的东西。

斯科特:现在机器学习面临的一大挑战或障碍就是技能差距。顺便说一句，我知道一家公司可以帮忙。*(咳，咳——今天在注册一个[免费 ACG 账户，不需要信用卡，或者在限定时间内获得](https://acloudguru.com/pricing)[年度会员 40%的网络周折扣](https://acloudguru.com/content/bf40-2021?utm_source=site&utm_medium=blogbyl&utm_campaign=2021_blackfriday)——咳，咳。)*

## 数据驱动的企业

**Scott** :就在这次拍摄之前，我有机会参加了一个名为*ENT20——数据驱动型企业:从愿景到价值*的会议。

顺便说一句，这就是我喜欢 re:Invent 的原因。我本打算去参加一次会议，但我迟到了一会儿；它完全被填满了。所以我改变了路线，去了大厅对面的会议，这绝对令人惊讶——特别是如果你在你的组织中处于试图弄清楚“我有数据，但我如何将这些数据转化为价值？我有这个愿景，我如何将它转化为价值？”

我看到那里有摄像机，所以他们正在拍摄，希望它能在网上结束。如果你正处于试图弄清楚“我们如何理解这一切”早期阶段你会从中获益良多。

## DeepRacer

斯科特:最后，我想对《极速赛车》的团队喊一声。 [DeepRacer](https://aws.amazon.com/deepracer/league/) 决赛今天举行，2021 年 DeepRacer 冠军队是 JPMC-罗格海德拉巴。

### 跟上 re:发明 2021

好了，我们要和你说再见了。通过在推特上关注 ACG，关注 T2，关注脸书，关注 T4，在 YouTube 上订阅一位云专家。查看 [ACG 和 Pluralsight re:Invent 内容中心](https://www.pluralsight.com/reinvent-2021)了解更多新闻和 AWS 资源。在 ACG 的不和谐社区上和思想不稳定的人聊天。继续牛逼吧，云大师们！