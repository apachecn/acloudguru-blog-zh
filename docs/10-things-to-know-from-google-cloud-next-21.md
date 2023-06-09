# 从 Google Cloud Next 21 了解 10 件事

> 原文：<https://acloudguru.com/blog/engineering/10-things-to-know-from-google-cloud-next-21>

欢迎来到这个月的 GCP！这个月，我们来看看 Google Cloud Next’21 的一些重要成果。在这篇文章中，我和我的同事 GCP·古鲁·博达斯·帕尔默和乔·洛维里一起讨论了我们认为最激动人心的公告和他们认为最难忘的会议[。](https://acloudguru.com/videos/gcp-this-month/gcp-this-month-new-cloud-storage-features-added-cloud-functions-support-new-toronto-region)

* * *

## 获得新的 GCP 技能

*[今天就和云专家](https://acloudguru.com/pricing)一起开始，边做边学。ACG 可以通过围绕 Google Cloud、AWS、Azure 等的课程和实际动手实验室，帮助你掌握新技能并转变你的职业生涯。*

* * *

Mattias: 我很想听听你最喜欢的公告是什么。你们觉得什么特别？

## 1.大戟项目

乔:嗯，我必须承认一件事:没有什么特别喜欢的公告。像大多数会议一样，很多时候，我会去看演示。我想看一些新鲜热辣的东西，他们给我送来了。

在开发者主题演讲的开幕式上，谷歌技术基础设施高级副总裁 Urs hlz le 用五种不同的语言一句接一句地发言:英语、法语、印地语(我想)、西班牙语，然后是德语。除了英语和德语之外，他对这些语言都不流利，但是他的声音被用作模型，他的讲话被复制以便他能说话。

这是谷歌研究和 DeepMind 的衍生项目**项目** **Euphonia** 的成果，他们使用语音转文本技术，试图帮助那些难以被理解的人被更广泛地理解。

因此，首先数字设备可以理解它们，然后我们可以弥合这一差距，让人们理解数字设备。我想，“哇，这难道不是一个真正狂野的应用吗？也许我们会看到用演员自己的声音进行语言配音。”

##  2。**顶点 AI 工作台**

对我来说，它也更深入地研究了[机器学习](https://acloudguru.com/blog/engineering/what-is-machine-learning-as-a-service-mlaas)和人工智能，这也是我试图了解更多的东西。我喜欢的一件事是**顶点人工智能工作台**。不仅了解到这一点，谷歌 Next 也在这方面做了快速的启动。他们采用了客户终身价值模型。他们使用 [BigQuery](https://acloudguru.com/hands-on-labs/working-with-bigquery-in-google-cloud-shell) 进行分析，然后使用 [TensorFlow](https://acloudguru.com/course/tensorflow-developer-certificate-exam-prep) 和[顶点 AI](https://acloud.guru/series/gcp-this-month/view/305) 。

他们分析了客户的消费金额和消费频率，并据此建立了一个基线。然后他们用带有 TensorFlow 和 Vertex AI 的 [Docker](https://acloudguru.com/course/docker-deep-dive) 容器创建了一个训练模型。这将作为模型使用顶点 AI 预测的端点。快速入门真的帮助我了解了更多关于 Vertex AI 的知识，以及如何从可用于 TensorFlow enterprise 的托管笔记本中使用它，以及如何从您自己创建的新笔记本中使用它。所以这是一个非常神奇的工具，我很高兴我深入了解了它。我已经觉得自己更聪明了！

乔:这种对人工智能的强调实际上是谷歌在整个行业的主要推动力之一，几乎是他们所做的一切。他们真的试图越来越多地引入这一点，你可以看到它开始在不同的领域和不同的服务中全面涌现。那真令人兴奋。Mattias，你最大的收获是什么？

##  3。谷歌分布式云

马蒂亚斯(Mattias):我总是对所有的无服务器公告感兴趣，但我相信我们很快也会谈到这些。但是让我印象深刻的是**谷歌分布式云**。

谷歌分布式云是一个非常有趣的包装，为你提供了不同的管理方式。当你谈论 Vertex AI Workbench 时，我将提到我有多喜欢托管服务，因为为我们做工作是我真正欣赏的。因此，让他们通过谷歌分布式云接触到更多的地方——我认为这是一件非常有趣的事情。他们有四类为你管理东西的地方。这是谷歌网络边缘，有他们所有的存在点，在世界各地有 140 个。

Mattias :运营商与电信公司互动，管理手机和其他连接设备的响应能力。一个是客户优势，比如在工厂车间或零售店，他们需要在那里进行处理，并具有响应能力或离线能力等。还有客户数据中心。因此，不仅仅是谷歌的云，还有客户数据中心、colo 设施或其他任何东西，这还没有涉及到他们现在如何为多云提供新的 API。

他们演示了通过 Anthos 的多云 API 部署到 GCP 和 Azure，他们只是在各地推广，对吗？所以，如果你想让谷歌帮你管理东西，这是最好的方法。我认为这是许多真正有趣的东西，它们聚集在一起，嗯，将许多组织的产品包放在一起，这些组织正在考虑云计算，希望获得这种功能，但也希望获得不必管理东西的好处。

## 4.谷歌的多云焦点

Joe: 你知道，我认为这确实反映了谷歌的很多世界观，也是你我经常谈论的一些东西；他们不会认为“嘿，每个人都来我们的平台，我们会教你我们的平台。”不，他们想要的是让人们知道如何在现实世界中工作。他们意识到不是每个人都在云上，但是人们正在往那里移动。所以他们想让这变得更容易。他们基本上是去顾客所在的地方。无论你是在处理混合云的情况，使用你的本地云，希望是[谷歌云](https://acloudguru.com/blog/engineering/what-is-google-cloud-platform-gcp)(但也可能不是)，还是尝试去多云化，利用 Azure 的一些更好的服务或更好的 AWS。并将这些与一流的谷歌云服务相结合。所以，这整个方法，这种分布式云的工作方式，我认为对我来说这就是谷歌的世界观。这是他们看待现实的方式。

是的，我完全同意。尤其是涉及到数据的时候。即使在云环境中孤立数据也容易出错。因此，理解到允许他们的客户基于不同的云平台查询数据是 BigQuery Omni 现在正式发布的原因。因此，我认为这是谷歌很久以前就意识到的事情，甚至在创建 [Kubernetes](https://acloudguru.com/course/kubernetes-deep-dive) 的时候。

* * *

[![Complete guide to the Cloud and Dictionary ](img/93ebf63b88ab7fbd48705a01952ba688.png)](https://get.acloudguru.com/cloud-dictionary-of-pain)

[**获取谷歌云痛苦字典**](https://get.acloudguru.com/cloud-dictionary-of-pain?ajs_aid=8b2cc73f-c0e0-442b-ba6d-0eb362250ebb)
说云不一定要硬。我们分析了数以百万计的回复，找出了最容易让人犯错的概念。抓住这个[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)获取谷歌云中一些最痛苦术语的简洁定义。

* * *

## 5.BigQuery Omni

**Mattias:** Broadus，我真的很高兴你提到了 BigQuery Omni，因为我觉得 BigQuery Omni 在它所代表的东西上真的很有趣。

我们都听说过 BigQuery。我们已经看到 BigQuery 有多受欢迎。能够对所有数据进行查询，甚至以无服务器的方式使用 ESQL 查询，并且能够通过 AWS 和 Azure 上的 BigQuery Omni 访问 BIgQuery，仅仅是普遍可用就真的很棒。我真的很兴奋，现在这是可行的，但我也很兴奋，因为我认为这意味着谷歌正在考虑他们已经得到的其他技术。这些谷歌工程师显然是非常聪明的人，我们喜欢他们所做的一切。我们爱 GCP，因为那里有很多好东西。我认为他们也在考虑将更多这些东西带到其他云上。我很想看看他们会带来什么。

**Broadus:** 谷歌现在正在成为一个平台，这不是说，“嘿，来我们的平台，使用我们的产品，”而是他们正在做的是找出其他云平台需要什么——他们的客户需要什么。所以现在，AWS 和 Azure 需要它们的服务来运行。所以，使用谷歌服务，现在他们只是收集数据，分析它如何工作，如何帮助，如何整合。然后，创新将出现在他们带来这些云平台本身需要的服务的地方。所以，消除竞争，但要合作。这创造了一个更大的云市场。这就是我看到的发展方向。

## 6.GCP 无服务器

Joe: 哦，他们还利用 BigQuery Omni 获得了一项现有的服务并对其进行了扩展。你之前提到过无服务器，我知道你有点迫不及待地想要得到无服务器的东西。因此，我将在这一点上击败您，因为我同意，而且我看了一下无服务器的情况。

这很有趣，因为他们说我们经历了云功能和云运行的所有重大变化，在较小程度上，是云构建。但是他们真的在利用自己的优势，在这些优势的基础上更上一层楼。

例如，在云函数中，他们增加了更多的运行时。他们有红宝石。NET Core，甚至 PHP，而且他们已经将 Python 更新到了更新的版本，比如 3.9 和 node。JS——他们甚至在预览版本 16。所以他们真的在向前发展，但他们也扩展了云功能的功能，以及如何与他们合作进行定制。所以你有私人工人池。现在，您可以指定一个私有的工人池，甚至为此构建环境变量，而不是让云函数的构建完全脱离您的控制。最好的事情之一是他们在功能中增加了最少的实例，这将有助于人们避免一个快速运行的功能的冷启动。但是，如果你有一个暖云功能已经设置好了，你就完全避免了冷启动的时间框架。

Mattias: 虽然我是一个无服务器纯粹主义者，但我想说的是，能够为云函数设置最少的实例实际上是一件好事。实际上，云运行也是一样，你可以固定它，让它们运行来做后台处理等等。

它确实适合不仅仅是事件驱动的模型的情况，我认为它所做的是帮助更多的组织以适合他们的方式采用这些技术。我不知道这在开发团队的对话中出现了多少次，比如“哦，好吧，我们要做什么？比如，我们需要重新实现整个过程吗？”我是说，这种事多久能被批准一次，对吧？除非是超级快的事情。真的没有。因此，能够通过采用适合您的环境的方法，然后看一看调整的东西，沿着这条路改变它们，从而获得更大的进步，渐进的进步总是一个值得考虑的伟大策略，对吗？

## 7.云运行

**Joe:** 你提到云运行是即将推出的一些增强功能的一部分。我真的被那里发生的事情吸引住了。

现在他们有了他们所谓的第二代执行环境，你可以选择，它提供了更高的网络和 CPU 性能。它们拥有完整的 Linux 功能，甚至网络文件系统支持。我觉得这有点惊人。

正如你所说，他们现在允许你用一个新的模拟器在本地开发你的云运行应用，他们甚至可以用一个三个字的命令在本地部署。我是说，你一定会喜欢这三个字的命令！我一直有点嫉妒 App Engine。您可以云、应用、部署和运行！所有其他 GCloud 命令都是 15 个单词，带有双破折号标志和所有内容。所以云跑现在已经爬上了那艘船，现在它可以滑动这面旗帜 GCloud run deploy 了。因此，他们通常运行得非常快，这就需要一种服务，这种服务获得了很大的吸引力，并对其进行了改进，还增加了很多安全性。全面加强安全似乎也是会议的一个主题。

Mattias: 嗯，我当然喜欢简短的命令行，因为我是按字符付费的。但是从开发者的角度来看，可用性是一件大事。因此，没有真正复杂的东西，然后能够在仿真器中本地部署调试，这是一件非常重要的事情。很长一段时间以来，无服务器的开发故事一直是朝着那个方向和那个战略的最困难的部分之一，我很高兴这些事情现在得到了这么多的关注和支持。

## 8.谷歌工作流程和文档人工智能

**Broadus:** 是的，这是一个有趣的观点，Mattias，还有与 Google Workflows 的合作，你现在已经实现了 HTTP 回调，GCP API 连接器，在 Google Next 他们正在讨论与 Document AI 的合作，这是来自 GCP 的新 API，真的会与 Typeform 这样的服务竞争。现在你可以使用人工智能和典型的机器学习来理解你需要的文档类型。看看文件结构的位置，以及你的文件应该如何放置，看你是否有发票，合同，任何你真正要展示的东西。工作流是一个很好的工具，它与内存和并发性密切相关。

因此，我已经看到了谷歌工作流的一些令人兴奋的东西，特别是我认为值得一试的文档人工智能。他们有一些 GitHub，你可以从中提取。您甚至可以深入了解如何创建和部署服务帐户，并看看在现实情况下是什么样子。

## 9.一流的火花支持

Mattias: 另一件很酷的事情是第一类 Spark 支持，因为现在谷歌将为你管理 Spark。我喜欢谷歌为我们管理东西。其中之一就是无服务器，所以开发者可以忽略所有的集群。您只需提交一个作业，然后 Google 将负责为您提供集群和自动扩展，以确保该作业正常运行。所以拿走所有你不需要关心的东西绝对是一件好事。其他地方也有一流的 Spark 支持。现在，这些是在私人预览中，但你可以在 BigQuery，Vertex AI 和 DataPlex 中获得。因此，对于使用 Spark 的人来说，这些绝对是一些额外有趣的优点。

## 10.必看片段

**Broadus:** 我想谈谈 Google Next’21 上的必看片段。

对我来说，一个必须观看的部分是与文斯·瑟夫和吉姆·霍根关于技术残疾的有趣对话。吉姆·霍根谈到了自己的自闭症，他不太愿意把这一点告诉他的同龄人和雇主。但在谷歌，他找到了一个家，在那里他不仅感到被接受和培养，而且他觉得谷歌实际上是在通过培训其他员工来了解残疾人的感受以及如何与他们沟通和联系来发表声明。这是一个非常棒的会议，看到谷歌采取主动，许多公司甚至不敢试图理解。能够拥有这样一个包容性的生态系统来帮助每个人茁壮成长，我认为这是一件大事。为谷歌喝彩。

马蒂亚斯:我也赶上了那场比赛。这绝对是一部值得一看的电影，它让我们能够在与人交往时审视自己的一些假设。我们对此有什么假设？我们怎样才能做得更好？

**Joe:** 如果人们还没有机会观看开发者主题演讲，我会回去推荐他们观看，因为它不仅有我提到的关于文本到语音转换和不同语言的精彩演示，还有对 Euphonia 项目的很好的参考，以及一个非常有趣的链接，而且它们真正触及了为什么他们是一家面向开发者的公司的主要关键点， 他们介绍了很多工具，你们可能很熟悉，比如 Cloud Shell，但他们更深入地介绍了这些工具，真正解释和揭示了一些我不知道或不记得的东西，或者它的一些功能。 而且一直在扩大。

我想提到的另一件事是，安全确实是贯穿整个会议的一个大主题。特别提到的是，谷歌现在正在坚持 SALSA，这是一种行业标准，不仅仅是一道美味的菜肴，但他们正在将它用于他们的 Anthos 服务网格和云构建混合系统，这允许完全合规，并允许谷歌实施二进制授权，以便可以设置策略来确保正在部署的是贵公司希望部署的。

Mattias: 是的，二进制授权是那些听起来不太令人兴奋的事情之一，但它实际上保护了业务和开发管道。我真的很高兴看到他们正在整合更多的地方。所以这很酷。

你提到安全是主题之一。我想我们也谈到了多样性和包容性这一主题。实际上，我经常看到的另一个主题是可持续性和环境影响。我看到他们有许多新工具可供人们使用，以确定他们运行的工作负载对环境的影响。

## 最终外卖

**Broadus:** 我最后要说的不是谷歌这次专注于更多的新服务，而是对现有服务的更多改进，以及他们试图与其他公司和其他云服务提供商建立的关系。然后，我认为在未来的一两年内，可能会创新一些更多的解决方案，并帮助其他云服务提供商在生态系统中蓬勃发展。所以这一切都是关于可持续性，安全性，更多的是关于人工智能和机器学习的未来。谷歌掌握着这一切。

**Joe:** 我们都没有谈到的关键创新之一，我认为我们真的应该关注的是谷歌如何设法提高会议的效率。我是说，去年，那是什么？九周的会议？现在看看他们。他们只剩三天了。我是说，这太惊人了。你不得不佩服这种效率。

马蒂亚斯:嗯，我得感谢你们两位。我真的很高兴与你谈论谷歌云 Next’21。这就是这个月的全部内容，但我们很乐意继续与您交谈。加入我们的 [Discord](http://discord.gg/acloudguru) ，让我们知道你对 Google Cloud Next’21 的想法。保重，保持安全，继续成为令人敬畏的云大师！

## 关注谷歌云的一切

你知道云专家有一个免费账户层吗？不需要信用卡！每个月你都可以参加一套新的免费课程？查看[本月免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)，在这里报名[。](https://acloudguru.com/pricing)

*想跟上万物云？[在 YouTube 上订阅云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每周云新闻，在[脸书](https://www.facebook.com/acloudguru)上关注我们，在 [Twitter](https://twitter.com/acloudguru) 上关注我们，或者在 [Discord 上加入对话！](http://discord.gg/acloudguru)*