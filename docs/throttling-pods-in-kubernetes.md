# Kubernetes 中的节流豆荚|云专家

> 原文：<https://acloudguru.com/blog/engineering/throttling-pods-in-kubernetes>

如果你一直在学习 Kubernetes，那么你可能对 pod 的概念很熟悉。豆荚是 Kubernetes 的重要组成部分。这就是为什么 Minerva 的“ [Pod”(本](https://www.lucidchart.com/documents/view/b1b62a6e-1266-41dd-b48d-3c44252fb88f)[认证 Kubernetes 管理员](https://linuxacademy.com/linux/training/course/name/cloud-native-certified-kubernetes-administrator-cka)课程中使用的互动指南)代表 Pod 指南。

## **吊舱**

pod 被调度到机器或虚拟机，其中调度器(控制平面组件)尝试将 pod 安装到虚拟机上，假设虚拟机具有足够的 CPU 和内存来满足 pod 的需求。对于那些希望利用我们虚拟机的所有资源的人来说，你可能会问“我如何告诉 Kubernetes 在我的虚拟机上安装 pod，以便它利用它拥有的所有资源？”毕竟，我们大多数人都没有能力为我们的 pod 创建无限数量的虚拟机，利用我们购买的每一平方英寸的资源不仅具有成本效益，而且允许我们确保我们的 pod 获得足够的资源来运行，从而使我们的应用程序性能更好。在这个简短的教程中，您将学习如何对您的 pod 使用请求和限制，以便更好地组织您的 pod 在集群中的调度方式。我的目的是让您相信，将这一点添加到每个 pod 定义中是一个很好的想法，可以让您安心，为您在 Kubernetes 上运行的应用程序增加价值。

## **请求和限制**

在创建 pod 时，您可以指定容器需要的 CPU 和内存量，称为**请求**。您还可以对容器应该使用的 CPU 和内存数量设置限制，这被称为**限制**。当考虑 Java 应用程序的 JVM 堆大小时，设置请求和限制变得非常重要。如果设置不正确，JVM 进程很可能会被系统 OOM 杀手杀死。让我们继续创建一个只包含请求的 pod，我将解释这对 pod 有什么作用。首先，创建以下 pod YAML，它将指定要使用的图像和请求数量。如果你不能访问你自己的集群，那么就开始使用 [Linux 学院的免费社区版](https://linuxacademy.com/join/community)(限制访问)。

```
apiVersion: v1kind: Podmetadata:name: pod1spec:containers:- image: busyboxcommand: ["dd", "if=/dev/zero", "of=/dev/null"]name: pod1resources:requests:cpu: 800mmemory: 20Mi
```

继续运行以下命令来创建 pod:

```
kubectl create -f pod.yaml
```

要查看此 pod 以及它在哪个节点上运行，请输入以下命令:

```
kubectl get pods -o wide
```

要获取有关节点及其利用的资源的更多信息，请输入以下命令:

```
kubectl describe node [node_name]
```

**注意** **:** 如果您不知道节点名称，请键入以下内容来获取:`kubectl get nodes`在`kubectl describe node`命令输出的底部，您会注意到请求和限制，类似于此: [![](img/ee55f74138f3636393f2e007fd251170.png)](https://wpengine.linuxacademy.com/wp-content/uploads/2019/05/kubectl-describe-node-command.png) 您可能会从上面的截图中注意到，在这个节点上运行的不止一个 pod。这是因为法兰绒和 kube-proxy 也将运行在集群中的 kube-system 名称空间中。这就是请求总量的来源。从上面的截图来看，法兰绒 pod 请求 100m 的 CPU，而我们刚刚安排的 pod 请求 800m 的 CPU。这使我们的总数 9 亿(90%)列在底部。

## **节点 CPU 资源**

你可能会认为，因为每个 pod 都请求了一个数量，所以它们只会使用请求的数量，仅此而已。这不是真的。实际上，如果需要的话，这两个 pod 很可能会使用所有剩余的 CPU。但是，他们不只是平均分配。剩余的 CPU 以 1:5 的比例分割。第一个 pod 将获得六分之一的 CPU 时间，另一个将获得剩余的六分之五。为了明确说明 pod 可以使用的最大 CPU 和内存量，我们也可以在 pod YAML 中设置限制。这是第一个舱中的 YAML，但我们增加了限制:

```
apiVersion: v1kind: Podmetadata:name: pod1spec:containers:- image: busyboxcommand: ["dd", "if=/dev/zero", "of=/dev/null"]name: pod1resources:requests:cpu: 800mmemory: 20Milimits:cpu: 800mmemory: 20Mi
```

要应用这些更改，您必须删除现有的 pod，并使用修改后的 YAML 重新创建它。使用以下命令删除 pod:

```
kubectl delete pods pod1
```

然后，您可以使用以下命令创建具有新 YAML 的 pod:

```
kubectl create -f pod.yaml
```

我们可以通过输入以下命令来检查 pod 是否正在运行:

```
kubectl get pods -o wide
```

现在我们的 pod 正在运行，它请求了 800m CPU 和 20Mi 内存，因为我们设置了相同的限制，所以它将使用请求的数量，仅此而已。

## **关于 Pod CPU 和内存的更多信息**

这是一个关于在 Kubernetes 中设置 CPU 和内存请求和限制的简短教程。如果你想了解更多关于 Kubernetes 的日程安排，请查看 Linux Academy 上的[云原生认证 Kubernetes 管理员(CKA)课程](https://linuxacademy.com/linux/training/course/name/cloud-native-certified-kubernetes-administrator-cka),或者查看以下免费资源以了解更多关于 Kubernetes 的信息: