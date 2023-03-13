# Docker 桌面不再对“大型”企业免费

> 原文：<https://acloudguru.com/blog/engineering/docker-desktop-no-longer-free-for-some-businesses>

你好，云大师们！我是 Nigel Poulton，这是关于 Kubernetes 最新动态的每月更新。在本帖中，我们将深入探讨令许多人困惑的新 Docker 订阅计划。此外，我将与您分享我对上个月 Kubernetes 前三名公告的选择。

想了解更多？请继续阅读！

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## Docker 桌面不再对大型企业免费

Docker 桌面被世界各地的组织大量使用，但是如果你是一个大企业，Docker 桌面就不再免费了。

我们一会儿会定义“大”。但我认为最重要的是，如果你是一个个人用户，如果你在教育或小型企业，那么没有什么会改变。对你来说还是免费的。

但是如果你是大企业呢？是的，事情正在发生变化。

基本上，如果你雇佣了超过 250 名员工，并且你的年收入超过 1000 万美元，Docker 认为你很大，你需要开始付费。老实说，我完全同意他们的观点。

我的意思是，Docker Desktop 是一款精致的产品，人们每天都从它身上获得价值，所以他们应该付费。如果每个人都继续免费使用它，最终，它将不复存在——我们都不想这样。事实上，我坚信一个健康的码头工人对我们所有人都有好处。

不管怎样，如果你*真的*落入那个大生意桶，你有三个选择:职业、团队或生意。

Docker Desktop Pro 帐户每个用户每月起价 5 美元，团队帐户起价 7 美元，商业帐户起价 21 美元。

Docker Business 是一个新的订阅类别，它的目标是希望对 Docker 开发环境有更多控制的组织。这样，您将获得一个集中的控制平台，能够控制开发人员使用哪些注册表、哪些映像和版本，更好地控制安全性，等等。

所以，是的，如果你很小或者在受教育，你可以在 Docker 个人计划下继续免费使用 Docker。但是如果你很大，做正确的事情，开始付钱。

1.亚马逊 EKS 任何地方

## 好的，所以我上个月的第一选择是宣布 EKS 在任何地方。

亚马逊将他们广受欢迎的弹性 Kubernetes 服务带到本地数据中心。我猜，如果你是一个现有的 EKS 用户，并且你有自己的数据中心，那么将你的 Kubernetes 管理平台整合到 EKS 可能是有意义的，因为这是你实际上将会得到的。我认为，顾名思义，它会像 EKS 一样，只是在你自己的数据中心。

所以相同的部署模型和工具。此外，还可以通过单一控制台查看基于云的本地 EKS 集群。

我想，即使你不是现有的 EKS 用户，但也许你正在评估发行版(可以这么说)，事实上，你现在可以在本地和云中拥有 EKS 的体验和工具，这可能会让 EKS 对你更有吸引力。这显然是亚马逊想要的。

2.NGINX 入口控制器版本 1.0

## 对，本月综述的第二名:Kubernetes 的 NGINX 入口控制器 1.0 版本。

总的来说，Ingress 在 Kubernetes 的最新版本中做了一些大动作。嗯，这一次流行的 NGINX 入口控制器终于到了 1.0，或 GA。这是在几个领域迈出的一大步。

首先，它显示了项目的承诺，我们希望看到这一点。但这也是一个突破性的改变。

它只适用于 Kubernetes 1.19 和更高版本。它需要 networking.k8s.io API 子组中的 v1 API。所以不再有 v1beta1。

您必须使用最新版本的 Kubernetes，并且需要更新清单中的 API 版本。

除此之外还有很多，但是你可以点击[这个链接](https://github.com/kubernetes/ingress-nginx/releases/tag/controller-v1.0.0)获得迁移文档的另一个链接，如果你打算使用它，它们绝对值得一读。

**[观看:自动化 Kubernetes 安全](https://go.acloudguru.com/automating-kubernetes-security-webinar)** [](https://get.acloudguru.com/aws-cloud-formation-power-user-webinar) 在[这个免费的点播网络研讨会](https://go.acloudguru.com/automating-kubernetes-security-webinar)中，学习如何用 Pod 安全策略来增强您的 K8s 安全。我们将向您展示它们是如何工作的，以及在一个真实的 Kubernetes 集群中实现它们的样子。

* * *

3.Snyk 筹集了 3 亿美元

* * *

## 最后，但并非最不重要的一点是，证券公司 Snyk 刚刚在一系列 F 轮融资中筹集了整整 3 亿美元，使其估值达到 85 亿美元。有了 b，这是 10 亿。

所以祝贺 Snyk 的团队。显然，市场很喜欢他们赋予开发者安全性的方式，并使之变得简单。我知道我之前已经说过很多次了，但是现在组织并没有在安全性上浪费时间，所以你也不应该浪费时间。像 Snyk 这样的工具和合作伙伴真的在推针。

跟上 K8s

## 本月 [Kubernetes 本月](https://acloudguru.com/videos/kubernetes-this-month)到此为止。注意安全，我们下个月再见——同一时间，同一地点。

相关 K8s 资源

### *想要了解 Kubernetes 的所有信息？在推特[上关注奈杰尔](https://twitter.com/nigelpoulton)或者在这里关注他[。在 YouTube 上订阅一位云计算专家](https://nigelpoulton.com/),获取定期更新、分析和各种精彩内容。你也可以在[脸书](https://www.facebook.com/acloudguru)上喜欢 ACG，在[推特](https://twitter.com/acloudguru)上关注我们，或者在[不和谐](http://discord.gg/acloudguru)上加入对话！*

*Want to keep up with all things Kubernetes? Follow Nigel on [Twitter](https://twitter.com/nigelpoulton) or keep up with him [here](https://nigelpoulton.com/). [Subscribe to A Cloud Guru](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1) on YouTube for regular updates, analysis, and assorted awesomeness. You can also like ACG on [Facebook](https://www.facebook.com/acloudguru), follow us on [Twitter](https://twitter.com/acloudguru), or join the conversation on [Discord](http://discord.gg/acloudguru)!*