# # CloudGuruChallenge-AWS 上的事件驱动 Python 

> 原文：<https://acloudguru.com/blog/engineering/cloudguruchallenge-python-aws-etl>

### 挑战步骤

你需要安装 [Python3](https://www.python.org/downloads/) 并访问 AWS 环境。 *查看[这篇来自 AWS 英雄 Ben Kehoe 的文章](https://read.acloud.guru/my-python-setup-77c57a2fc4b6)，了解如何建立一个健康的 Python 开发环境。*

![Flowchart of an example ETL job](img/6c739282d3587ccb06672cc4b2746fce.png)

1.  **ETL 工作。**创建一个按每日计划运行的 Python 计算作业。你可以通过创建一个 Python Lambda 函数来实现，然后[从每天一次的 CloudWatch 规则](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/RunLambdaSchedule.html)中触发它。或者，您可以创建一个 s [调度的 Fargate 任务](https://docs.aws.amazon.com/AmazonECS/latest/userguide/scheduled_tasks.html)，或者使用 AWS Glue 查看[调度任务。唯一的要求是底层计算必须每天触发一次，而不是在持续轮询的服务器上。](https://docs.aws.amazon.com/glue/latest/dg/monitor-data-warehouse-schedule.html)
2.  **提取。**在你的 Python 代码中，从 Github 下载[这个 CSV 文件](https://github.com/nytimes/covid-19-data/blob/master/us.csv)。(这是来自《纽约时报》维护的存储库的美国新冠肺炎数据的每日转储。每天，该文件都会更新一行额外的数据。)将数据加载到内存中的对象中。
3.  **转型。**用 Python 代码执行数据操作。
    *   **清理**–日期字段应该转换成日期对象，而不是字符串。
    *   **加入**–我们希望显示恢复的病例以及确诊病例和死亡病例。NYT 的数据不跟踪恢复，所以你需要从这个约翰霍普金斯数据集的[中提取我们的恢复数据，并将其合并到你每天的记录中。*注:约翰·霍普金斯数据集的病例数和死亡数与 NYT 的数据不一致。我们将把 NYT 的数据视为权威数据，并且只复制来自约翰霍普金斯大学的恢复数据。)*](https://raw.githubusercontent.com/datasets/covid-19/master/data/time-series-19-covid-combined.csv)
    *   **过滤**–从约翰霍普金斯数据集中删除非美国数据。删除两个数据集中不存在的任何日期。(有一个逐个关闭的问题。)
4.  **代码清理。**将你的数据操作工作抽象成一个 [Python 模块](https://www.learnpython.org/en/Modules_and_Packages)。这个模块应该只执行转换。它不应该关心 CSV 文件存储在哪里，并且在下一步中不应该知道任何关于数据库的信息。
5.  **加载。**现在，编写代码将转换后的数据加载到数据库中。出于本练习的目的，您可以使用您选择的任何数据库。我建议使用 DynamoDB 搭配 boto3 或者 RDS Postgres 搭配 pyscopg。无论哪种方式，您都希望表中的每条记录都包含疫情一天的日期、美国病例数、死亡人数和恢复情况。
6.  **通知。**当数据库更新后，您的代码应该触发一条 SNS 消息，通知任何感兴趣的用户 ETL 作业已经完成。该消息应该包括数据库中更新的行数。
7.  **错误处理。**您的代码应该能够处理这些常见的控制流情况:
    1.  初始加载与更新-您应该能够在作业首次运行时将整个历史数据集加载到数据库中，然后仅使用最近一天的数据进行更新。
    2.  如果数据包含意外或格式错误的输入，您的代码应该会正常失败，并通过 SNS 报告一条错误消息。下次您的作业运行时，它应该记得它没有成功处理以前的数据，并在继续处理更新的数据之前重试。
8.  **测试。**为了确保您的代码能够处理意外情况，请对您的代码进行单元测试，用无效数据替换新冠肺炎 CSV 文件，并确认您的代码能够正确响应。
9.  **IaC。**确保您的基础设施(Lambda 函数、CloudWatch 规则、SNS 触发器、数据库等)在代码(CloudFormation、Terraform 或类似代码)中定义
10.  **源码控制。**将你的代码和配置存储在源代码控制中(GitHub，或者类似的)
11.  **仪表板。**没有报告的 ETL 流程会是什么样的？看看你能否[将你的数据库连接到 AWS Quicksight](https://docs.aws.amazon.com/quicksight/latest/user/enabling-access-rds.html) 或其他 BI 服务，如 Tableau，以生成一段时间内美国病例数、死亡率和恢复情况的可视化。
12.  **博文。**(非常重要)写一篇简短的博文，解释你的收获和应对挑战的方法。链接到您的数据可视化，以便我们可以尝试一下！如果你没有自己的博客， [Hashnode](https://hashnode.com/) 或 [dev.to](https://dev.to) 是一个很好的起点。

* * *

*有兴趣升级或开始您的云开发之旅吗？云专家的 [AWS 开发者学习路径](https://acloudguru.com/learning-paths/aws-developer)提供适合初学者和高级专家的定制课程！*

* * *

### 当你完成的时候

你可以自己或与他人合作完成项目要求。欢迎在论坛或社交媒体上使用#CloudGuruChallenge 标签提问[！](https://acloud.guru/forums/cloud-guru-challenge/recent?p=1)

当你完成项目的所有步骤后，在指定的[论坛](https://acloud.guru/forums/cloud-guru-challenge/recent?p=1)主题中发布你的博客文章的链接。**然后我将能够在 LinkedIn 上为你在这个项目中展示的技能背书:Python、事件驱动编程和 AWS。**(你还将有机会赢得一些超酷的奖品！)

最重要的是，#CloudGuruChallenge 是免费的，每个人都可以使用；你所需要的就是[一个 ACG 免费会员](https://acloudguru.com/pricing)来发表你的论坛帖子。

### 资源

准备好做一些谷歌搜索，但是如果你是 ACG 会员，这里有一些资源可以帮助你更好地使用 Python 和事件驱动编程:

[Python 开发简介](https://acloud.guru/learn/df3778be-ba58-4be7-a232-aa658bed7517) (16 小时课程)

[使用 Python 进行数据管理和报告](https://acloud.guru/learn/a0abe7d4-ce82-4dfe-beb9-21d98f4c6941?_ga=2.70420368.1665217949.1599591206-415638573.1596472192) (6 小时课程)

[在 AWS 上构建全栈无服务器应用](https://acloud.guru/learn/871c7714-6ba7-46f9-9458-b60c779e5a18?_ga=2.58421034.1665217949.1599591206-415638573.1596472192) (8 小时课程)

你不需要执行这些额外的步骤来“宣布胜利”,但它们将帮助你的项目脱颖而出，并提供令人敬畏的额外学习。

1.  使用 GitHub Actions、AWS CodePipeline 或类似的服务为您的 ETL 管道创建 CI/CD 管道。您的目标应该是每当您对您的源代码控制库进行更改时，都在 AWS 中更新您的 Python 代码和基础结构。
2.  向您的 CI/CD 管道添加一个“冒烟测试”,下载一个示例 CSV 文件，对其运行转换，并将其存储在数据库中，然后验证是否将正确的消息发布到 SNS。找到一种不影响正常日常作业运行的“生产”数据的方法。
3.  想办法创建一个实时更新的仪表板！

请注意，如果您对更有趣的可视化有想法，欢迎调整建议的特定数据转换和数据字段。尽情发挥创造力吧！

### 最终外卖

乍看之下，这一挑战似乎并不华丽。毕竟，它实际上只是从某个地方获取一些数据，将其与其他一些数据相结合，然后将其存储在其他地方。但是像这样的数据操作是云专业人员面临的一个非常常见的实际问题！以及所有这些棘手的情况——如果外部数据格式突然改变，会发生什么？—导致一些强大的复杂性。

熬过这一关，你就能在下一次求职面试中拿出一个精彩的故事。我保证你的招聘经理会开始想一两个他们自己的故事。

祝你好运！