# 利用 AWS 代码管道实现 CI/CD 自动化

> 原文：<https://acloudguru.com/blog/engineering/automating-ci-cd-with-aws-codepipeline>

谁不喜欢一个 [CI/CD 管道](https://acloudguru.com/course/implementing-a-full-ci-cd-pipeline)？尤其是当你在 AWS 上争论基础设施的时候。我们今天的问题是:我们能使用 AWS 自己的代码管道服务来管理 AWS 基础设施的频繁部署吗？

嗯，首先……你知道什么是持续集成和持续部署管道*吗*？如果你有，那太好了。跳过下面斜体部分。如果没有，继续读下去。

持续集成和持续部署(CI/CD)管道用于自动化软件交付步骤，包括构建、测试和部署阶段。是的，这是一个安全的空间。尽情跳你的快乐之舞，不要害怕评判。

持续集成(CI)阶段包括构建和测试阶段。CI 确保构建的变更工件也可以安全部署。现在是一个很好的时机来说明，如果部署阶段是**而不是**完全自动化，那么 CD 也可能意味着持续交付。在本教程中，CD 意味着持续部署，因此所有的更改都被部署到生产环境中。紧张？尝试在生产环境之前部署到临时环境。

好了，开始了。在这篇博文中，我将带您浏览我为[云简历挑战](https://cloudresumechallenge.dev)创建 CI/CD 管道时采取的步骤。这是我的 [GitHub 知识库，用于云简历挑战赛的后端资源](https://github.com/bmitchell21/backend-resources)。如果你只是想跟着这个例子走，这里是我的 [GitHub 库为这个教程](https://github.com/bmitchell21/acg-pipeline-test)。

第一步是拥有一个 AWS 账户。它是免费创建的，在最初的 12 个月里，你可以免费访问许多资源！(阅读有关 [AWS 自由层](https://aws.amazon.com/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc)的更多信息。)

您拥有 AWS 帐户。你在滚动。让我们开始…有趣的部分。在 AWS 控制台中，导航到代码管道。选择**创建管道**。在创建管道的这一点上，我感到很有信心。这是我最后一步。*我想，这大约需要一个小时*。是啊，没错。更像是五天(我真的*投入了时间)。我不想让其他人花那么长时间。这篇文章只是为了帮助读者更快地完成这个过程。还给你，教程。*

1.  选择管道名称并创建新的服务角色。请记住，稍后可能需要编辑服务角色。(说真的。记住这个。许可对我来说是一个很大的障碍)。

![](img/aa7620e88cfd41433fe43a530a4e82d8.png)

**下一个**。配置源阶段。我使用了 AWS CodeCommit，它需要 CodeCommit 中的存储库。在创建 CodeCommit 存储库之前，我们有两个步骤要完成。

2.  我们需要一个 S3 水桶。S3 桶是用来存放文物的。我使用 AWS CLI 创建了一个 bucket。请参见下面的命令。

![](img/a9e312e50de4b465c4499806c05ba40a.png)

3.  创建云信息角色。在这个例子中，我创建了一个角色，将 **CloudFormation** 作为可信实体，并授予了 **AWSLambdaExecute** 权限。然后，我使用 JSON 选项卡将如下所示的内联策略附加到角色上。根据您的 SAM 应用程序，您可能需要不同的权限。

![](img/15d754280a486a1663bda3185c61b51c.png)

让我们建立我们的 CodeCommit 存储库。

4.  在 AWS 控制台的新选项卡中打开 CodeCommit。
5.  创建一个存储库来保存您的工件。
6.  [将存储库克隆到您的本地机器](https://docs.aws.amazon.com/codecommit/latest/userguide/getting-started.html)。

![](img/c0e1bdbafe06a9a9cebacbe80a7ebe33.png)

7.  将所有需要的文件上传到本地文件夹，然后将它们推送到存储库。我的存储库包括一个 [AWS SAM](https://aws.amazon.com/serverless/sam/) 应用程序所需的文件。

![](img/482bf1d9e084090d0cd11664d809af31.png)

8.  回到 AWS 控制台中的 CodePipeline，配置源阶段设置。这建立了我们的源代码控制服务(CodeCommit ),作为我们部署管道的第一步。

![](img/b05ea933339f9eea25415574c2a4aea5.png)

9.  创建构建阶段。这是我们打包应用程序进行部署的地方。

![](img/49aa413d5e5042bc725cd4984a35812a.png)

**下一个**。我们必须创建一个项目。

10.  选择**创建项目**并选择一个项目名称。我的下一步如下所示。

![](img/e8fda8c3e87dbaf15f9e0f195245be09.png)![](img/13d34227e2f394e0e77daa0bc4066542.png)

11.  记下**角色名**。管道在首次部署后将会失败，因为角色需要更新。

**下一个**。是时候配置部署阶段了。我们很接近了。我保证。

12.  我在部署阶段使用了可爱的云形。请记住，AWS SAM 只是 CloudFormation 的超集，因此您可以通过 CodePipeline 原生部署 SAM 应用程序！这只是与 AWS 服务深度集成的一个很酷的优势。

![](img/260c91ae483cb8697b9ec486c20f9d06.png)![](img/1a156ed0771bbeac71c6284b5cde66f2.png)

13.  使用之前为部署阶段的角色创建的 CloudFormation 角色。

**下一个**。查看管线并创建管线。

请记住，更改将会失败，因为需要额外的权限。

14.  将 **AmazonS3FullAccess** 策略附加到我们之前创建的管道角色。
15.  请重试部署。

现在，这三个阶段都应该显示成功。现在我们需要做的就是添加一个执行变更阶段。就是这样！至少对管道来说是这样。

16.  编辑管道，然后编辑**部署阶段**。
17.  在**底部**选择**添加动作组**。

![](img/bdfa848038f774ebf28e871dba04dec1.png)

18.  选择**完成**。然后**救**。然后**发布变化**。

![](img/95a06a00d4aefa09fbc0be7d84103ba5.png)

19.  现在我们想要自动化 API 测试。下载[邮差](https://www.postman.com/)和[纽曼](https://support.getpostman.com/hc/en-us/articles/115003703325-How-do-I-install-Newman-)。你可能想知道这个过程是否会结束。(剧透:确实如此)
20.  复制 API url 并粘贴到 Postman 中。点击 **+** 打开下面页面的空白版本。

![](img/fba9e62140a62663ae5ce4cf9efdc8e0.png)

21.  包括您需要的特定测试。使用右边的片段来帮助。
22.  按下**保存**。单击 collections，将集合导出到保存 SAM 应用程序的其他文件的同一位置。

![](img/a39a1b1ae2bbb51b43e383e72ed04a04.png)

23.  更新 buildspec.yml 文件，然后在终端内部运行 newman 命令以确保它能够工作。

![](img/3ecbefd0678bc6aab27f3f099fc28194.png)

![](img/a741afee8743d4890582462c329c5f2c.png) ![](img/9bc266325415f23e91a9aedb21506fb4.png)

24.  将文件推送到 CodeCommit 存储库。然后，您可以查看代码构建日志，以了解管道的状态。

![](img/4d2894fa2cea74e564b0245c01656e4a.png)![](img/16d337a7c14e48e0c85607a9f4797b44.png)

它做了什么宝贝！！！我们完了！希望有帮助！如果你喜欢这个教程，请在 Twitter 上关注我，或者在 T2 的 LinkedIn 上联系我。在未来的日子里，我会有更多与 AWS 相关的教程。此外，请随时问我任何问题！如果可以的话，我非常乐意帮忙。

*Brooke Mitchell 是* *的一名云专家学习者和云开发者。*