# 使用云专家 Azure DevOps 部署 Kubernetes 应用程序

> 原文：<https://acloudguru.com/blog/engineering/deploy-kubernetes-app-with-azure-devops>

**大家好，我是[查德·克罗威尔](https://www.youtube.com/watch?v)，微软 Azure 课程的讲师，在一个云计算大师那里。我非常热衷于帮助 你实现梦想，并帮助你利用自己的技能度过逆境。在一起，我们可以完成任何事情。**

* * *

在科技世界里，我们喜欢创造新的流行语！有些会脱口而出，有些不会。他们中的一些人甚至发现自己在我们的职位上，尽管他们可能不应该这样。DevOps 是那些超级酷的流行语之一。DevOps 是那些听起来很酷的词之一(因为马丁·福勒是这么说的)，而且似乎甚至在我们今天的对话中仍然存在。因此，我认为探索 Azure DevOps 中的新特性并带您通过一个简单的管道会很有趣。

* * *

准备好和云专家一起深入 Azure 内容了吗？

* * *

## DevOps 是什么？

简单来说， [DevOps 就是将之前由于物理系统的约束而分离的两个进程](https://acloudguru.com/blog/engineering/devops-vs-agile-whats-the-difference)合并。这两个过程是开发(构建计算机程序/应用程序的过程)和操作(创建运行所述计算机程序的基础设施/机器的过程)。无论你是不是开发人员，单独工作还是在团队中工作， [Azure DevOps 培训](https://acloudguru.com/course/introduction-to-azure-devops)可以帮助你组织你计划、创建和交付软件的方式。

制约因素是什么？物理机器必须由一群工程师以相当智能的方式组装起来。例如，构建计算机、将其添加到网络、实施身份管理、加强安全性等。快进到今天，已经不是这样了。一切都变了。

## 云改变了一切

许多硬件组件的虚拟化和云的流行(更不用说进入门槛低了)使得许多运营人员改变了他们的工作职能。以前他们处理硬件，现在他们构建代码基础设施(IaC ),以及其他与编码相关的任务。

既然我们已经了解了这些年来工程师工作职能的转变，我们就来谈谈微软 800 磅重的大猩猩(又名 Azure)。Azure 提供的不仅仅是云中的基础设施。有了 PaaS、SaaS 和介于两者之间的一切，Azure 是云中弹性和高可用性的一站式商店。

## Azure DevOps

Azure DevOps 的前身是 Visual Studio Team Services (VSTS)，它简化了从代码集成到软件应用程序发布和测试的流程，让开发人员感到满意。虽然 Jenkins 一直是 CI/CD 软件的主导者，但微软希望窃取一些市场，但仍然支持 Jenkins 以缓解这种过渡。

## AKS 应用集成教程

在真正的边做边学中，让我们直接进入并在 Azure DevOps 中创建一个项目，展示使用一些简单的命令行技巧将应用程序集成和部署到 AKS 中是多么容易。跟着做，最后，你也可以拥有一个运行在 AKS 上的闪亮的新的 web 应用程序，可以从任何 web 浏览器访问，其中包括来自云专家的友好消息。

若要跟进，您必须拥有 Azure 和 GitHub 帐户。GitHub 帐户是免费的，所以如果你还没有注册的话，就直接去 https://github.com 的[](https://github.com)注册吧！

此外，在继续之前，前往 https://aex.dev.azure.com[](https://aex.dev.azure.com)创建一个 Azure DevOps 组织(如果您还没有的话)。只需点击“创建新组织”按钮。

以下所有命令都应该在 Azure Cloud Shell 中运行。通过从任何浏览器进入[【https://shell.azure.com】](https://shell.azure.com)并登录您的 Azure 帐户来访问此 shell。

**PRO 提示:** **可以使用 PowerShell 屏幕，但是在终端中键入“bash”切换到 bash 命令**。

## 我们开始吧！

**首先，将 Azure DevOps 扩展添加到我们的云外壳会话:**

~$ az 扩展添加–名称 azure-devops

**接下来，让我们为我们的 shell 添加上下文来引用我们的 DevOps 组织(我的组织名称是“https://dev . azure . com/ccrowellla/”，但您的名称会有所不同):**

~ $ az devo PS configure–defaults organization = https://dev . azure . com/ccrowellla/

从云壳，我们必须重新登录，这样我们的帐户才能访问 Azure DevOps。按照终端的提示进行登录:

~ ~ $登录￥t1

**接下来，让我们创建一个新的 DevOps 项目:**

~$ az devops 项目创建–命名项目 1

**现在，设置要使用的默认项目:**

~ $ az devo PS configure–defaults project = project 1

**让我们创建一个资源组，以便在逻辑上组织我们将在后续步骤中创建的 Azure 资源:**

~ $ az group create–name aks-rg–location eastus

我们可以为我们的 AKS 集群创建一个服务主体。我们的 AKS 集群将使用这个服务主体来访问 Azure 容器注册表和拉容器映像。

#### 重要提示:将以下命令的输出复制到记事本中，您以后会用到它:

~ $ az ad sp create-for-RBAC–跳过分配

**现在，让我们创建一个 AKS 集群来部署我们的应用程序(在这里，您使用前一个命令的输出将“appId”粘贴到“–service-principal”之后，并将“password”粘贴到“–client-secret”之后):**

~ $ az aks create-g aks-rg-n myaks cluster–node-count 1–service-principal " e 848493 e-1614-4f 58-b6a 7-a 880045 e 7d 8 f "-client-secret " 47 b01a 18-903 e-463 b-ac68-641 b 40 be 80 b 6 "

接下来，让我们创建一个 Azure 容器注册中心(ACR)。这将是我们在 AKS 中使用的容器的存储库。ACR 名称必须是全球唯一的，这意味着世界上没有人可以拥有相同的名称。发挥创意的时间:

~ $ az ACR create-g aks-rg-n uniqueacrname here–SKU Basic–admin-enabled true

**为了允许 AKS 从 ACR 获取图像，我们必须为服务主体设置我们的 Azure RBAC 权限(在此填写您唯一的 ACR 名称):**

~ $ ACR _ ID = $(az ACR show–name uniqueacrnamehere–resource-group AK s23–query“ID”-output tsv)

~ $ CLIENT _ ID = $(az aks show-g aks-rg-n myaks cluster–query " serviceprincipalprofile . clientid–output tsv)

~$ az 角色分配创建–被分配人$ CLIENT _ ID–角色 ACR pull–范围$ACR_ID

#### 现在，让我们进入正题；创建和部署应用程序！

**对于应用程序代码，您将派生 repo，克隆该 repo(从您的 GitHub 帐户)并更改到“pipelines-sample-app”目录:**

**Fork 这个 GitHub repo(在新标签页打开这个链接，点击“Fork”):[https://github.com/chadmcrowell/pipelines-sample-app](https://github.com/chadmcrowell/pipelines-sample-app)**

**一旦分叉，用“git 克隆”将其克隆到云 shell 中的终端会话，但将 github 用户名改为您的用户名:**

~$ git 克隆 https://github.com/<your-github-username-goes-here>/pipelines-sample-app . git

~$ cd pipelines-sample-app

**现在让我们在 Azure DevOps 中创建一个管道:**

~$ az 管道创建-名称“管道 1”

**按照终端提示设置管道:**

**第一次提示:**输入你的 GitHub 用户名；按回车键

**第二次提示:**输入你的 GitHub 密码；按回车键

**第三次提示:**再次输入你的 github 密码确认；按回车键

**第四次提示:**输入服务连接名称(如管道)；按回车键

**第 5 次提示:**选择【3】部署到 Azure Kubernetes 服务；按回车键

**第 6 次提示:**选择您刚刚创建的 k8s 集群；按回车键

**第 7 次提示:**选择【2】为“默认”kubernetes 命名空间；按回车键

**第 8 次提示:**选择您刚刚创建的 ACR 按回车键

**第 9 次提示:**输入图像名称值(回车接受默认)；按回车键

**第 10 次提示:**输入服务端口的值(回车接受默认)；按回车键

**第 11 次提示:**输入一个值，为拉式请求启用审核应用流(按 Enter 键，无需键入值)

**第 12 次提示:**选择【1】继续生成 YAML；按回车键

**第 13 次提示:**选择【1】直接提交到主分支；按回车键

**恭喜恭喜！**你已经创建了一个 Azure DevOps 项目！等待大约四分钟，让应用程序构建容器，推送到 ACR，然后部署到 AKS。

**通过获取 kubeconfig 凭证来访问您的 AKS 集群:**

~ $ az aks get-credentials–resource-group aks-rg–name myaks cluster

**查看您的项目已经创建的 Kubernetes 资源:**

~$ kubectl 获取全部

在新的部署和 pod 中有一项服务。复制服务 IP 地址(在“外部 IP”下)并粘贴到一个新的浏览器选项卡中，在末尾添加“:8080”(例如 104.45.182.156:8080)。

### 这是你的最终结果:

![A Cloud Guru loves Kubernetes](img/2685d18e135e16d380d65aff528bec9c.png)

## 摘要

在这篇短文中，我们在 Azure DevOps 中创建了一个新项目。在该项目中，我们建立了一个 CI/CD 渠道。该管道在一个容器内构建我们的应用程序，将该容器推送到容器存储库，并将该容器部署到 AKS。最终允许我们通过 Kubernetes 服务从 web 上查看我们在 AKS 中运行的 web 应用程序。很酷吧。

**重要的**:注意我们管道的触发器。回到你的分叉回购，查看文件“azure-pipelines.yml”。您应该看到“trigger:–master”这一行，这意味着每当我们对主分支进行更改时，一个新的构建就会自动开始。

所以，这里最大的收获不是我们运行了 web 应用程序。此外，从现在开始对应用程序的所有更改都将自动部署到我们的 AKS 集群中。这意味着当您开始开发应用程序时，您可以立即“实时”看到变化。太棒了，对吧？！？

如果你和我一样，对将这种自动化构建到你的部署过程中感到兴奋，请查看我的课程“[用微软 Azure](https://acloudguru.com/course/build-and-deploy-pipelines-with-microsoft-azure) 构建和部署管道”，在那里我演示了许多这方面的其他例子。

* * *

你准备好让你的技能更上一层楼了吗？现在开始训练。

* * *

### 想要更多的 DevOps 善良？看看这些: