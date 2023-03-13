# CDK vs Terraform vs Cloud formation |云专家

> 原文：<https://acloudguru.com/blog/engineering/cloudformation-terraform-or-cdk-guide-to-iac-on-aws>

CDK vs 地形 vs 云层——哪个更好？了解 AWS 上这些基础设施代码(IaC)工具的更多信息，并找出最适合您的工具。

我已经与 Amazon Web Services 合作多年，虽然随着时间的推移，云已经发生了很大的变化，但有一点是始终如一的:**基础设施即代码(IaC)是 AWS 健康实施的核心支柱。**

对于任何比玩具云应用更大的东西，IaC 都是赌注。你很难找到一个管理任何规模的人认为让人们在控制台上点击是最佳途径。

这些天来，我发现从我的所有应用程序甚至是 IaC 工具的概念验证开始更快。一次又一次，我发现在几周或几个月后再回到项目上，很快就能从熟悉的基线和环境中理解事情是如何运作的。我不需要在我的脑海中从头开始重建我的想法。

当然，“如何”接近 IaC 是 AWS 工程师自己版本的老“制表符对空格”的争论。

那么，AWS 中有哪些 IaC 工具可供您使用，您如何在它们之间进行选择？请继续阅读我们对 AWS CloudFormation、AWS Cloud Development Kit 和 Terraform 的总结和比较。

* * *

**通往更好职业的钥匙**

