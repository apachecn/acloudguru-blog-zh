# Windows 服务器热修补不再需要烦人的重启|云专家

> 原文：<https://acloudguru.com/blog/engineering/ws-hotpatching-cross-region-restores-and-other-vm-magic>

本周 Azure 有什么新消息？你问得真有趣！本周，我们将推出 Windows 服务器热修补、虚拟机删除魔术、面向企业的 Spring Cloud 以及跨区域恢复。让我们开始吧！

* * *

**通往更好职业的钥匙**

[立即开始 ACG](https://acloudguru.com/pricing) 通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室来改变你的职业生涯。

* * *

## Windows Server 热修补

IaaS 最好的部分是在安装补丁或更新后重启你的 Windows 服务器…从来没有人这么说过。

我的意思是，重新启动任何计算设备都有点烦人，但当涉及到运行您的关键业务流程的服务器时，它会变得非常可怕。等待一切恢复正常、对关键补丁的焦虑、深夜安排停机时间等等。

但是现在有了[热修补](https://techcommunity.microsoft.com/t5/windows-server-essentials-and/windows-server-hotpatching-is-here/ba-p/3174930)！您可以在 Azure 上修补和更新 Windows Server Azure Edition 核心虚拟机，而无需重新启动。它通过修补正在运行的进程的内存代码来工作。你将需要来自微软的热补丁，到目前为止，它只在 Windows Server 2022 Datacenter，Azure Edition 上工作，但这是一个开始。这将改善所有 Server 2022 虚拟机的保护、部署时间和可用性。当您将此与 Azure 自动管理和 Azure 协调的修补结合起来时，管理虚拟机现在变得更加容易。

需要注意的一点是，在安装非“热修补”的更新时，以及在安装微软所谓的“基线”更新(大约每季度一次)后，您仍然需要重新启动虚拟机。

## **自动删除**

本周的小改进——但非常有帮助——你现在可以在删除相关虚拟机时自动删除磁盘、网卡和公共 IP。我们只用了十年，但它终于来了。耶！

## Azure Spring 云企业版现已推出预览版

说实话，这个故事不是我强势的一面。我还没有在 Azure 上使用过带有 VMware 的 Spring Cloud。但事实证明，Spring Cloud 如此受欢迎，以至于 Azure 创建了一个新的[企业层](https://azure.microsoft.com/en-au/blog/azure-spring-cloud-enterprise-is-now-available-in-preview/)。至少他们是这么宣称的。我敢肯定，这与能否收取更多费用无关……无论如何，新的企业级“包括商业支持的 Spring 运行时组件，以帮助企业客户更快地发货，并释放 Spring 的全部潜力，”正如微软营销所说。

此次发布是微软和 VMware 合作的下一步。我们的计划是最终让您部署多语言应用程序，这些应用程序本质上可以跨任何 Azure 服务、任何云或任何本地系统进行移植。大索赔。我喜欢！如果你是 Azure 上 Spring Cloud 的粉丝，去看看新的企业层。

* * *

**[希望在 2022 年提升您的云计算职业生涯？](https://acloudguru.com/blog/engineering/how-to-begin-your-cloud-career)**
退房 [ACG 的免费计划](https://acloudguru.com/pricing)！[本月的免费云培训](https://acloudguru.com/blog/news/whats-free-at-acg)包括对微软 Azure 云采用框架的介绍。最重要的是，你不需要信用卡来注册！

* * *

## 跨区域虚拟机还原点

您现在可以在您选择的任何公共区域创建[虚拟机还原点](https://techcommunity.microsoft.com/t5/azure-storage-blog/protect-and-recover-your-azure-workloads-from-disasters-using/ba-p/3148732)，而不管虚拟机部署在哪个区域。

假设您有一个工作负载运行在美国东部的一台虚拟机上，您希望保护它免受灾难影响。虽然不常见，但一场灾难可能会拖垮整个地区。现在，您可以定期在远离源区域的目标区域创建虚拟机恢复点，比如北欧。如果您的美国东部工作负载由于灾难或故障而变得不可访问，您可以使用在北欧创建的恢复点之一来创建故障转移虚拟机，从而最大限度地减少数据丢失和停机时间。整洁！

但这还不是全部！您还可以在区域之间复制还原点，以增加灵活性。

## **让美好继续到来**

想要跟上云的所有事物？在 YouTube 上订阅一位云专家的每周云新闻。你也可以在[脸书](https://www.facebook.com/acloudguru)上喜欢我们，在[推特](https://twitter.com/acloudguru)上关注我们，或者在 [Discord](http://discord.gg/acloudguru) 上加入对话。

本周新闻到此结束！直到下一次，勇往直前，学习所有的东西。一如既往地保持敬畏，云大师们！