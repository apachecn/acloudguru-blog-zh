# Azure Arc 对私有端点的支持&聚焦 Azure 安全！|云专家

> 原文：<https://acloudguru.com/blog/engineering/azure-arc-support-for-private-endpoints>

本周蓝色新闻发生了什么？首先，你知道 WannaCrypt 在全球范围内造成大破坏已经有五年了吗？它通过加密和交换数据来获取比特币。2012 年 5 月，微软向 Azure 客户提供工具来帮助抵御这一威胁。

WannaCrypt 只是这些年来许多网络攻击中的一个，这就是为什么很高兴看到几个新的 Azure 公告可以抵御其他安全威胁，例如 Azure Arc 对私有端点的支持。所以让我们跳进去，获得安全和保障！

* * *

**通往更好职业的钥匙**

[立即开始 ACG](https://acloudguru.com/pricing) 通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室来改变你的职业生涯。

* * *

## 对可信启动虚拟机的计算库支持

可信启动通过确保安全威胁不隐藏在引导加载程序、操作系统内核或驱动程序中，帮助您保护 Azure 中的虚拟机。这有助于您防御复杂的攻击，否则很难检测到这些攻击。

可信启动支持来自市场的 Linux 和 Windows 虚拟机映像，但您不能将此功能用于自定义虚拟机映像。因此，如果你有像标准化部署或 Azure 虚拟桌面这样的定制虚拟机映像，可信启动是不受支持的。

直到现在，也就是！只要您通过计算机图库管理您的自定义映像，您现在也可以启用可信启动。什么[欢迎更新](https://azure.microsoft.com/en-us/updates/trusted-launch-azure-compute-gallery-support/)。

## 支持 Azure Arc 的服务器的私有端点支持

我有一个问题要问你。

您是否有托管在竞争对手云上的服务器？也许 AWS，或者 GCP？没关系，真的，这里没有评判。

玩笑归玩笑，越来越常见的是组织采用多云和混合部署。也正是因为这个原因，微软创造了 Azure Arc。

有了 Azure Arc，无论 Windows 或 Linux 服务器在哪里使用 Azure Portal、Azure Policy、Azure Automation 等等，你都可以管理它们。

但所有这些都需要公共互联网的可访问性。直到现在。

随着[宣布支持 Arc 启用服务器的私有端点](https://azure.microsoft.com/en-us/updates/arc-server-private-endpoints-ga/)，你将能够使用 Azure Arc，而不必开放公共网络访问。

为了使用此新功能保护 Arc 连接，您需要配置 Azure 专用链接范围，并且您必须使用 ExpressRoute 或站点到站点 VPN 来连接到 Azure。

这将帮助您安全地管理您的服务器，无论它们在哪里。

## **针对流分析的额外托管身份支持**

流分析是一项强大的服务，可以帮助企业从数据中获取价值。它允许您分析、转换和处理来自设备、传感器或其他来源的数据流。

但是，与大多数分析工具一样，流分析通常只是多服务数据分析平台中的一项服务。因此，我们需要确保可以跨服务安全地访问数据。

嗯，[有了这次更新](https://azure.microsoft.com/en-us/updates/cosmosdb-servicebus-asami/)，Stream Analytics 现在可以使用托管身份安全地访问您在 Cosmos DB 和 Service Bus 中拥有的数据。这是对 Blob 存储或 Power BI 等其他服务的现有支持的补充。

有了托管身份认证，您无需担心管理用户名或密码。相反，您可以为您的流分析作业分配一个托管身份，并让平台处理剩下的工作。

现在，您的流分析作业有了 Azure AD 身份，可以安全地授予访问其他 Azure 服务中的数据的权限。

## 跟上所有蓝色的事物

好了，这就是本周的全部内容！想要跟上云的所有事物？在推特上关注 ACG，关注 T2 和脸书。你还可以[在 YouTube 上订阅一位云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的 Azure 每周更新，并在 [Discord](https://discord.gg/zbvhJz66VE) 上加入对话。

想了解更多关于云和 Azure 的信息，或者想在 2022 年开始你的云计算生涯？查看我们每月更新的[免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)的轮换阵容。(不需要信用卡！)