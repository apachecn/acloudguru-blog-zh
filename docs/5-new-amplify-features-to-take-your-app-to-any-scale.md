# 5 项新的增强功能，可将您的应用扩展到任何规模|云专家

> 原文：<https://acloudguru.com/blog/engineering/5-new-amplify-features-to-take-your-app-to-any-scale>

就在 re:Invent 2021 之前，AWS 为 Amplify 推出了一系列功能，既简化又增强了客户构建应用程序的方式，同时还实现了原型制作和部署到生产中。在这篇文章中，Michael Liendo(AWS Amplify 的高级开发人员)谈到了其中的五个特性，以便更好地理解它们的用例以及如何开始！

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## 什么是 AWS Amplify？

AWS Amplify 是一套工具，面向希望在 AWS 上创建全栈应用的前端开发人员。使用它的 CLI，客户可以使用终端提示来自动编写他们的应用程序的后端。

Amplify 库和[预建组件](https://ui.docs.amplify.aws/)允许无缝的前端到后端解决方案，只需点击几下鼠标，应用程序就可以托管在 [Amplify 主机](https://aws.amazon.com/amplify/hosting/)上。

最后，客户可以在我们的[管理 UI](https://sandbox.amplifyapp.com/getting-started) 中构思他们的数据模型，甚至不需要 AWS 帐户。

最棒的是，这套产品可以相互集成，这样它们就可以作为一个整体使用，或者作为一个单独的产品使用，这取决于您团队的需求。

这里有五个新的 Amplify 功能，可以帮助您将应用扩展到任何规模。

## 1.覆盖放大生成的资源

许多客户喜欢 Amplify 在添加资源时生成默认配置，如 Cognito 用户或身份池，或 S3 桶。但是，我们知道组织可能有不同的法规遵从性和治理标准。出于这个原因，[我们在 CLI 中引入了一个新命令](https://docs.amplify.aws/cli/auth/override/):`amplify override <category>`。

这将接受指定的类别并创建一个 TypeScript 文件，然后可以根据您的需要访问和重新配置该文件中的资源。我们从客户那里听到的常见场景包括在 AWS DynamoDB 表项目上启用 TTL，以及将现有函数设置为触发器，以将 Amazon Cognito 用户从一个用户池迁移到另一个用户池。

在用户键入`amplify override storage`的情况下，用几行就可以启用 bucket 版本控制。

```
import { AmplifyS3ResourceTemplate } from '@aws-amplify/cli-extensibility-helper'

export function override(resources: AmplifyS3ResourceTemplate) {
    resources.s3Bucket.versioningConfiguration = {
        status: 'Enabled',
    }
}
```

值得指出的是，上面代码片段中看到的新的`@aws-amplify/cli-extensibility-helper`模块是自动安装的，正确的导入语句是由 CLI 自动处理的。

## 2.使用 AWS CDK 添加自定义资源

开箱即用，Amplify 支持添加 AWS 服务，如 AppSync、Lambda、S3、Cognito、Fargate、API Gateway、[亚马逊位置地图](https://docs.amplify.aws/cli/geo/maps/)等，全部通过其 CLI。然而，客户通常希望根据他们正在构建的应用程序以及构建应用程序的需求来添加其他服务。

幸运的是，我们没有将所有 175 个以上的服务添加到我们的 CLI 中，而是[引入了一个新命令](https://docs.amplify.aws/cli/custom/cdk/) : `amplify add custom`

此命令支持通过 AWS CDK(类型脚本)和 AWS CloudFormation 创建的资源。

现在，Amplify 生态系统的简单性和 AWS 生态系统的庞大性在一个项目中结合在一起。

下面的代码片段展示了如何创建一个包含项目名称和 Amplify 环境名称的 SNS 主题。

```
import * as cdk from '@aws-cdk/core';
import * as AmplifyHelpers from '@aws-amplify/cli-extensibility-helper';
import * as sns from '@aws-cdk/aws-sns';
import * as subs from '@aws-cdk/aws-sns-subscriptions';

export class cdkStack extends cdk.Stack {
  constructor(scope: cdk.Construct, id: string, props?: cdk.StackProps, amplifyResourceProps?: AmplifyHelpers.AmplifyResourceProps) {
    super(scope, id, props);

    /* Do not remove - Amplify CLI automatically injects the current deployment environment in this input parameter */
    new cdk.CfnParameter(this, 'env', {
      type: 'String',
      description: 'Current Amplify CLI env name',
    });

    const projectName = AmplifyHelpers.getProjectInfo().projectName;

    const topic = new sns.Topic(this, 'sns-topic', {
      topicName: `sns-topic-${projectName}-${cdk.Fn.ref('env')}`
    });

    topic.addSubscription(new subs.EmailSubscription("<your-email-address>"));
  }
}
```

> Pro 提示:将 Lambda 的定制资源与定制 IAM 策略结合起来！

## 3.对定制 IAM 策略的 Lambda 和容器支持

Amplify 本身支持 Lambda 函数和 Fargate 容器的创建。通常，客户需要整合在 Amplify 生态系统之外创建的现有资源。出于这个原因，现在每当创建一个 Lambda 或容器时，我们都会生成一个`custom-policies.json`文件:

`[`


`{``"Action"``:`` ``[``"iam:GetPolicy"``]``,``"Resource"``:`` ``[``"arn:aws:iam:::policy/*"``]``}`


这个简单的文件接受一组策略，并自动将它们应用于相应函数或容器的执行角色。

值得指出的是，虽然默认情况下`Effect`是`allow`，但是策略也可以设置为`deny`。此外，请注意，在当前的 Amplify 环境中也支持和添加通配符，这对于[多环境场景](https://docs.amplify.aws/cli/teams/overview/)非常方便。

## 4.自定义命令挂钩

无论是确保使用特定版本的 Amplify CLI，还是希望在构建成功或失败时向您的团队发送 slack 通知，[自定义命令挂钩](https://docs.amplify.aws/cli/project/command-hooks/)都是解决方案。

当初始化一个新的 Amplify 项目时，我们现在生成一个`amplify/hooks`目录。在这个目录中，文件名采用“什么时候”的方式。例如，一个名为`pre-push.js`的文件将在一个项目被推送到 AWS 之前运行。此外，在使用`amplify add function`命令成功地将一个函数添加到一个项目中之后，一个名为`post-add-function.js`的文件将会运行。

回顾一下想要实施特定版本的 Amplify 的用例，这样做的代码如下所示:

```
const fs = require('fs');
const parameters = JSON.parse(fs.readFileSync(0, { encoding: 'utf8' }));

// Get the running Amplify CLI major version number
const currentCLIMajorVersion = parameters.data.amplify.version.split('.')[0]
console.log('Amplify CLI major version: ', currentCLIMajorVersion)

const MINIMUM_MAJOR_AMPLIFY_CLI_VERSION = 5
console.log('Minimum required Amplify CLI major version: ', MINIMUM_MAJOR_AMPLIFY_CLI_VERSION)

if (currentCLIMajorVersion < MINIMUM_MAJOR_AMPLIFY_CLI_VERSION) {
  // Non-zero exit code will stop the Amplify CLI command's execution
  console.log('Minimum CLI version requirement not met.')
  process.exit(1) 
} else {
  console.log('Minimum CLI version requirement met.')
  process.exit(0) 
}
```

值得注意的是，除了 JavaScript，build hooks 默认情况下也支持 shell 脚本，也可以启用像 python 这样的[自定义脚本运行时](https://docs.amplify.aws/cli/project/command-hooks/#adding-a-custom-scripting-runtime)！

## 5.将放大器后端导出为 CDK 堆栈

我们单子上的最后一项！

这个特性允许最大的灵活性，但是我要补充的是，它是高级的，是为特定的客户设计的。因此，虽然大多数客户永远不会需要这种能力，但它进一步加强了 Amplify 可用于生产应用的地位。

`amplify export`

通过运行此命令，Amplify CLI 会将您的整个 Amplify 后端导出为 CDK 堆栈。然后可以将其引入现有的 CDK 管道，并与您的其余基础设施一起部署。

注意，这是*而不是*弹出放大器。当一个放大项目被迭代时，此命令可以运行多次。

导出 Amplify 项目很简单，不过让我们通过一个示例阶段来看看将生成的堆栈集成到现有管道中是什么样子:

```
import { CfnOutput, cfnTagToCloudFormation, Construct, Stage, StageProps } from '@aws-cdk/core';
import { AmplifyExportedBackend } from '@aws-amplify/cdk-exported-backend';
import * as path from 'path'
import * as cdk from '@aws-cdk/core'

export class AmplifyStage extends Stage {

  constructor(scope: Construct, id: string, props?: StageProps) {
    super(scope, id, props);

    // ADD AMPLIFY EXPORTED BACKEND STACK HERE
    const amplifyStack = new AmplifyExportedBackend(this, "amplifyexportedbackend", {
      path: path.resolve(__dirname, '..', 'amplify-export-mytodoapp'),
      amplifyEnvironment: "dev"
    })
  }
}
```

如果 CDK 开发人员以前部署过管道，他们应该对此很熟悉。注意，`@aws-amplify/cdk-exported-backend`包处理必要的绑定。

更多详情可在[文档页面](https://docs.amplify.aws/cli/usage/export-to-cdk/#use-an-exported-amplify-backend-in-aws-cloud-development-kit-cdk)上找到。

* * *

## 结论

在这篇文章中，我们看到了新发布的特性，这些特性使得 Amplify 应用程序更具可扩展性。这是除此之外的功能，例如能够[将现有资源](https://docs.amplify.aws/cli/storage/import/)导入您的 Amplify 项目。

现在，客户不仅可以通过定制构建挂钩等功能进行更细粒度的控制，而且覆盖和添加资源的能力意味着在 AWS 控制台上花费更少的时间，将更多的时间专注于构建您的产品。

更多关于 AWS Amplify [的信息，请访问我们的文档页面](https://docs.amplify.aws/)，并与我保持同步，您可以[在 Twitter 上关注我](https://twitter.com/mtliendo)。

### 关于作者

Michael Liendo 是@ AWS Amplify 的高级开发者拥护者。你可以在 Twitter 上关注他。

* * *

*通过在* [*上追随一位云宗师【推特】*](https://twitter.com/acloudguru)*[*【脸书】*](https://www.facebook.com/acloudguru)*[*上订阅一位云宗师*](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1) *进行每周更新，并在* [*上加入对话*](http://discord.gg/acloudguru) *。您也可以查看我们本期的* [*免费课程*](https://acloudguru.com/blog/news/whats-free-at-acg) *！***