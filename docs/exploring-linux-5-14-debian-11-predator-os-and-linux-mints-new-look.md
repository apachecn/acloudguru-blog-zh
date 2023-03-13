# Linux 5.14、Debian 11、Predator-OS 和 Linux Mint 的新外观

> 原文：<https://acloudguru.com/blog/engineering/exploring-linux-5-14-debian-11-predator-os-and-linux-mints-new-look>

在本帖中，我们将报道所有最新的 Linux 新闻。而且我们有很多新闻要讲，包括 Linux Mint 的新外观，Linux Lite 5.6，Predator-OS 特性，Debian 11，以及 Ubuntu 21.04 和 22.10 的发布日期！但首先，让我们谈谈最大的发展之一:Linux 5.14 内核。让我们直接跳进来吧！

Linux 5.14 内核现已正式发布

## 在上个月的 Linux 本月的第一集中，我提到了 5.14 内核的第一个发布候选里程碑，表明第一个开发版本可以进行公开测试，但这不是一个生产就绪的版本。现在，我很高兴地宣布，5.14 内核已经作为 GA 公开发布，这意味着它已经向公众开放，并且现在已经可以生产了。

Linus Torvalds 在 Linux 30 周年后的几天发布了这个[公告](http://lkml.iu.edu/hypermail/linux/kernel/2108.3/05438.html)！我对这个版本感到非常兴奋，因为它在安全性和性能方面都有很大的改进，这对 Linux 用户和云用户都很有价值。

Linux 内核是 Linux 操作系统的核心，它运行大约 90%的公共云工作负载。此外，这个版本已经通过了七个候选版本，所以它是一个经过充分测试的稳定版本。

在这个版本中，我最喜欢注意的特性包括:

对 Raspberry Pi 400 的主线支持，如果你是一个游戏玩家，你可能已经见过这台电脑和键盘合二为一，可以连接到你的电视上。我很高兴看到这个设备被添加到主线支持。

*   该版本还为众多其他硬件类型提供了更好的硬件支持，包括核心处理和对英特尔和 AMD 图形驱动程序的改进。再说一次，谁不喜欢更多的图形和硬件支持呢？
*   添加了内核调度，以帮助缓解 Spectre 和 Meltdown 攻击以及其他现代 CPU 漏洞，在这些漏洞中，无权限用户可以访问内核内存。这个新特性支持性能和安全性，这两者在云计算中都是特别重要的组件。以前的缓解措施要求禁用 CPU 超线程，这会导致性能影响。核心调度支持可信和不可信任务的分离，这样它们就不会共享一个 CPU 核心。这限制了攻击的风险，同时保持了云级别的性能。
*   最后，添加了一个名为 memfd_secret()的新系统调用，它可以为应用程序创建秘密的内存空间，即使是内核也无法访问。我真的很喜欢这个功能，因为我们终于开始解决一些 CPU 漏洞，我们在过去已经看到，非特权攻击者能够访问特权内存空间。
*   要获得新特性和改进的完整列表，请查看位于[kernel.org](https://www.kernel.org/)的发行说明，在那里您也可以根据自己选择的 Linux 发行版手工编译内核。

Debian 11，也被称为牛眼，已经发布

## 截至 2021 年 8 月 14 日， [Debian Bullseye](https://lwn.net/Articles/866272/) 现已全面上市。这个稳定的长期支持版本将支持到 2026 年 8 月。

这个版本开发了 2 年 1 个月零 9 天，它包含了超过 11，294 个新的包，总共有 59，551 个包。此外，上一个版本中超过 72%的包已经更新。这是很多的更新，但是我可以说的是，牛眼是第一个提供支持 exFAT 文件系统的内核的 Debian 版本。并且支持九种不同的架构，包括。英特尔、小端和 ARM 架构。

默认情况下，这个版本还会激活它的持久日志，所以默认情况下您会得到额外的日志记录，而不会浪费任何时间来设置它。您可以通过在[https://debian.org/CD/live](https://debian.org/CD/live)访问该版本来测试该版本的多种桌面环境，而无需安装它，这允许您在计算机内存中运行完整的只读操作系统。

Linux Mint 获得了新的外观

## Linux Mint 正在[重新设计](https://blog.linuxmint.com/?p=4130)他们网站的外观和感觉——以及他们的操作系统。

Linux Mint [宣布](https://blog.linuxmint.com/?p=4130)他们的新网站设计已经完成了 75%,并将于本月部署。他们还说，他们正在审查 Linux Mint 本身的外观和感觉。Mint-X 正在修改应用内通知，并改进 Nemo 工具栏。Mint-Y 正在进行精简，以简化明暗主题以及图标的新艺术作品。Linuxmint.com 的[有完整的功能列表。](https://linuxmint.com/)

Linux Lite 5.6 已经推出(还有一个可靠的 Windows 11 替代版本)

## Linux Lite 5.6 最终版于 8 月 31 日[发布](https://www.linuxliteos.com/forums/release-announcements/linux-lite-5-6-final-released/)。这个操作系统是一个基于 Ubuntu 20.04.3 的稳定版本，随 Linux 5.4.0-81 内核一起提供。

它使用的是 XFCE 桌面，对于从 Windows 切换过来的人来说，这是一个有点熟悉的桌面环境。随着 Windows 11 的重大变化，对于那些希望尝试 Linux 发行版而不是升级现有系统来支持新的 Windows 11 系统要求的人来说，这可能是一个很好的选择。

这个版本包括了“支付你所能支付的”数字下载模式的引入。。。但是该团队强调 Linux Lite 将永远免费。最新版本包括直接从 Lite 欢迎界面进行更简单的安装，更新的图标主题，7 种新壁纸，Python 3，Firefox 91.0.1 和 libre office 6.4.7.2

Ubuntu 22.04 将于 2022 年 4 月发布

## Canonical 现在正在完成 Ubuntu 21.10，预计将于 2021 年 10 月 14 日发布。他们还预计下一个主要版本 Ubuntu 22.04 长期支持将于 2022 年 4 月 21 日发布。因此，您现在就可以升级您的系统，并且有足够的时间来计划下一次升级到长期支持版本。

去直升机那里！Predator-OS 带来了强大的安全功能

## 最后，我想提一下 Predator-OS 的最新版本。如果你没有听说过 Predator-OS，你应该知道！这个新的开源社区项目成立于 2021 年，旨在进行渗透测试和道德黑客攻击，它基于 Ubuntu 20.04 LTS 迷你版和 Linux 内核 5.10 LTS 版，并包括一个轻量级 XFCE4 桌面环境。

该操作系统经过安全强化，可提供匿名性、隐私性和安全性。它包括 100 多种功能，如利用工具、渗透测试、安全审计、取证工具、安全风险分析和漏洞评估。这些功能和更多功能在这里列出[。](https://predator-os.com/fich/index.html)

提升您的 linux 学习水平

## 这就是本月的 Linux 新闻。在我忘记之前，我想让你知道我们提供的几门 Linux 课程: [Linux 操作系统基础](https://acloudguru.com/course/linux-operating-system-fundamentals)和 [ Linux 网络客户端管理](https://acloudguru.com/course/linux-network-client-management)。

这个月就这些了。愿您的源代码保持开放，您的代码可以编译。下次见，继续牛逼吧，云大师们！

加速您在云计算领域的职业发展

## 立即从 ACG 开始，通过围绕 AWS、Microsoft Azure、Google Cloud、Linux 等的实践学习转变您的职业生涯。而且，在有限的时间内，[节省高达 89 美元](https://acloudguru.com/content/cloudgames?utm_source=site&utm_medium=blog&utm_campaign=2021_cloudgames)。