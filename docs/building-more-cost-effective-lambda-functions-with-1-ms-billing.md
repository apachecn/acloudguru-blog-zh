# Lambda:构建经济高效的功能|云专家

> 原文：<https://acloudguru.com/blog/engineering/building-more-cost-effective-lambda-functions-with-1-ms-billing>

AWS re:Invent 2020 最大的无服务器声明之一是 [AWS Lambda](https://aws.amazon.com/lambda/pricing/) 功能的 1 ms 计费。这是一项行业领先的变革，从根本上改变了许多无服务器应用程序的运行成本。

在这篇文章中，我解释了它的影响，并展示了如何优化 Lambda 函数来利用这个新特性。这可以帮助您进一步降低运行无服务器应用程序的成本。

## Lambda 计费的工作原理

Lambda 是一个按需计算平台——它只在响应事件时运行，你只需在代码运行时付费。

[λ定价](https://aws.amazon.com/lambda/pricing/)有两个维度——请求和持续时间。每当调用一个函数时，就会发生一个请求，不管函数的大小如何，费用都是每百万 0.20 美元。持续时间是作为时间和内存使用的一个因素计算的，每 GB 秒 0.0000166667 美元。还有一个[自由层](https://aws.amazon.com/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%2520Tier%2520Categories=categories%2523serverless)允许 100 万个请求和每月高达 400，000 GB/s 的计算。在这个级别下，你不需要为任何 Lambda 的使用付费。

在此次发布之前，计费的最小持续时间是 100 毫秒，计费持续时间总是四舍五入到最接近的 100 毫秒。这意味着，一个 5 毫秒的功能四舍五入到 100 毫秒，一个 385 毫秒的功能四舍五入到 400 毫秒。随着改为 1 毫秒计费，最小持续时间值现在是 1 毫秒，所有其他使用都四舍五入到下一个 1 毫秒。

## 从 100 毫秒到 1 毫秒的舍入-现有代码的成本差异

Lambda 是为非常高的流量而设计的，许多基于生产的应用程序会导致数百万次调用。持续时间粒度的这种变化为几乎所有的 Lambda 函数节省了成本，这将自动出现在您的 AWS 账单上。

为了了解这种价格变化对不同函数持续时间的影响，我比较了三种类型的 Lambda 函数:

1.  短命的(~100 毫秒):它们通常作为“粘合剂”运行，在 AWS 服务之间最低限度地处理数据。
2.  亚秒(1 秒以下):用于[更复杂的业务逻辑](https://acloudguru.com/blog/engineering/evolution-of-business-logic-from-monoliths-through-microservices-to-functions)处理更多数据。
3.  长期函数(不到 1 分钟):用于计算复杂的逻辑，或者同步调用第三方服务的函数。

下表对这三种功能的持续时间进行了随机抽样，然后按 1 毫秒和 100 毫秒的粒度对可计费持续时间进行舍入:

![](img/2044ad142858f0c825164469c0653f4a.png)

这表明，可计费持续时间的变化对运行短期功能的成本影响最大，在本例中，可计费持续时间缩短了 67%。对于亚秒函数，该示例显示平均持续时间下降了 10%,而对长期函数的影响较小。

实际上，在大多数生产工作负载中，Lambda 函数运行的时间很短，因此这里有很好的优化机会。

## 内存、成本和持续时间

作为 Lambda 开发人员，您可以使用的主要配置工具之一是内存。您可以在 128 MB 到 10 GB 范围内以 64 MB 为增量设置分配的内存。然而，内存也控制着可用于您的功能的虚拟 CPU 的数量，范围从 128 MB 的单核的百分比到最大内存的六个完整的虚拟 CPU。

对于许多计算密集型功能，增加内存会缩短整体持续时间。这意味着在许多情况下，您可以实现更快的功能，而对成本的影响可以忽略不计。要找到您的功能的最佳平衡，有几个选项。您可以手动测试一个具有不同内存分配的函数，以测量对持续时间的影响，或者您可以使用 [AWS Lambda 功率调整](https://github.com/alexcasalboni/aws-lambda-power-tuning)工具。

该工具有助于自动寻找内存、持续时间和成本之间的平衡，并将结果可视化。例如，计算密集型函数在不同的内存级别进行评估。结果图表显示，3008 MB 内存的性能最快，但 1024 MB 和 1536 MB 内存的成本最低:

![](img/78bcab60d7fdf142efa008ab4be68ea3.png)

当最短计费持续时间为 100 毫秒时，优化运行时间少于 100 毫秒的功能不会带来任何财务收益。虽然在这些情况下增加内存可能会减少毫秒数，但由于额外的内存使用量和最短持续时间不变，总体成本会增加。然而，随着 1 毫秒计费的出现，这一切都变了——现在有必要优化这些功能的效率。您可以采取许多步骤来优化这些短期运行的函数。

## 在 Node.js 中重用 TCP 连接

在 Node.js 中，默认的 HTTPS 代理为每个新请求创建一个新的 TCP 连接。如果您正在与 DynamoDB 之类的服务进行交互，此操作的延迟可能会比数据库请求所花费的时间更长。如果您的服务请求使用 [AWS 密钥管理服务](https://aws.amazon.com/kms/)，这种延迟也会增加。

您可以通过使用版本 [2.463.0](https://github.com/aws/aws-sdk-js/blob/master/CHANGELOG.md#24630) 中的 [AWS SDK](https://aws.amazon.com/tools/) 启用的标志来更改设置，以确保 TCP 连接被重用。最简单的方法是在 Lambda 函数中使用一个环境变量。通过将*AWS _ NODEJS _ CONNECTION _ REUSE _ ENABLED*设置为 1，函数的热调用将重用该连接。

本节引用了本[代码报告](https://github.com/aws-samples/building-faster-aws-lambda-functions)中的一个应用示例。我比较了将一个项目放入 [Amazon DynamoDB](https://aws.amazon.com/dynamodb/) 表的延迟，有和没有重用标志。我在 300 秒内对 1000 个请求的每个函数运行了一个[负载测试](https://aws.amazon.com/blogs/compute/load-testing-a-web-applications-serverless-backend/)。使用这个 [CloudWatch Insights](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/AnalyzingLogData.html) 查询，我可以分析持续时间平均值和百分比指标:

```
filter @type = "REPORT"
| stats
    avg(@duration) as Average,
percentile(@duration, 99) as NinetyNinth,
percentile(@duration, 95) as NinetyFifth,
percentile(@duration, 90) as Ninetieth
by bin(60m)
```

在没有重用标志的示例代码的 v1 中，结果如下:

![](img/ca962e7ba7b555e970c349cb8166faac.png)

在示例代码的 [v2 中，](https://github.com/aws-samples/building-faster-aws-lambda-functions/tree/main/v2) [AWS 无服务器应用模型](https://aws.amazon.com/serverless/sam/) (AWS SAM)模板在函数定义中将标志作为环境变量传递:

```
AddToDDBfunction:
    Type: AWS::Serverless::Function 
    Properties:
      CodeUri: addToDDBfunction/
      Handler: app.handler
      Runtime: nodejs12.x
      MemorySize: 128
      Timeout: 3      
      Environment:
        Variables:
          AWS_NODEJS_CONNECTION_REUSE_ENABLED: 1  
```

在此版本上运行相同的负载测试，CloudWatch Insights 查询显示了性能提升:

![](img/f1d9ddaa4b930e48dded27e901bf79d0.png)

如果这两个功能都被调用 100 万次，这些平均持续时间指标显示成本降低了 23%:

| 
 | **请求** | **内存(MB)** | **持续时间(毫秒)** | **GBs** | **请求$** | **持续时间$** | **总计** |
| ***v1*** | 1,000,000 | 128 | 56 | 0.007 | $0.20 | $0.12 | $0.32 |
| ***v2*** | 1,000,000 | 128 | 21 | 0.002625 | $0.20 | $0.04 | $0.24 |

## 优化 Node.js 的依赖关系用法

当您*需要*函数中的 JavaScript SDK 时，它会导入整个 SDK，但您的函数可能只使用一两个 AWS 服务。这是来自示例的[版本 2](https://github.com/aws-samples/building-faster-aws-lambda-functions/tree/main/v2) 的代码:

```
const AWS = require('aws-sdk')
AWS.config.region = process.env.AWS_REGION 
const docClient = new AWS.DynamoDB.DocumentClient()
```

您可以通过仅[请求您的函数中使用的服务](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/creating-and-calling-service-objects.html)来减少内存使用和初始化时间。为此，更新 require 语句来指定服务，然后将任何配置选项传递给服务构造函数，如示例的[版本 3](https://github.com/aws-samples/building-faster-aws-lambda-functions/tree/main/v3) 所示:

```
const DynamoDB = require('aws-sdk/clients/dynamodb')
const documentClient = new DynamoDB.DocumentClient()
```

此版本的负载测试在 CloudWatch Insights 查询中显示了以下结果:

![](img/f6b8aa884b407a28dfa21460ad630623.png)

与原始版本相比，这将持续时间成本降低了约 75%，总体成本降低了 26%:

| 
 | **请求** | **内存(MB)** | **持续时间(毫秒)** | **GBs** | **请求$** | **持续时间$** | **总计** |
| ***v1*** | 1,000,000 | 128 | 56 | 0.007 | $0.20 | $0.12 | $0.32 |
| ***v2*** | 1,000,000 | 128 | 21 | 0.002625 | $0.20 | $0.04 | $0.24 |
| ***V3*** | 1,000,000 | 128 | 16 | 0.002 | $0.20 | $0.03 | $0.23 |

## 亚 100 毫秒函数的其他优化

还有其他几个因素需要考虑，这些因素可能会缩短函数的总持续时间。您的用例将决定您可以应用哪些。

首先，您对运行时的选择很重要。尽管 Lambda 服务对运行时是不可知的，但是一些运行时比另一些运行时初始化得更快。对于短函数，可以考虑使用 Node.js、Go 和 Python 这样的运行时，它们通常可以运行得更快。

让您的部署包尽可能小，因为较大的包通常需要较长的初始化时间。您应该删除函数不直接使用的任何需求或库导入。此外，避免包含多个代码路径的“单一”函数，尽可能缩小您的代码，以帮助获得尽可能小的部署包大小。

确保在全局范围内定义了任何需要初始化的全局对象，如数据库连接。这是 Lambda 处理函数之外的代码，也称为“INIT”代码。如果同一个执行环境被多次调用，那么任何冗长的初始化代码的成本都会分摊到多次调用中。

寻找更多的云转型善？看看这些:

## 结论

对于 Lambda 函数的新 1 ms 计费，优化代码持续时间对运行 Lambda 函数的成本有直接影响。寿命较短的函数通常只需做一些小的改动就可以运行得更快，这就意味着降低了成本。

Lambda 中的内存分配决定了函数的 CPU 能力。为了帮助确定持续时间、成本和内存之间的最佳平衡，请使用 AWS 功率调整工具。“重用 HTTP 连接”标志有助于减少 Node.js 函数中的延迟，您可以使用环境变量来启用它。选择性地选择要导入的 AWS SDK 的一部分还可以减少持续时间，而不会影响业务逻辑的功能。

想采取下一步措施提升您自己或您的团队在无服务器应用方面的技能吗？云专家提供最新的课程库来超越你的简单项目。例如，为您的下一个无服务器项目利用 [aws 图形数据库](https://acloudguru.com/course/go-serverless-with-a-graph-database)的力量！立即开始您的[免费试用](https://acloudguru.com/pricing)或与我们交流您的需求。

要获得更多帮助您充分利用基于 Lambda 的应用程序的技巧和诀窍，请访问[无服务器世界](https://serverlessland.com/)。