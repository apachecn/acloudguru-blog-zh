# 微软推出 VPN 网关 NAT，Azure 应用程序网关更新

> 原文：<https://acloudguru.com/blog/engineering/microsoft-rolls-out-vpn-gateway-nat-azure-application-gateway-update>

当一些人关注另一个云会议的时候， [Azure 本周发生了什么？我很高兴你问了！我们得到了](https://acloudguru.com/videos/azure-this-week) VPN 网关的改进，一些应用程序网关的更新，以及新的 Azure 功能特性。让我们开始吧！

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

GA 中的 VPN 网关 NAT

## 当您的公司建立本地网络时，它具有本地 IP 范围，例如从 10.1.1.1 或 192.168.1.1 开始。当其中两个网络需要通过 VPN 通信，并且定义了重叠的 IP 地址时，就有问题了。(你不希望你的办公室打印机突然与你的新 Pixel 6 Pro 共享一个 IP 地址。)

Azure VPN Gateway 有一项新服务可以提供帮助: [VPN Gateway NAT](https://azure.microsoft.com/en-au/updates/vpn-nat-now-ga/) 。

网络地址转换(或 NAT)功能旨在解决这种情况。这是指在互联网上或通过专用广域网使用 VPN 连接专用网络。网关设备上的 NAT 根据 NAT 策略或规则转换源和/或目的 IP 地址，以避免地址冲突。

这是朝着更健壮、更通用的混合环境迈出的又一步。干得好，蔚蓝。

*想要了解更多关于云开发的信息(有或没有特定的网络元素)？查看 ACG 的免费计划。不需要信用卡！*

* * *

应用程序网关上的通配符监听器

* * *

## Azure 应用程序网关是一个第 7 层路由服务，用于 web 应用程序的传入流量。(第 7 层是指 HTTP 层，而不是 7 层 dip。)

在其他特性中，您可以基于 URL 路径(如/images 或/customer)将流量路由到多个后端 web 应用程序。这是一种优化 Azure 基础设施中面向单一客户的站点的优雅方式。

其中一个障碍是，您必须完全限定您想要路由的所有路径，这有点死板，有时很难管理。

不过从本周开始，Azure 应用网关[支持](https://azure.microsoft.com/en-au/updates/general-availability-wildcard-listener-on-application-gateways/)使用通配符，如星号(*)和问号(？)用于多站点 HTTP(S)侦听器上的主机名。这将使服务在更多的场景中更具可配置性！

AWS 中的 Azure 用户？

* * *

### 当热爱 Azure 的 Lars 前往黑暗面并尝试 AWS 任务时会发生什么？我们挑战 Lars 在他不知道的云平台上走过(或绊倒)一个他从未见过的场景。

应用服务和 Azure 功能中的自定义 OpenID 提供程序

* * *

## 最后，对应用服务和 Azure 功能的一个小而重要的更新。

为这两个服务提供的定制 OpenID 现在已经全面上市。

OpenID 是什么？这是一个开放的标准和分散的认证协议，作为一种标准化的用户认证方式，例如当你使用你的脸书账户登录活动网站购买*油脂*复兴之旅的门票时。

好吧，现在您可以使用定制的 OpenID 提供者了——如果您碰巧有自己的提供者的话。我不会深入讨论你如何向一个定制的 OpenID 提供者注册你的应用，但是 Azure 会在这里的文档[中介绍。哦，我有没有提到它也适用于 Azure 函数？](https://docs.microsoft.com/en-us/azure/app-service/configure-authentication-provider-openid-connect)

查看新的 AZ-500 课程

## 本周的新闻到此结束。我确实想提一下本周在 ACG 平台上推出的全新的 AZ-500 微软 Azure 安全技术课程。令人难以置信的 Azure 安全向导李中清是该课程背后的大师。

嗯，正如我们在云专家团队中所说的，当你意识到已经是 12 月了，你还没有衣服穿的时候已经太晚了，但是请记住，帽子预算很早就获得了批准:“寻找，你就应该云！”继续牛逼吧，云大师们！

*想跟上万物云？* [*在 YouTube 上订阅一位云专家*](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1) *的每周微软 Azure 新闻(以及其他云提供商的新闻)。你也可以像我们一样关注*[](https://www.facebook.com/acloudguru)**，关注我们的* [*推特*](https://twitter.com/acloudguru) *，或者加入* [*不和谐*](http://discord.gg/acloudguru) 的对话。*

* * *