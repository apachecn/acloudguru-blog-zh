# 随着 VPN 的围攻，云桌面得到了他们的特写

> 原文：<https://acloudguru.com/blog/engineering/vpn-cloud-desktop-amazon-workspaces>

预测 Linux 在桌面上的“年份”可能永远是徒劳的。但我认为我们可以有把握地说，2020 年是云中桌面之年。

仅 Amazon Workspaces 一家就报告称过去几周使用量增长了十倍，原因不难理解:人们需要可以在家访问的可控工作环境，祝 T2 好运，现在就能买到笔记本电脑。但是这里正在发生更深层次的变化。

**在家工作正在扼杀公司网络(字面上和象征上)**

传统的网络安全“城堡”模式用私有网络的高墙将可信服务包围起来，只有通过 VPN 的吊桥才能访问。这些网络是为无云世界设计的，大多数应用程序和数据由直接连接到公司局域网的用户访问。

远程工作和基于云的工具如 Slack 和 GSuite 的兴起已经侵蚀了工作只发生在企业内部的假设。但是没人能预料到在过去的几个月里突然出现的全球范围的在家工作的转变。

当每个员工的房子突然变成他们自己在城堡周围的迷你前哨时，会发生什么？[紧张的 VPN 和过载的网络](https://techcommunity.microsoft.com/t5/office-365-blog/how-to-quickly-optimize-office-365-traffic-for-remote-staff-amp/ba-p/1214571#)，因为吊桥无法承受试图远程访问其应用程序的庞大人群的压力。

从短期来看，系统管理员[报告称，他们通过最大化许可来扩大 VPN](https://www.reddit.com/r/sysadmin/comments/fj361t/how_is_everyone_increasing_their_vpn_capacity/)的规模，以应对前所未有的流量。但是就像笔记本电脑一样，VPN 硬件现在很难获得，采购过程[可能需要几周](https://diginomica.com/coronavirus-exploding-remote-workforce-heres-how-it-should-prepare)。所以很多人也配置了“[分割隧道](https://stackoverflow.blog/2020/03/13/scaling-your-vpn-overnight/)”，只推送敏感流量通过 VPN，让其他流量通过个人用户的常规网络。这在带宽成本和用户速度方面具有优势，但也会使您的网络受到来自受损终端用户设备的安全威胁。(这就是为什么一些监管机构对此不以为然。)

**未来:身份**

就像火药让城堡变得过时一样，解决我们遭受的网络问题的真正办法不是建立一个更好的 VPN，而是重新设想我们访问和保护数据本身的方式。

科里·奎因，著名的云经济学家和 T2 的 AWS 专家，称只能通过 VPN 访问的可信企业网络是过时的设计。“身份必须成为新的前沿，”他说。

[基于身份的网络](https://www.hashicorp.com/identity-based-security-and-low-trust-networks)意味着与服务相关的短期凭证，而不是长期的“服务账户”。这意味着 SSL 流量，而不是一个很可能受到危害的“可信网络”。正如谷歌的[“零信任”网络政策](https://www.beyondcorp.com/)所展示的那样，“BeyondCorp”运动预见了一个没有 VPN 的世界，我们的工作存在于云服务上，任何地方的员工都可以访问。当您的网络基础设施是互联网本身时，您可以无限制地扩展。

但是，BeyondCorp 的设置存在许多实际障碍。正如 Quinn 指出的那样，许多企业应用程序仍然是在这样的假设下构建的，即网络请求通过 LAN 传输到位置相近的系统。由云服务连接的世界需要非常不同的假设来避免淹没在延迟中。我们甚至还没有开始考虑那些没有跟上云计算步伐的监管者的约束。

**桌面即服务:弥合差距**

好吧。你不能让每个人都在家攻击 VPN，但是到下一个 sprint 结束时，大规模的组织转移到云原生应用和无边界安全不会发生。

这就是桌面即服务(DaaS)提供商如亚马逊工作区和 Azure 虚拟桌面的用武之地。您的用户可以使用云提供商的基础设施( [VDI](https://acloudguru.com/blog/engineering/aws-workspaces-vs-azure-virtual-desktop-choosing-your-vdi-solution) )向他们提供类似的体验，而不是登录到企业数据中心托管的环境中。

云桌面让您可以将最终用户设备(此时很可能是个人笔记本电脑)视为无特权的哑终端。IT 仍然可以控制云工作区上的内容，包括防病毒软件和证书。但是这一次，扩展和硬件管理不是您的问题。如果有人的 BYO 设备坏了，不用担心备份，一切都在云端。

奎因认为这是迈向真正的云原生工作环境的第一步，但提醒可用性的重要性:“即使非技术人员也需要能够设置这一点。”您希望 DaaS 体验像登录一样简单，不需要复杂的客户端配置。我还没有使用过 Windows 虚拟桌面，但我已经断断续续地使用亚马逊 Workspaces 大约六年了，我可以确认 PCoIP 技术的效果[和 Jeff Barr 所说的](https://aws.amazon.com/blogs/aws/i-love-my-amazon-workspace/)一样好。它对本地桌面的响应不太快，但也不会明显滞后，而且能完成任务。

如果你需要访问公司网络上的服务，你仍然需要在你的云桌面上安装一个 VPN 客户端。(尽管 Workspaces 位于 VPC，所以如果你通过 VPN 访问 [AWS 服务，你可能只需要 VPC 对等工作空间。)但此时你的目标应该是减少需要建立这种联系的案例数量。GSuite 或 Office365，Slack 和 Zoom——这些工具可以伸缩，所以你不必。Workspaces】在 6 月份](https://acloudguru.com/hands-on-labs/creating-an-aws-site-to-site-vpn)大幅降价，这也有所帮助。

你可能觉得现在还没有准备好离开公司网络城堡的围墙。但你也可能别无选择。云桌面之年已经到来，从内部网络到云的工作转型才刚刚开始。

* * *

*面向企业的 ACG 加速您向云的迁移。*