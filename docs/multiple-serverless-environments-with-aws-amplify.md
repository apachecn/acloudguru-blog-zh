# AWS 放大和多个无服务器环境|云专家

> 原文：<https://acloudguru.com/blog/engineering/multiple-serverless-environments-with-aws-amplify>

## 团队的生产工作流程

自从 8 月份发布了 [AWS Amplify](https://acloudguru.com/blog/engineering/create-a-serverless-python-api-with-aws-amplify-and-flask) CLI 以来，最受欢迎的功能之一就是处理多团队&多环境的能力。

在最新发布的 AWS Amplify 工具链中，当使用 AWS Amplify 开发应用程序时，现在有了处理多种环境和团队的一流支持。

### 放大控制台

最近另一个大的发布是 [Amplify 控制台，这是一个为移动网络应用提供的持续交付和托管服务](https://acloudguru.com/blog/engineering/how-to-deploy-a-custom-domain-with-the-amplify-console)。Amplify 控制台与我们在本帖&中将要讨论的多环境功能密切相关，我们将学习如何在团队的集中工作流程中利用多个 Amplify AWS 环境。

> Amplify 控制台还具有持续部署、轻松定制域+免费 HTTPS、多环境支持功能分支部署、&允许您在单个部署工作流程中管理前端&无服务器后端等功能。
> 
> 要了解更多关于 Amplify 控制台的信息，请点击[这里](https://aws.amazon.com/amplify/console/)。

### 测试它

使用以下命令安装 Amplify CLI :

```
npm install -g @aws-amplify/cli
```

*如果这是您第一次使用 AWS Amplify CLI，请查看* [*这段*](https://www.youtube.com/watch?v=fWbM5DLh25U) *视频，了解安装后如何配置它。*

## 使用新的 AWS 环境功能

CLI 中现在有了一个新命令，即 **env** 命令:

```
amplify env
```

运行此命令时，您将获得一个在 AWS 环境中工作的可用选项列表:

*   **同步—** 将您的环境与当前云环境同步。这将允许您下载您已经在其中工作的环境的较新版本
*   **检出** **<环境名>** —将您的环境移动到命令中指定的环境
*   **列表** —显示您的 Amplify 项目中所有环境的列表
*   **get** —显示命令中指定的环境的详细信息
*   **添加** —将一个已经存在的 Amplify 项目堆栈添加到您的本地后端
*   **移除** —从 Amplify 项目中移除一个环境

要在现有的 AWS Amplify 项目中创建一个新的 AWS 环境，您可以运行`amplify init`命令&您现在可以选择在当前工作项目中初始化一个新的环境。

#### 接下来，让我们学习如何在两种不同的场景中使用多个 AWS 环境:

1.  **使用多个本地放大环境**
2.  **在集中式工作流程中使用 Amplify 控制台与多个 Amplify 环境合作/与团队合作**

## 处理多个本地放大环境

让我们先来看看如何创建和管理多个本地放大器环境。

在这个例子中，我们将看到如何添加和测试新功能，而不影响我们原来的/主要的放大器项目。当新特性准备好了，我们将把它合并到我们的主放大环境中&删除特性环境。

我们将使用以下工作流程来演示这一点:

1.  创建一个新的放大项目。主放大器环境将被称为**开发**。
2.  向主环境添加新功能(身份验证)
3.  推动主 Amplify 环境在我们的 AWS 客户中创建认证服务
4.  创建新的放大环境，以创建和测试新功能。在这个新环境中，我们将添加并测试一个 [AWS AppSync GraphQL API](https://acloudguru.com/blog/engineering/8-steps-to-building-your-own-serverless-graphql-api-using-aws-amplify) 。这个新的放大环境将被称为**蜂房**。
5.  一旦我们测试了这个新特性并知道它按照我们想要的方式工作，我们就会将它合并到我们现有的 **dev** 环境中。

为了以与框架无关的方式演示这个工作流，我们将在一个空目录中创建一个新的 Amplify 项目&遍历上面的所有步骤。

### 初始化一个新的放大项目

```
mkdir blanktest
cd blanktest
amplify init
```

> 出现提示时，将环境命名为**dev**T2 】,出于本演示的目的，您可以随意选择所有其他选项的默认值。

接下来，在新环境中，使用以下命令添加身份验证服务:

```
amplify add auth
```

> 出现提示时，如果您想使用默认的身份验证和安全配置，请选择“是”。

现在，我们将通过运行 push 命令在我们的帐户中创建服务:

```
amplify push
```

*   您确定要继续吗？ **Y**

既然我们已经成功地将身份验证服务添加到我们的开发环境中，那么让我们看看如何创建一个新的特性-api 环境来创建和测试 AWS AppSync GraphQL API。

### 创造新的放大环境

为了创建新环境，我们将使用`init`命令:

```
amplify env add
```

*   您想使用现有环境吗？普通
*   输入环境的名称:apifeature

现在，新环境已经创建。如果我们想要查看所有当前环境，我们可以运行以下命令来列出它们:

```
amplify env list
| Environments |
| ------------ |
| dev          |
| *apifeature  |
```

> 我们当前使用的环境现在应该显示在列表中，旁边有一个星号。

现在我们已经初始化了新环境，我们需要在我们的帐户中创建应用程序堆栈，这样我们就可以开始测试了。为此，请运行 push 命令:

```
amplify push
```

现在我们已经创建了一个新环境，我们将添加新功能:

```
amplify add api
```

> 当提示输入 API 的类型时，选择 GraphQL &为这个演示的其余选项选择缺省值。

完成上述步骤后，我们将运行 amplify push 在我们的帐户中创建 GraphQL API:

```
amplify push
```

*   您确定要继续吗？ **Y**
*   是否要为新创建的 GraphQL API 生成代码？ **N**

成功创建服务后，我们可以运行 status 命令来查看项目的当前状态:

```
amplify status
Current Environment: apifeature
| Category | Resource name | Operation | Provider plugin   |
| -------- | ------------- | --------- | ----------------- |
| Auth     | cognitoauth   | No Change | awscloudformation |
| Api      | blanktest     | No Change | awscloudformation |
```

> 如果我们访问 [AWS AppSync 控制台](https://console.aws.amazon.com/appsync/home)，我们现在应该看到添加了**API feature**(blank test-API feature)的新 AWS AppSync API。

### 将新特性合并到开发环境中

现在，我们如何将这个新功能引入到我们原来的开发环境中呢？这很简单。我们需要检查原始的开发环境&我们现在将看到这个特性的副本，以及已经为我们设置的所有配置。

```
amplify env checkout dev
amplify status
Current Environment: dev
| Category | Resource name | Operation | Provider plugin   |
| -------- | ------------- | --------- | ----------------- |
| Api      | blanktest     | Create    | awscloudformation |
| Auth     | cognitoauth   | No Change | awscloudformation |
```

我们现在在项目中看到了 API 类别。我们还看到 API 对应的操作目前是**创建**。这意味着虽然 AppSync API 的配置已经准备就绪，但是实际的服务还没有在我们的帐户中创建。为此，我们需要运行`push`:

```
amplify push
```

现在，新的 AppSync GraphQL API 已经创建好了&它现在应该会出现在我们的[仪表板](https://console.aws.amazon.com/appsync/home)中。

要快速演示此工作流程，请观看以下视频:

删除 AWS 环境

既然我们已经成功地将我们的特性合并到我们的主环境中，我们如何清理我们在测试环境中创建的资源呢？这很简单，我们只需运行以下命令:

### 您还想从云中删除环境的所有资源吗？ **Y**

remove 命令将为您删除该环境中的所有内容(IAM 角色、Cognito 服务、AWS AppSync API 和 DynamoDB 表)。

```
amplify env remove apifeature
```

*   **多重放大团队环境**

既然我们知道了如何在本地管理多个环境，那么我们如何在面向 git 的工作流中管理多个环境&与团队一起？

## 在团队中处理 Amplify 项目有两种主要方式:

团队成员在他们自己的沙盒环境中工作(推荐)

### 团队成员共享同一个开发后端来工作

1.  我们要看的例子(1)是团队成员如何在他们自己的沙盒环境中工作，然后将更改合并到开发环境中以测试一些更改，然后在测试完成后进行控制。
2.  首先，我们希望有两个独立的 git 分支:master 和 dev。我们还希望有两个独立的放大器环境，与这些环境相对应。

设置主环境和开发环境

要设置主环境和开发环境，我们将继续并初始化它们:

## 一旦我们在 Git 中设置了“主”分支，我们将在您的 Amplify 项目中设置一个“开发”环境(这将基于您的“主”环境):

这将为云中的项目设置另一个环境。后端配置和资源现在是从“主”环境克隆的。运行`amplify push`为您的新环境(dev)提供所有 AWS 资源。

```
$ amplify env add
? Enter a name for the environment master
// Provide AWS Profile info
// Add amplify categories using `amplify add <category>`
$ git init
$ git add <all project related files>
$ git commit -m <commit-message>
$ git remote add origin git@github.com:<repo-name>
$ git push origin master
```

现在将更改推送到“主”分支(*)当运行`git status`命令时，您将只看到对 team-provider-info.json 文件*的更改。这个文件包含了所有项目环境的累积堆栈信息，当您想要在一个团队中共享相同的后端时，这些信息非常有用。在这之后，让我们创建一个新的 git 分支——与我们刚刚创建的新环境相对应的“dev”。

```
$ amplify init
? Do you want to use an existing environment? No
? Enter a name for the environment dev
// Provide AWS Profile info
```

在团队中共享项目

现在，我们在云中有了两个独立的环境(master & dev ),并且在 git 上有了相应的 Git 分支和我们的 amplify 后端基础设施代码。

```
$ git add .
$ git commit -m "creating master amplify environment"
$ git push origin master
$ git checkout -b dev
$ git push origin dev
```

## 假设一个团队成员想要在同一个 Amplify 项目上工作，向它添加一些特性，然后将更改推送到开发环境来测试一些更改。他们将执行以下步骤:

接下来，假设团队成员想要将这些变更转移到开发和主环境/分支:

在测试了开发阶段的一切工作正常之后，您现在可以将开发合并到主 git 分支:

```
$ git clone <git-repo>
$ cd <project-dir>
$ git checkout -b mysandbox
$ amplify init
? Do you want to use an existing environment? No
? Enter a name for the environment mysandbox
// Rest of init steps
// Add/update any backend configurations using amplify add/update <category>
$ amplify push
$ git push -u origin mysandbox
```

其他工作流程

```
$ git checkout dev
$ amplify init
? Do you want to use an existing environment? true
? Choose the environment you would like to use: 
❯ dev 
 master
$ git merge mysandbox
$ amplify push
$ git push -u origin dev
```

还有其他工作流，包括允许团队成员共享同一个开发后端&甚至共享团队之外的项目。

```
$ git checkout master
$ amplify init
? Do you want to use an existing environment? true
? Choose the environment you would like to use: 
 dev 
❯ master
$ git merge dev
$ amplify push
$ git push -u origin master
```

### 要了解有关这些其他工作流的更多信息，请查看此处列出的[文档。](https://aws-amplify.github.io/docs/cli/multienv#setting-up-master-and-dev-environments)

结论

在 Amplify CLI 发布之后，最受欢迎的特性之一是能够创建多个 AWS 环境并与团队共享，因此我对这个新版本感到非常兴奋。

## AWS Amplify CLI 和客户端库都是开源的&我们鼓励讨论、问题、拉请求和功能请求。如果你有兴趣参与这个项目，请点击这里查看回复。

要了解更多关于 AWS Amplify 的信息，请点击此处查看文档。

获得更好职业所需的技能。

掌握现代技术技能，获得认证，提升您的职业生涯。无论您是新手还是经验丰富的专业人士，您都可以通过实践来学习，并在 ACG 的帮助下推进您的云计算职业生涯。

* * *

## Get the skills you need for a better career.

Master modern tech skills, get certified, and level up your career. Whether you’re starting out or a seasoned pro, you can learn by doing and advance your career in cloud with ACG.

* * *