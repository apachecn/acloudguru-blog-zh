# 从头开始开发 Kubernetes 运营商|云专家

> 原文：<https://acloudguru.com/blog/engineering/developing-kubernetes-operators>

Kubernetes 是构建其他平台的一个很好的平台。这意味着它非常适合创建符合您需求的工作流。Kubernetes 中的操作者模式是启用定制工作流的关键，开发操作者使您能够作为平台提供商利用 Kubernetes。

我们将在我的课程“[从头开始开发 Kubernetes 操作符](https://acloudguru.com/course/developing-kubernetes-operators-from-the-ground-up)”中深入介绍开发 Kubernetes 操作符的过程，但是如果您想开始开发一个操作符，只需看看这个快速指南就可以了！

## **你将需要什么**

首先，我们需要确保拥有开发操作符所必需的工具。我们将讨论如何创建一个基于 go 的 Kubernetes 操作符。以下是您需要的工具:

*   [**Go**](https://www.techtarget.com/searchitoperations/definition/Go-programming-language) :这将是用于构建操作符的编程语言。
*   [**Docker**](https://docs.docker.com/engine/install/) :这将用于构建和推送映像，如果您选择将 kind(Docker 中的 Kubernetes)用于本地 Kubernetes 集群，则需要安装 kind。
*   [**操作员 SDK**](https://sdk.operatorframework.io/docs/installation/) :这有两个组件，列举如下:
    *   *Operator-SDK*:命令行界面(CLI)工具和 SDK 方便了操作员的开发。
    *   操作员生命周期管理器(Operator life cycle Manager):这有助于集群内操作员的安装、升级和基于角色的访问控制(RBAC)。
*   **Kubernetes 集群:**这个应该是[在本地运行](https://www.techtarget.com/searchitoperations/answer/Evaluate-3-ways-to-run-Kubernetes-locally)。我推荐 [ki](https://kind.sigs.k8s.io/docs/user/quick-start) [n](https://kind.sigs.k8s.io/docs/user/quick-start) [d](https://kind.sigs.k8s.io/docs/user/quick-start) 做这个，但是任何当地的 Kubernetes 集群都可以。
    *   对于本地开发和测试，使用 with **cluster-admin** 权限。
    *   您还需要安装 [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl) ，这样您就可以与您的集群进行交互。
*   **图像注册:**例如，使用 hub.docker.com 发布图像。

安装好这些工具后，乐趣就开始了。

## **创建操作员项目**

首先，我们需要为 operator dev 项目创建项目目录。我们需要创建它，然后移动到项目目录中。

```
mkdir memcached-operator cd memcached-operator
```

在我们移动到目录中之后，我们就可以初始化项目目录并下拉脚手架文件来帮助您创建操作符。这里是我们开始使用运营商 SDK 的地方。您将使用带有`--domain`和`--repo`标志的`operator-sdk init`命令。在我的课程中，我将更详细地解释为什么这些选项是必要的。

```
operator-sdk init --domain example.com --repo github.com/example/memcached-operator
```

## **创建 API 和控制器**

我们的下一步是为我们的操作员创建一个简单的 API 和控制器。在本课程中，我们将创建一个更健壮的 Memcached 操作符，但对此我们只是想开始做些事情，所以我们可以简单地使用`operator-sdk create api command`。为了创建这个 API 的控制器和其他资源，我们还将使用`--resource`和`--controller`选项。

```
perator-sdk create api --group cache --version v1alpha1 --kind Memcached --resource --controller
```

## **创建和部署操作员图像**

接下来，我们将使用 docker 来构建我们的操作员映像并将其推送到我们的映像注册中心。在本课程中，我们将简单地使用 Docker Hub，但是您可以使用任何您想要的注册表。您将使用以下命令来构建和推送映像。

```
make docker-build docker-push IMG="example.com/memcached-operator:v0.0.1"
```

现在我们已经构建了我们的操作员映像，对于如何部署我们的操作员，我们有几个选项。

### **使用 OLM 部署**

我们的第一种方法是使用运营商生命周期管理器来部署我们的运营商。OLM 允许您使用操作员框架轻松地管理、版本化和升级您的操作员。首先，我们需要在集群中启用 OLM。

```
operator-sdk olm install
```

接下来，我们将为我们的操作员创建包映像，然后我们将构建并推送映像。您将使用 make bundle、make `bundle-build`和 make `bundle-push`命令来完成这个任务。

```
make bundle IMG="example.com/memcached-operator:v0.0.1" make bundle-build bundle-push BUNDLE_IMG="example.com/memcached-operator-bundle:v0.0.1"
```

接下来，我们将使用`operator-sdk run bundle command`将操作员部署到我们的集群中。

```
operator-sdk run bundle <some-registry>/memcached-operator-bundle:v0.0.1
```

然后，您可以使用我们下载的脚手架创建一个示例定制资源。

```
kubectl apply -f config/samples/cache_v1alpha1_memcached.yaml
```

这将显示如下所示的输出:

```
memcached.cache.example.com/memcached-sample created
```

接下来，如果我们想卸载我们的操作员，您可以使用以下命令:

```
operator-sdk cleanup memcached-operator
```

### **直接部署到集群**

我们部署操作员的下一个方法是直接部署到集群。我们将使用 make deploy 命令。

```
make deploy IMG="example.com/memcached-operator:v0.0.1"
```

部署操作符后，我们就可以创建自定义资源了。

```
kubectl apply -f config/samples/cache_v1alpha1_memcached.yaml
```

接下来卸载您将简单地运行以下:

```
make undeploy
```

### **在集群外本地运行**

最后，我们的最后一种方法是在部署到集群之前测试我们的操作员。您将简单地使用此命令来完成此操作:

```
make install run
```

这将运行它在您的终端，并退出它只需做一个 ctrl+c。

## 那么下一步是什么？

既然你已经有了基本的东西，我相信我们已经激发了你的兴趣！如果这是一个你感兴趣的话题，并且你想更深入地研究这个话题，那么就来看看我的课程“[从头开始开发 Kubernetes 操作符](https://acloudguru.com/course/developing-kubernetes-operators-from-the-ground-up)”。我将进一步深入介绍所使用的工具以及构建第一个基于 go 的 Kubernetes 操作符的过程。

做一个令人敬畏的大师，学习所有的东西！