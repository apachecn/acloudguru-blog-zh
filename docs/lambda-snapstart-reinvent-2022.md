# Lambda SnapStart:我们从 re:Invent 2022 那里了解到了什么

> 原文：<https://acloudguru.com/blog/business/lambda-snapstart-reinvent-2022>

AWS re:Invent 的第一个主题是关于性能的。因此，我们惊喜地听到 Peter DeSantis 在他周一晚上在 AWS re:Invent:Lambda SnapStart 的[主题演讲中宣布了一个新的 Lambda 功能。](https://acloudguru.com/blog/engineering/aws-reinvent-2022-day-1-overview)

这是我们目前所知的。

## 什么是 Lambda SnapStart？

Lambda SnapStart 通过创建 Lambda 函数的快照来绕过通常的初始化过程，几乎消除了冷启动过程。

Lambda 最大的优势之一——也是让开发人员不断回来的原因——是它处理尖峰工作负载的能力。通俗地说，就是处理工作量意外持续增加的能力。但是对于想要使用 Lambda 的开发人员来说，最大的挑战是经常发生的冷启动。特别是对于那些使用 Java 的人来说，漫长的初始化周期让 Lambda 冷启动更加痛苦。尤其是在 Java 环境中。

至少到目前为止。根据 DeSantis 的说法，使用 Lambda SnapStart 的组织应该会看到冷启动时间提高了 90%。

## AWS SnapStart 如何让我的组织受益？

通过消除最大的障碍，AWS 为更多的组织将工作负载转移到 Lambda 上铺平了道路。

### 为什么要用 Lambda？

Lambda 是一个无服务器的基础设施平台，在特定事件触发时运行代码。这个想法是，开发人员可以专注于代码，而不用担心创建或维护底层基础设施。所以它很受开发者的欢迎，因为它的灵活性。他们可以编写代码，并在几分钟内获得实时反馈。而且它很受领导们的欢迎，因为它能以最低的运营成本运行。

有了 Lambda，AWS 可以为您执行所有的应用程序操作和管理需求，包括容量供应、监控、运行前端 web 服务和应用安全补丁。这为组织带来了四大好处。

#### 现收现付模式

现收现付模式对于公共云服务来说并不新鲜，但 Lambda 是最能节省成本的模式之一。EC2 实例必须被启动来接收请求，所以它们会保持长时间运行——只要它们还在运行，您就要为它们付费。Lambda 让你更接近于只为你想运行的代码付费。

#### 事件驱动的基础设施

Lambda 是专门设计的，只在被触发时运行。虽然它是全天候可用的，但您不必为每一秒钟付费。这使得它成为流量具有高峰和低谷的服务的最佳解决方案。

#### 按比例建造

Lambda 的构建是为了根据请求的并发执行的数量，即时自动地扩大或缩小并行执行的规模。一旦执行，分配给该函数的所有资源都会自动销毁。

#### 支持多种框架

无论你运行的是 Java、Go、PowerShell、Node.js、C#、Python 还是 Ruby 代码，Lambda 都自带对该语言的原生支持。在使用运行时 API 开发函数时，还可以使用其他编程语言。

总的来说，Lambda 是为开发人员设计的，以最小的开销快速轻松地发布应用程序代码。Lambda SnapStart 增强了这些特性，使得 AWS Lambda 功能对最敏捷的开发团队更具吸引力。

## AWS SnapStart 是如何工作的？

一旦你启用了 Lambda SnapStart，你的函数需要运行一次才能生效。在标准初始化之后，Lambda SnapStart 获取其状态的加密快照，并将其缓存以供将来使用。当该函数再次被触发时，Lambda SnapStart 会抓取缓存的快照，而不是运行整个初始化阶段来启动该函数。

Lambda SnapStart 对所有 Lambda 用户都可用，但在使用前必须启用。它目前仅适用于使用 Corretto 运行时的 Java 函数。