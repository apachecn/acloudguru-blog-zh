# 放大管理用户界面:开发人员的 10 个激动人心的特性

> 原文：<https://acloudguru.com/blog/engineering/10-exciting-features-of-the-new-amplify-admin-ui>

本周 AWS 发布了一个主要的新功能——[Amplify Admin UI](http://docs.amplify.aws/console/adminui/start)**。**Amplify Admin UI 为开发人员提供了一个可视化界面，用于创建、更新和删除他们的 Amplify 云后端，为他们的数据建模，以及改善 Amplify 项目内部的协作等。你可以在[放大器控制台](https://console.aws.amazon.com/amplify/home)或者通过[创建一个新的沙箱](https://sandbox.amplifyapp.com/)来尝试。

以下是我在发布会上最喜欢的 10 个功能。

### **可视化定义您的数据模型**

我最喜欢的，也可能是最强大的特性，是可视化定义数据模型的能力。使用新的可视化编辑器，您不仅可以创建和部署您的数据模型，还可以对模型之间的关系(一对多、多对一和多对多)进行建模，以及为细粒度的访问控制定义安全设置和授权规则。

一旦部署了数据模型，就可以更新和部署对数据模型的更改。UI 还为您提供了如何在所有支持的前端(JavaScript、iOS、Android 和 Flutter)上本地下拉和运行新后端的逐步说明。

### **在没有 AWS 帐户的情况下，在管理 UI 和 CLI 中配置您的后端**

只有 Amplify Console 的第一个后端部署需要 AWS 帐户。之后，您可以通过电子邮件邀请团队成员使用 [AWS Admin](https://acloudguru.com/course/intro-to-azure-for-aws-admins) UI 和 Amplify 命令行界面(CLI)。所有具有完全访问权限的管理 UI 用户都可以在没有 AWS 帐户的情况下使用 Amplify CLI。

![](img/73493834cc33b997616beef1cb917603.png)

* * *

*对构建更多命令行界面感兴趣？查看我们关于 [Python Click](https://acloudguru.com/hands-on-labs/servercheck-building-a-python-cli-with-click) 的动手实验，并学习使用 Click(命令行界面创建工具包)创建 Python CLI！*

* * *

### **简单易懂的授权规则**

一旦创建了数据模型，就可以定义授权规则并配置细粒度的访问控制。您可以配置 API 访问的主要类型(公共、私有等..)以及每个模型的访问设置(创建、读取、更新、删除)。

使用这些规则，您可以为许多类型的常见应用程序建模常见的授权场景和用例，并直接从仪表板部署更改。

使用这些规则，很容易实现许多类型的应用程序所需的通用授权配置。

![](img/35d1d93d10f25f16fd3ab7b3954ee9ea.png)

### **内容管理**

部署您的数据模型后，所有应用程序数据都可以在管理 UI 的内容管理视图中看到，使应用程序管理员能够管理内容(例如，更新产品价格或添加新的博客文章)。

您可以使用基本的数据类型(字符串、整数、布尔值等)..)以及使用内置的富文本编辑器编辑网站和博客内容的富文本。

![](img/428fa5723149c58490b7cbe3e6c9b469.png)

### **按照代码部署基础设施**

Admin UI 使用 AWS CloudFormation 和嵌套堆栈来部署后端资源。这些 CloudFormation 堆栈允许您将后端基础设施定义保存为代码。可以使用 Amplify CLI 本地提取所有堆栈定义。管理 UI 和 Amplify CLI 协同工作。通过运行 amplify pull 命令，可以在 CLI 中实现在管理 UI 中所做的更改。类似地，对数据模型或 auth 的 CLI 更改将在 Admin UI 中可见。

### **使用 Amplify CLI 和 Amplify Hosting**

使用 Admin UI 启用的后端服务的配置可以使用 Amplify CLI 下拉到您的本地项目中。然后可以使用 CLI 或 Admin UI(或两者)迭代和更新项目。

还有一个新的非基于节点的 CLI，使许多尚未使用或不熟悉 Node.js 的开发人员更容易上手和运行。

可以使用以下命令安装新的 CLI:

```
curl -sL https://aws-amplify.github.io/amplify-cli/install | bash && $SHELL
```

部署后端后，您可以使用任何前端 web 项目设置托管和全栈 CI & CD，方法是使用 Git repo 或使用 Amplify CLI 在本地连接它们。

### **从 Amplify 控制台克隆和删除环境**

创建环境后，您可以将整个基础架构克隆到新环境中。这对于测试新特性或增强功能非常有用。

然后，如果您想将任何更改合并到另一个环境中，可以使用 Amplify CLI 在本地下拉这些环境。

![](img/0ea6b422ac992a5988e2897821b14f09.png)

### **在部署到云之前用沙盒构建应用**

使用[沙箱](https://sandbox.amplifyapp.com/)，您可以在部署到云之前创建、测试、共享和协作数据模型。一旦你创建了一个沙箱，你就可以通过一个公开的 URL 与任何人分享，无论他是否有 AWS 账户。

如果你认为其他人会发现应用程序的想法有用，你也可以为你想要公开分享的数据模型创建模板。您可以从头开始创建数据模型，也可以从 Amplify 提供的一个示例模式中创建数据模型。

![](img/3fc7fb42974d16b65d996d9ebb8ef029.png)

### **设置认证，管理用户和群组**

您可以设置和部署身份验证(由 Amazon Cognito 提供支持)，定义登录方法，以及配置和定义注册属性。

部署后，您可以创建用户和组，将用户添加到组中，查看登录活动，并在您的数据模型上定义授权规则。

![](img/abc1aa1eb459d282f5398ff248dad8a7.png)

### **具有友好重定向的自定义域**

如果您的应用程序设置为使用 [Amplify 控制台的网络托管功能，](https://acloudguru.com/blog/engineering/how-to-deploy-a-custom-domain-with-the-amplify-console)您可以使用您为应用程序前端设置的自定义域访问应用程序的管理用户界面。

例如，如果你在 https://exampledomain.com 托管你的应用程序，你可以设置一个友好的重定向到应用程序的管理用户界面的域名地址，如[https://exampledomain.com/amplify/adminui](https://exampledomain.com/amplify/adminui)。

Nader Dabit 是 web 和移动开发人员、作家，也是 AWS 的高级开发人员倡导者，专门从事全栈云开发。