[立即开始 ACG](https://acloudguru.com/pricing) 通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室来改变你的职业生涯。

* * *

## AWS 云阵

[AWS CloudFormation](https://aws.amazon.com/cloudformation/) 是 AWS 的原始 IaC 工具，于 2011 年发布。我对它描述和管理基础设施的能力产生了尊敬、厌恶、喜爱和敬畏。CloudFormation 最初只在 JSON 中提供，但我们在 2016 年得到了一个 tabs vs spaces 的帮助，实际上与[本地 CFN YAML 支持有关。](https://www.trek10.com/blog/cloudformation-yaml-and-why-its-awesome)

CloudFormation 是构建、管理、更改和销毁基础架构中资源的最安全方式之一。它提供了健壮的资源状态管理，现在它可以在您运行部署之前告诉您将要发生什么。

让我们来看看让 CloudFormation 变得令人愉快和高效的一些优秀特性。

### **云形成宏和变换**

AWS CloudFormation 的强大功能之一是[宏](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-cloudformation-macro.html)和[转换](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/transform-section-structure.html)，这带来了全新的功能，可以添加您自己认为有价值的功能。

想象一下，能够提供自以为是的 IAM 策略生成器或 S3 资源宏——无论您想做什么，宏都可以帮您实现。请注意。虽然功能强大，但最终可能会踏入危险的领域，因为有效地构建自己的特定领域语言(DSL)变得很容易。您没有使用 CloudFormation 来管理您的资源，而是将 CloudFormation 作为一个糟糕的 DSL 编译器来使用，您将不得不照看它。

### **资源提供者**

有一段时间，我们只有[个定制资源](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-custom-resources.html)来供应和管理 AWS CloudFormation 本身不支持的资源。这现在很大程度上被[资源提供者](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-macros.html)所取代，它允许你创建私有或公开的提供者，将第三方和不受支持的资源管理到你的堆栈中。例如， [Datadog](https://www.datadoghq.com/blog/monitoring-as-code-with-datadog-and-cloudformation/) 是一款流行的监控工具，可以在您的堆栈中使用，以提供和管理监控，而无需一些带外流程。

在我最近使用 AWS CloudFormation 的大部分工作中，我默认使用 AWS 无服务器应用程序模型，或 [SAM](https://aws.amazon.com/serverless/sam/) 。SAM 是 CloudFormation 的一个超集，通过一些方便的转换，您可以更少地输入和连接各种资源和权限。把它想象成一个经过深思熟虑和“管理”的宏。如果您正在使用 AWS Lambda 或事件驱动计算，并且希望提升您的 YAML 争论水平，请从 SAM 开始。

## AWS 云开发套件(CDK)

[AWS 云开发套件](https://aws.amazon.com/cdk/)(CDK)2019 年发布。使用熟悉的编程语言并提供了 TypeScript、Python、Java 和。NET 中，开发人员可以使用与他们的堆栈的其余部分相同的代码来管理他们的基础设施。

然而，CDK 并非没有自动气象站的云系。事实上，CDK 合成了云的形成。通过采用 CDK，您仍然可以利用云形成的所有状态管理和固有的好处(和缺点)。

一个小题外话:我想强调的是，有些人认为 CloudFormation 是 AWS 的“汇编语言”,主要是因为有很多工具“编译”成 CloudFormation。我认为这是一个危险的比较。这可能会导致一种解释，即像任何高级汇编语言一样，您不需要真正理解低级指令集如何有效地利用高级结构。根据我的经验，在云形成的情况下，这显然是不真实的。即使对它有一个初步的了解，也能在像 CDK 这样的高级用法中做出更好的决定。

最后，我认为 CDK 是开发人员开始构建云原生应用程序的最舒适和最自然的切入点。

让我们来看看 AWS CDK 的一些主要功能。

### **构造**

CDK 最强大的功能之一——我相信 AWS CloudFormation 一直在努力提供——是真正可共享和可重用模块的想法。CDK 引入了[结构](https://docs.aws.amazon.com/cdk/latest/guide/constructs.html)的概念。实际上，构造提供了一切，从您希望在项目中重用的一些特定默认设置的简单包装，到复杂的多资源编排和[资源提供者的包装](https://docs.aws.amazon.com/cloudformation-cli/latest/userguide/resource-types.html)。这些构造的分发方法依赖于本机。

CDK 构造的另一个重要部分是一个叫做 [jsii](https://github.com/aws/jsii) 的东西。对项目进行报价；“jsii 允许任何语言的代码自然地与 JavaScript 类交互。正是这项技术让 AWS 云开发套件能够从单一代码库交付多语言库！”。如果您用 TypeScript 编写构造，那么跨其他核心 CDK 语言分发和利用这些构造是相当简单的——这进一步鼓励了模块的共享。

我可以用一种最优雅的方式来说明 CDK 的体验有多好，那就是并排展示亚马逊州语的用法对比。

首先，它在 AWS CloudFormation Native ASL 中是什么样子的:

```
{
  "DeliveryStepFunctionStateMachine": {
    "Type": "AWS::StepFunctions::StateMachine",
    "Properties": {
      "RoleArn": {
        "Fn::GetAtt": ["DeliveryStepFunctionStateMachineRoleC6479370", "Arn"]
      },
      "DefinitionString": {
        "Fn::Join": [
          "",
          [
            "{\"StartAt\":\"MapperTask\",\"States\":{\"MapperTask\":{\"Next\":\"SetStatusTo-pending\",\"Retry\":[{\"ErrorEquals\":[\"States.ALL\"],\"MaxAttempts\":10}],\"Parameters\":{\"FunctionName\":\"",
            {
              "Ref": "DeliveryStepFunctionMapper"
            },
            "\",\"Payload.$\":\"$\"},\"OutputPath\":\"$.Payload\",\"Type\":\"Task\",\"Resource\":\"arn:",
            {
              "Ref": "AWS::Partition"
            },
            ":states:::lambda:invoke\"},\"SetStatusTo-pending\":{\"Next\":\"retry seconds\",\"Type\":\"Task\",\"ResultPath\":null,\"Resource\":\"arn:",
            {
              "Ref": "AWS::Partition"
            },
            ":states:::dynamodb:updateItem\",\"Parameters\":{\"Key\":{\"pk\":{\"S.$\":\"$.pk\"},\"sk\":{\"S.$\":\"$.sk\"}},\"TableName\":\"",
            {
              "Ref": "PersistenceDDBTable"
            },
            "\",\"ExpressionAttributeNames\":{\"#status\":\"status\"},\"ExpressionAttributeValues\":{\":status\":{\"S\":\"pending\"}},\"ReturnValues\":\"ALL_NEW\",\"UpdateExpression\":\"SET #status = :status\"}},\"retry seconds\":{\"Type\":\"Wait\",\"SecondsPath\":\"$.retrySeconds\",\"Next\":\"SetStatusTo-in-progress\"},\"SetStatusTo-in-progress\":{\"Next\":\"DeliverTransactionTask\",\"Type\":\"Task\",\"ResultPath\":null,\"Resource\":\"arn:",
            {
              "Ref": "AWS::Partition"
            },
            ":states:::dynamodb:updateItem\",\"Parameters\":{\"Key\":{\"pk\":{\"S.$\":\"$.pk\"},\"sk\":{\"S.$\":\"$.sk\"}},\"TableName\":\"",
            {
              "Ref": "PersistenceDDBTable"
            },
            "\",\"ExpressionAttributeNames\":{\"#status\":\"status\"},\"ExpressionAttributeValues\":{\":status\":{\"S\":\"in-progress\"}},\"ReturnValues\":\"ALL_NEW\",\"UpdateExpression\":\"SET #status = :status\"}},\"DeliverTransactionTask\":{\"Next\":\"Delivery success?\",\"Retry\":[{\"ErrorEquals\":[\"States.ALL\"],\"MaxAttempts\":10}],\"Parameters\":{\"FunctionName\":\"",
            {
              "Ref": "DeliveryStepFunctionDeliverTransaction"
            },
            "\",\"Payload.$\":\"$\"},\"OutputPath\":\"$.Payload\",\"Type\":\"Task\",\"Resource\":\"arn:",
            {
              "Ref": "AWS::Partition"
            },
            ":states:::lambda:invoke\"},\"Delivery success?\":{\"Type\":\"Choice\",\"Choices\":[{\"Variable\":\"$.status\",\"StringEquals\":\"complete\",\"Next\":\"SetStatusTo-complete\"},{\"Variable\":\"$.status\",\"StringEquals\":\"failed\",\"Next\":\"SetStatusTo-failed\"}],\"Default\":\"SetStatusTo-pending\"},\"SetStatusTo-complete\":{\"End\":true,\"Type\":\"Task\",\"ResultPath\":null,\"Resource\":\"arn:",
            {
              "Ref": "AWS::Partition"
            },
            ":states:::dynamodb:updateItem\",\"Parameters\":{\"Key\":{\"pk\":{\"S.$\":\"$.pk\"},\"sk\":{\"S.$\":\"$.sk\"}},\"TableName\":\"",
            {
              "Ref": "PersistenceDDBTable"
            },
            "\",\"ExpressionAttributeNames\":{\"#status\":\"status\"},\"ExpressionAttributeValues\":{\":status\":{\"S\":\"complete\"}},\"ReturnValues\":\"ALL_NEW\",\"UpdateExpression\":\"SET #status = :status\"}},\"SetStatusTo-failed\":{\"End\":true,\"Type\":\"Task\",\"ResultPath\":null,\"Resource\":\"arn:",
            {
              "Ref": "AWS::Partition"
            },
            ":states:::dynamodb:updateItem\",\"Parameters\":{\"Key\":{\"pk\":{\"S.$\":\"$.pk\"},\"sk\":{\"S.$\":\"$.sk\"}},\"TableName\":\"",
            {
              "Ref": "PersistenceDDBTable"
            },
            "\",\"ExpressionAttributeNames\":{\"#status\":\"status\"},\"ExpressionAttributeValues\":{\":status\":{\"S\":\"failed\"}},\"ReturnValues\":\"ALL_NEW\",\"UpdateExpression\":\"SET #status = :status\"}}}}"
          ]
        ]
      }
    }
  }
}
```

然后是 AWS CDK(利用一些现有的结构来为我编辑 Amazon DynamoDB 记录)。

```
const STATUS = "$.status"
const RETRY_SECONDS = "$.retrySeconds"
const PENDING = "pending"
const PROGRESS = "in-progress"
const FAILED = "failed"
const COMPLETE = "complete"

const setPending = stepFunction.setStatus(this, props.table, PENDING);
const setProgress = stepFunction.setStatus(this, props.table, PROGRESS);
const setSuccess = stepFunction.setStatus(this, props.table, COMPLETE);
const setFailed = stepFunction.setStatus(this, props.table, FAILED);
const waitForNSeconds = this.waitTask("retry seconds", RETRY_SECONDS);

const definition = this.mapperTask()
  .next(setPending)
  .next(waitForNSeconds)
  .next(setProgress)
  .next(this.deliverTransactionTask())
  .next(
    new sfn.Choice(this, "Delivery success?")
      .when(sfn.Condition.stringEquals(STATUS, COMPLETE), setComplete)
      .when(sfn.Condition.stringEquals(STATUS, FAILED), setFailed)
      .otherwise(setPending)
  );
```

如果您必须阅读第二段代码才能理解第一段代码在做什么，我完全理解。当然，没有什么能阻止 CloudFormation 采用和支持更优雅的 DSL。事实上， [AWS SAM](https://aws.amazon.com/serverless/sam/) 正是在这方面的一次尝试，其重点是无服务器开发者体验。

鉴于当前 CDK 社区的发展势头和 AWS 不断增长的投资，我希望看到越来越多的团队从 CDK 开始，并愉快地继续将其作为基础设施管理的主要工具。

## AWS 上的 Terraform

Terraform 于 2014 年推出，目标是能够将基础设施编排为代码。它最初[的目标是 AWS](https://github.com/hashicorp/terraform/commit/d6d5a97ec9cd08658e015ca83b34da3795e199ad) ，但是已经发展到能够管理一个[大型模块生态系统。](https://registry.terraform.io)事实上，多提供商支持能力是该技术的主要卖点之一。

Terraform 推出了自己的 DSL，叫做 [Hashicorp 配置语言](https://github.com/hashicorp/hcl) (HCL)。从表面上看，它感觉像是一个更人性化的 JSON。如果你有受虐狂的一面，那么 Terraform 本身也支持 JSON。

* * *

**[获取 Terraform 备忘单](https://acloudguru.com/blog/engineering/the-ultimate-terraform-cheatsheet)**
*查看排名前十的 Terraform 命令，并在我们的 [Terraform 备忘单](https://acloudguru.com/blog/engineering/the-ultimate-terraform-cheatsheet)中获得您需要的所有基本命令的完整摘要。*

* * *

## 云的形成和地形有什么不同？

作为代码的 AWS 基础设施只是花哨的状态管理。Terraform 和 AWS CloudFormation 的最大区别在于它实际上是如何与基础设施本身进行交互的。有了 CloudFormation，你可以向它提供你的目标状态的表示，它将在你的基础设施上执行所有操作，让你在平台内自然地到达那里。同样，Terraform 采用您的目标状态的表示，[构造一个 API 调用计划](https://www.terraform.io/docs/commands/plan.html),直接调用您的 AWS 基础设施以达到该状态。

### 为什么选择 Terraform 而不是 CloudFormation？

在一个完美的世界里，这两种方法都完美无缺。但这是我们正在谈论的云。正如沃纳·威格尔喜欢提醒我们的那样，每件事都会失败。

直到最近，Terraform 在能够从进程外更新资源的人那里恢复方面还是很出色的。它能够解决不一致问题，并刷新基础架构的正确状态，即使有人“只是为了测试某些东西”而手动编辑了该安全组。AWS CloudFormation 在这些不一致的状态中挣扎，但是[漂移检测](https://aws.amazon.com/blogs/aws/new-cloudformation-drift-detection/https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/detect-drift-stack.html)的引入试图解决一些令人头痛的问题。

Terraform 还提供了一个更优雅的故事，即[导入](https://www.terraform.io/docs/import/index.html)非托管资源，或者来自其他栈的资源。CloudFormation 提供了这一功能，但仅针对支持漂移检测的资源子集。

除了这些好处，AWS 上的 Terraform 确实是“一次学习，利用大多数地方”的一个真正的选择。不管你对多云和混合云的感觉如何，对你自己或你的团队进行单一技术培训的吸引力是诱人的，这种技术可以从许多不同的可能目标的知识转移中受益。

## CDK 与云的形成和地形有什么不同？

为地形 (CDKTF)引入 [CDK 有效地允许开发者编写 CDK，在引擎盖下，目标是地形而不是云形成。这是我们在云世界中最接近拥有我们的蛋糕并吃掉它的方式，因为你可以想象一个 CDK 应用程序使用 CloudFormation 作为你的 AWS 嵌套堆栈目标，使用 Terraform 作为外部提供者堆栈目标。](https://www.terraform.io/cdktf)

## CDK vs 陆地 vs 云形成:哪个更好？

那么，应该选择哪种工具呢？鉴于存在大量的选择和业务需求，在一篇 1600 字的文章中强加一个放之四海而皆准的观点是不负责任的。相反，在考虑你的选择时，我会用一系列的问题来问你自己。

| 我是否在开发一个**简单的、几乎没有服务器的解决方案**并且具有最小的依赖性？ | 自动气象站云形成(特别是自动气象站 SAM)很有可能 |
| 我是否拥有最佳实践和流程编排的**自上而下的分布**？ | AWS CDK 或 Terraform |
| 我想完全留在 AWS 生态系统中吗？ | 自动气象站云形成或自动气象站 CDK |
| 我需要协调 AWS 生态系统之外的**资源吗？** | 地形或地形的 CDK(CDKTF) |
| 我是否想要一个**多提供商实用程序**，特别是针对多/混合云知识转移？ | 将（行星）地球化（以适合人类居住） |

Choosing the right IaC tool on AWS

唯一真正错误的答案是阻止你建造任何东西的答案。

IaC 空间正在增长，每个人都有自己的观点和事情应该如何工作。我认为竞争是健康的，在某些情况下，竞争迫使供应商自己提高了竞争力。以下是 IaC 领域中的一些其他可用工具。

| AWS Amplify CLI | 用于简化无服务器 web 和移动开发的 CLI 工具链。如果你主要是一个前端开发人员，或者只是想尽快上手，那就别再找了。Amplify CLI 和框架管理幕后的所有复杂性，帮助您构建和部署实时 web 和移动应用程序。 |
| [电池组](https://www.pulumi.com/) | 如果 Terraform 和 CDK 团队一起重新构思，我觉得它会有点像 Pulumi。 |
| [对流层](https://github.com/cloudtools/troposphere) | 对流层库允许通过编写 Python 代码来描述 AWS 资源，从而更容易地创建 [AWS CloudFormation JSON](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html) 。对流层还包括通过 Heat 对 [OpenStack 资源](http://docs.openstack.org/developer/heat/template_guide/openstack.html)的一些基本支持。 |
| 英格拉夫 | InGraph 是用于 AWS CloudFormation 的开源和声明性基础设施图形 DSL。关键特性是能够创建可组合的基础设施组件，同时保留 AWS CloudFormation 语言的严格语义。 |
| [无服务器框架](https://www.serverless.com/) | 零摩擦无服务器开发。轻松构建可在低成本的新一代云基础架构上自动扩展的应用。 |

[*Trek10*](https://trek10.com) *是专注于云原生和无服务器应用的 AWS 首要咨询合作伙伴。*