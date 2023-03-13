# Azure 存储帐户网络:何时使用防火墙和服务端点

> 原文：<https://acloudguru.com/blog/engineering/azure-storage-account-networking-when-to-use-firewalls-and-service-endpoints>

最近，当我为即将到来的课程之一[Microsoft Azure Architect Technologies–Exam AZ-300](https://linuxacademy.com/azure/training/course/name/az-300-exam-preparation-microsoft-azure-architect-technologies?utm_source)构建内容时，我发现微软文档并没有立即明确存储帐户防火墙和服务端点的排他性。

我需要一起使用它们吗，或者它们可以彼此完全独立使用吗？

和往常一样，一旦我们深入了解，在测试环境的帮助下，事情实际上是如何工作的就变得更加清楚了。

这篇文章分享了我在这样的旅程中学到的一些重要的经验。

## 我需要同时使用服务端点和存储防火墙吗？

配置存储帐户防火墙时，我们不必配置服务端点。同样，当我们为存储配置服务端点时，它不需要存储防火墙规则来实现安全/私有连接。

这是两个互补的特征。让我们仔细看看为什么。

### **服务端点**

如果我们从服务端点开始，这有助于理解这实际上是虚拟网络的属性。我们可以这样配置它:

*   用一个子网(`subnet1`)创建一个虚拟网络(`vnet1`)
*   运行以下 CLI 命令:`az network vnet subnet update -g vnet1rg --vnet-name vnet1 -n subnet1 --service-endpoints "Microsoft.Storage"`

现在我们实际做的，是 ***通过微软主干网启用了一条新的默认路由***；完全避开公共互联网。

如果您在该子网中有一个网卡，并查看有效路由，您会看到如下内容:

![](img/c62c06a9b0c0abba7b17bed7fa22dcba.png)

这意味着连接到`subnet 1`的设备不再通过公共互联网访问微软存储。

> ***提示*** :服务端点帮助我们创建使用微软主干网而非公共互联网的最佳网络路由。这样做的好处之一是提高了安全性，因为使用此功能的资源将安全地秘密连接到 Microsoft 存储。

### **存储帐户防火墙**

接下来，假设我们想要在网络层保护一个存储帐户。更具体地说，我们希望限制对特定存储帐户的访问，并且只允许可信 IP。我们可以使用存储帐户防火墙来做到这一点。

下面是我们如何配置它的一个例子:

*   创建存储帐户
*   导航到该存储帐户的防火墙和虚拟网络设置
*   通过选择来启用防火墙，以允许来自所选网络的访问
*   添加我们需要的任何允许的 IP(或者不添加任何 IP)

当我们启用防火墙时，对存储帐户配置的第一个改变，就是 ***增加了一个默认的“拒绝”规则*** *。*这可以通过资源浏览器([https://resources.azure.com](https://resources.azure.com))看得更清楚:

![](img/69a68af194253d5ac02ec1fa2bb98b37.png)

**不允许任何东西**访问存储帐户，除了我们免除的服务或我们列入白名单的 IP 地址。另外，请注意，我们不能将私有 IP 地址列入白名单，只能将公共 IP 地址列入白名单。

> ***提示*** :启用存储帐户防火墙会为该存储帐户创建一个默认的“拒绝”网络规则，有效地阻止任何和所有流量。然后，只能通过允许特定虚拟网络或者将公共 IP 地址列入白名单来允许流量通过。

## 我们应该使用一个还是两个功能？

默认的拒绝规则解释了为什么这两个功能有时听起来像是需要同时启用。如果我们*确实*启用了存储帐户防火墙，并且仍然希望 VNet 内的资源能够访问，那么我们有两个选择:

1.  记下我们资源的公共 IP 地址，并将其添加到白名单规则中，或者
2.  为我们资源的子网启用服务端点

然而，没有什么可以阻止我们单独使用这两种服务。我们可以使用服务端点，只是为了优化路由，或者我们可以利用存储防火墙本身来锁定网络访问。

> ***提示*** :这里的关键是要理解这些特性实际上是做什么的。一个用于路由，一个用于网络访问控制。

如果您想了解更多信息，请随时在社区、社交媒体上联系我，或者查看最近在 preview 中发布的 [AZ-300 课程](https://linuxacademy.com/azure/training/course/name/az-300-exam-preparation-microsoft-azure-architect-technologies?utm_source)。新的 [AZ-300 Azure Architect 技术课程](https://linuxacademy.com/azure/training/course/name/az-300-exam-preparation-microsoft-azure-architect-technologies?utm_source)涵盖了这一点，甚至更多。

一如既往，伙计们，我希望这有所帮助！