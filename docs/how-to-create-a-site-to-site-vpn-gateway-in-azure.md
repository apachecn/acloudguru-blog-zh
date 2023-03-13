# 如何在 Azure |云专家中创建站点到站点的 VPN 网关

> 原文：<https://acloudguru.com/blog/engineering/how-to-create-a-site-to-site-vpn-gateway-in-azure>

谈到[微软 Azure 认证](https://acloudguru.com/azure-cloud-training)考试，新模式强调工作角色。例如，参加 [AZ-700:设计和实施微软 Azure 网络解决方案](https://docs.microsoft.com/en-us/certifications/exams/az-700)考试将使你获得[微软认证:Azure 网络工程师助理认证](https://docs.microsoft.com/en-us/certifications/azure-network-engineer-associate/)。所以这意味着 cert 验证了实现和配置以网络为中心的 Azure 服务的技能。

在这篇文章中，我将向您展示如何建立一个站点到站点(S2S) VPN 网关，然后使用它来连接 Azure 网络和本地网络，以创建一个混合环境。这是我在一个云专家和 Pluralsight 上的 [AZ-700 微软 Azure 网络工程师助理](https://acloudguru.com/course/az-700-microsoft-azure-network-engineer-associate)课程(和我的合著者 Matt Ulassien 一起)中更详细介绍的内容。请加入我们的学习，获得更多关于 Azure 网络技术的知识！

* * *

**通往更好职业的钥匙**

[立即开始 ACG](https://acloudguru.com/pricing) 通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室来改变你的职业生涯。

* * *

## AZ-700 考试有多难？

在我们开始之前，我想给你简要介绍一下 AZ-700 考试的内容。

AZ-700 考试中的[域如下(最近一次由微软在 2021 年 11 月 23 日更新):](https://docs.microsoft.com/en-us/learn/certifications/exams/az-700)

*   设计、实施和管理混合网络(10–15%)
    *   创建 VPN 来连接我们的内部和 Azure 环境
*   设计和实施核心网络基础设施(20–25%)
    *   示例:在 Azure 中为我们的资源创建虚拟网络
*   设计和实施路由(25–30%)
    *   示例:引导所有流量通过防火墙
*   保护和监控网络(15–20%)
    *   示例:使用 Azure 防火墙保护网络，使用网络观察器排除网络故障
*   设计和实现对 Azure 服务的私有访问(10–15%)
    *   示例:使用私有端点在我们的 Azure 虚拟网络中为非 Azure 服务提供端点

那么 AZ-700 考试难吗？嗯，没有什么是容易的，但所有这些领域都涵盖在我们的证书准备课程。所以我们支持你。

## 在 Azure 中创建站点到站点(S2S) VPN 网关

现在，我们已经了解了官方 AZ-700 考试中涵盖的域，让我们浏览一下在我们的 [Azure 虚拟网络](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview) (VNet)和混合环境的本地网络之间设置 S2S VPN 的步骤。

### 1.让我们的鸭子排成一行

首先，我们需要完成以下先决条件:

1.  拥有一个 Azure 订阅(我推荐使用我们的 [Azure 云沙箱](https://acloudguru.com/platform/cloud-sandbox-playgrounds)来模拟这个组件)。\
2.  有一个兼容的 [VPN 设备](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpn-devices)(提示:你可以使用两个 VNets，一个作为 Azure 网络，另一个模拟你的本地网络——我会在课程演示中介绍这一点。)
3.  为您的 VPN 设备提供一个公共 IP(最好是静态分配)
4.  了解您想要连接到 Azure 的私有 IP 空间，并确保本地和 Azure 之间没有 IP 重叠。

### 2.创建我们的 S2S VPN 设置

接下来，我们可以按照以下步骤开始创建我们的 S2S VPN 设置:

1.  登录 Azure 门户。(这永远是第一步！)
2.  获取我们 Azure VNet 的区域和私有 IP 空间。(如果虚拟网络不存在，请使用默认设置创建虚拟网络。)
    1.  示例地区:美国东部
    2.  示例 IP 空间:10.0.0.0/16
3.  使用以下内容和默认配置选项创建一个 VNet 网关:
    1.  示例地区:美国东部(这必须与 VNet 地区相匹配。)
    2.  网关类型:VPN
    3.  VPN 类型:基于路由
    4.  SKU: VpnGw2
    5.  第二代
    6.  虚拟网络:InsertYourVNetName
    7.  网关子网地址范围:10.0.255.0/27(建议网关子网使用/27 CIDR)
        1.  VNet 网关将使用网关子网在 Azure 端连接我们的 S2S。
    8.  公共 IP 地址:新建
    9.  公共 IP 地址名称:InsertYourPublicIPName
4.  创建本地网络网关。(这代表本地 VPN 设备。)
    1.  IP 地址:YourOnPremVPNPublicIP
    2.  地址空间:YourOnPremisePrivateIPRange
    3.  地区:美国东部(这必须与地区匹配。)
5.  从 VNet 网关资源创建 VPN 连接。
    1.  连接类型:站点到站点
    2.  选择本地网络网关和虚拟网络网关
    3.  指定预共享密钥
    4.  IKE 协议:选择 IKEv2
6.  配置本地 VPN 设备。

这将取决于你的 VPN 设备。(我建议看看微软现有的[配置脚本](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-download-vpndevicescript)是否适合你的需求。)

* * *

![why should i get azure](img/3ee87ddb6a81b5631ab6555721b8b023.png)

*想了解更多关于 Azure 认证的信息？*
*查看我们的* *[Azure 认证和学习路径。](https://acloudguru.com/azure-cloud-training)*

* * *

### 3.检查我们的连接

现在，我们已经创建了从 Azure 到本地的 S2S VPN，我们可以通过从 Azure 门户检查我们的连接状态来确认这一点，方法是导航到我们的 VNet 网关，并在其连接刀片下查看我们的连接状态是否为“已连接”。

好吧，这看起来很简单！开玩笑！在 Azure 中没有什么是容易的——也不应该是容易的，因为这些是有价值的技能，可以转化为技术领域的高薪职位。

如果你想了解更多关于如何使用 Azure 连接我们的本地网络，或者甚至只是使用 Azure 网络技术，请确保查看我们的 [AZ-700 课程](https://acloudguru.com/course/az-700-microsoft-azure-network-engineer-associate)，并使用它来准备 AZ-700 考试，以便你可以在就业市场中验证你的技能。感谢你和我一起发表这篇博文，现在继续做一个令人敬畏的大师吧！