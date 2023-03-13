# 如何使用 Cosmos DB 和 Terraform 在 Azure 中部署简单的应用程序

> 原文：<https://acloudguru.com/blog/engineering/deploy-a-simple-application-in-azure-using-terraform>

Azure Cosmos DB 是一个全球分布式数据库服务。在开发全球分布式应用程序时，它为开发人员提供了很大的灵活性。多亏了 Terraform，您只需几行 HCL 代码就可以轻松部署 Cosmos DB 帐户和资源。

在这篇文章中，我将向你展示如何在 Azure 中部署一个简单的应用程序。我们将通过使用 Terraform 将 Azure Cosmos DB 部署到 Azure 容器实例来实现这一点。首先，我们将学习如何创建 Azure Cosmos DB 实例，然后更新配置以创建 Azure 容器实例，最后创建一个使用这两种资源的简单应用程序。

* * *

加速你的职业生涯！

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯

* * *

## ****你需要什么****

要跟进这篇文章，你需要一些东西:

*   Azure 订阅
*   要么在本地安装 [Terraform](https://learn.hashicorp.com/tutorials/terraform/install-cli) ，要么在 Azure 中使用内置 Terraform 的云外壳
*   如果您在本地使用 terraform，您还需要安装 [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli) 来向 Azure 认证 Terraform。
*   您选择的文本编辑器(我的建议是 [VS 代码](https://code.visualstudio.com))

## ****步骤 1:创建初始配置****

假设您已经具备了入门所需的一切，接下来要做的事情就是配置 Terraform 来使用 Azure provider 进行配置。您需要在您为项目创建的目录中创建一个名为 **main.tf.** 的文件。我创建了一个名为 **terraformguru** 的目录，这将是我这个项目的工作目录。

在 **main.tf** 文件中，您首先需要定义您将用于配置的提供者。

一旦我们定义了提供者，我们将需要在初始配置中定义三个资源。

*   第一个资源是我们的资源组，我们将把其他资源绑定到这个资源组。
*   我们将需要在下一个资源块中使用随机提供程序来生成一个随机整数，以便在 Azure Cosmos DB 帐户配置中使用。
*   然后我们可以定义我们的 Azure Cosmos DB 帐户。

您的配置应该如下例所示:

![](img/8132cf7d12531a50e3408808d0a22032.png)

在我们的 Azure Cosmos DB 帐户资源块中，我们需要定义这些参数:

*   **名称**(与随机整数组合成唯一名称)
*   **位置**(资源组位置)
*   **资源组名称**(资源组的名称)
*   **报价 _ 类型**
*   **种类**
*   **一致性 _ 策略**
*   **地理位置**

一旦我们定义了三个资源，就该应用我们的配置并创建我们的 Cosmos DB 实例了。

## **步骤 2:应用我们的配置**

第一步是初始化我们的工作目录，这样我们就可以为我们的项目下载所需的提供者插件。我们可以通过运行以下命令来实现这一点:

![](img/41027e552d4ff72dfab37deeb5057968.png)

接下来，我们将通过运行以下命令来验证我们的配置，以确保代码的语法是正确的:

![](img/c11cbe146224f91f886eab1b45e0fa9e.png)

一旦我们确认我们的配置是有效的，我们接下来可以通过运行 plan 命令来进行配置的模拟运行，如下例所示:

![](img/150f5e1e0dc5a7353dd209b53735a0a4.png)

如果一切正常，看起来会像我们希望的那样，我们就可以最终应用我们的配置了:

![](img/6f67b4c346485bddf87f0236335c65ab.png)

在应用运行之后，我们应该在 Azure 中有一个 Cosmos DB 的实例。现在我们可以更新我们的配置，这样我们就可以使用我们的新实例。

## **步骤 3:用容器实例更新配置**

现在是时候更新我们的配置并添加一个容器实例了。这个容器实例将使用我们的 Cosmos DB 实例，该实例本身使用一个运行小型投票 web 应用程序的容器映像。添加的配置应该类似于下面的示例:

![](img/b102bc270e2f0dceda77db5b33afa25e.png)

这里我们为容器实例添加了一个资源块。在我们的 Azure 容器组资源块中，我们需要定义这些参数:

*   **名称**
*   **位置**(资源组位置)
*   **资源组名称**(资源组的名称)
*   **ip 地址类型**
*   **域名标签**
*   **os_type**
*   **容器**(这是我们指定图像的地方)
*   **安全 _ 环境 _ 变量**

这里需要指出几个关键点。

*   首先，在我们的容器参数中，注意我们指定了一个从微软容器图像注册表中提取的图像。我们使用 Cosmos DB 后端的前端投票应用程序。
*   我们从创建的 Cosmos DB 实例中提取两个环境变量，并为每个变量设置一个环境变量。
    *   首先，我们为数据库提取端点并设置环境变量 **COSMOS_DB_ENDPOINT** ，然后我们提取数据库的主密钥并设置环境变量 **COSMOS_DB_MASTERKEY** 。这两个环境变量是数据库的关键，允许容器连接到数据库并使用数据库实例。没有它们，应用程序将无法工作。
    *   另请注意，我们正在设置一个输出变量，该变量将显示我们的应用程序端点，以便我们可以连接到应用程序。

一旦我们将它添加到我们的配置中，它应该看起来像这样:

![](img/22bc742f5f315e4088ca3a242b4fcfc6.png)

我们现在可以将我们的更改部署到我们的配置中。我们应该验证我们的配置，以确保代码的语法是正确的:

![](img/c11cbe146224f91f886eab1b45e0fa9e.png)

然后，我们将对配置进行一次预演:

![](img/150f5e1e0dc5a7353dd209b53735a0a4.png)

最后应用我们的配置:

![](img/6f67b4c346485bddf87f0236335c65ab.png)

在应用运行之后，我们应该会看到以下输出:

![](img/c8cce326ca6b02b2b1dc6471c10f2be6.png)

### **测试我们的应用**

现在我们的资源已经部署好了，我们有了显示在终端输出中的应用程序端点。

转到您的浏览器，使用输出中显示的地址导航到我们的应用程序。您应该看到以下内容:

![](img/7ab19e7c4286adfbe828663b2ffada4d.png)

现在，如果您选择其中一个选项，您应该会立即看到如下的投票结果:

![](img/66bbea14c7826549a39d3bcfb40b833b.png)

## 第四步:成功！

就是这样！您已经成功地使用 Terraform 和 Cosmos DB 在 Azure 中部署了一个简单的应用程序。正如你所看到的，这是快速而简单的，只需要几行 Terraform 代码。要了解更多，请查看我的课程[Advanced terra form with Azure](https://learn.acloud.guru/course/advanced-terraform-with-azure/dashboard)。保持令人敬畏的大师，学习所有的东西！下次见。

*想要跟上 Azure 的所有事物？* [*在 YouTube 上订阅一位云大师*](https://www.youtube.com/c/AcloudGuru) *，获取每周亚马逊新闻和 AWS 公告。你也可以像 ACG 上的*[](https://www.facebook.com/acloudguru)**一样，关注我们上的* [*推特*](https://twitter.com/acloudguru) *，或者加入* [*不和谐*](https://discord.com/invite/pluralsight) *的对话！**