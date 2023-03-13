# GNOME 41 Linux 桌面；亲自参加的红帽活动又回来了

> 原文：<https://acloudguru.com/blog/engineering/gnome-41-linux-desktop-plus-in-person-red-hat-events-are-back>

在这篇文章中，我们将报道本月来自 Linux 的所有最新消息，包括对 GNOME 41 的深入研究、Fedora Linux 35 测试版、对 Ubuntu 14.04 和 16.04 的扩展支持、谷歌 Android“上游优先”内核方法、OpenSSH 8.8、Red Hat Summit: Connect 以及网飞将游戏添加到其订阅服务中。

让我们直接跳进来吧！

GNOME 41 桌面环境已经发布

## GNOME 41 桌面环境已经[发布了](https://help.gnome.org/misc/release-notes/41.0/)，增加了许多新特性。改进包括一个新的软件应用程序，并支持使用 Nautilus 文件压缩创建加密的 zip 存档。它还包括一个新的连接应用程序，现在可以显示平铺的连接，从而可以轻松地在不同的远程会话之间切换。我喜欢这个新特性，因为在一个应用程序中管理这些连接要容易得多。

GNOME 41 桌面也有一个新的图形界面用于新的连接。此外，状态菜单中还有新的电源配置和选项，包括一项令人惊叹的改进，让用户知道应用程序何时请求更改电源配置，因为它会影响整体系统性能。

他们还包括一个新的多任务面板和控制面板中的蜂窝部分。多任务面板允许您调整热点和活动屏幕大小选项，蜂窝部分允许轻松配置调制解调器和移动连接。

日历也有变化，允许文件处理，现在可以将它用作默认的日历应用程序。计算器应用程序也进行了彻底的检查，现在有了更多的颜色和查看计算器模式的能力。

总的来说，我们最喜欢的桌面外壳已经做了很多改进，现在增加了更多的颜色和更好的图标。你可以从 gnome.org 下载，亲自测试一下。

*想了解更多关于云安全的信息吗？查看[本月的免费 ACG 课程](https://acloudguru.com/blog/news/whats-free-at-acg)了解安全为重点的云学习自助餐。只需[创建一个免费账户](https://acloudguru.com/pricing)并开始行动。不需要信用卡！*

* * *

红帽峰会:联系现场(和虚拟)活动

* * *

## 第三波红帽峰会发布会已经[揭晓](https://www.redhat.com/en/summit)！20 人参加的红帽峰会:Connect 会议已安排在 10 月、11 月和 12 月举行，将在 20 个不同的主要城市举行。

地点包括波士顿、纽约、奥斯汀、芝加哥、罗利、休斯顿和旧金山，仅举几例。这些联系会议提供了亲自探索动手实验、培训、演示和交流机会的机会。你还可以参加专家咨询会议。

在 Connect 会议上，您可能想要查看的一个令人兴奋的实验室是权威的 Red Hat Enterprise Linux 8 动手实验室，它将帮助您快速了解新的 RHEL 8 内容。

还有一个关于“使用 Red Hat Insights 和 Red Hat Enterprise Linux 评估和解决大规模安全问题”的会议，如果您没有听说过 Insights，它是一个在大规模环境中从高层次识别配置偏差、安全漏洞和关键补丁的有价值的工具，是任何系统管理员或工程师都应该拥有的工具。

Red Hat Summit 是了解、运行和测试 Red Hat 最新软件的绝佳机会。。。同时，您还可以联系您最喜欢的支持团队，提出问题并获得技术配置方面的说明。

如果您有 Red Hat 支持代表，您还可以参加一对一的会议。

与会者将被要求出示全部新冠肺炎疫苗接种证明，并在现场佩戴口罩。如果你愿意，或者如果你不在美国，你仍然可以点播访问红帽峰会 2021 虚拟体验。您可以在[redhat.com/summit](https://www.redhat.com/en/summit)找到更多关于日期和地点的信息并进行登记。

Fedora Linux 35 Beta 发布供公众测试

## Fedora Linux 35 Beta 已经[发布](https://www.redhat.com/en/blog/fedora-35-beta-now-available)进行公开测试。它基于 Linux 5.14 内核，包含 GNOME 41 桌面环境的发布候选版本。如果您想测试这个测试版，请查看许多可用的映像类型，包括服务器映像、桌面映像、基于云的映像和 Linux 容器映像。这个版本包括 firewalld 1.0.0、LLVM 13、GNU 工具链更新、Python 3.10 和对 TLS 上 DNS 的支持。

加速您在云计算领域的职业发展

* * *

## 从 ACG 开始，通过围绕 AWS、Azure、Google Cloud、Linux 等的实践学习转变您的职业生涯。

扩展了对 Ubuntu 14.04 和 16.04 LTS 版的支持

* * *

## Ubuntu 长期支持版本 14.04 和 16.04 现在有扩展支持维护，这需要有效的 Ubuntu Advantage 订阅。这些版本已经分别在 2019 年和 2021 年寿终正寝，但它们仍在许多企业级业务中大量生产。这种延长支持维护使这些版本跟上了新的 10 年支持期。在[ubuntu.com](https://ubuntu.com/blog/ubuntu-14-04-and-16-04-lifecycle-extended-to-ten-years)了解更多信息。

OpenSSH 8.8 已经发布

## OpenSSH 8.8 已经发布，有了重大更新。默认情况下，它现在禁止使用 RSA-SHA 或 SHA-1 哈希数字签名。这确保了更安全的密码，但是如果您的应用程序依赖于 SHA-1，并且您计划升级到 OpenSSH 的最新版本，您可能希望进一步了解此更新。对使用 SHA-256 和 SHA-512 散列的 RSA 签名的支持保持不变

谷歌 Android 转向“上游优先”的新内核特性

## 谷歌[宣布](https://tech.slashdot.org/story/21/09/22/1920258/google-finally-shifting-to-upstream-first-linux-kernel-approach-for-android-features)一个新的“上游优先”的新内核更新方法。

一向以使用下游补丁著称的 Android，现在将把内核补丁推向主线 Linux 内核上游。

Android 的 Linux 内核在到达 Android 手机之前被广泛地分叉，错误修复要花很长时间才能完成。Android.com 的文档显示“这些修改可能是广泛的，以至于在一个设备上运行的多达 50%的代码是树外代码(不是来自上游的 Linux 或 AOSP 通用内核)。”这导致在最初的内核发布和手机发货之间花费了大量的时间，有时发货的手机内核已经有两年了。

这种新的“上游优先”方法对 Android 和客户来说都很棒，因为它确保了新发布的设备中包含新功能和新漏洞修复

Linux 游戏:夜校工作室加入网飞

## Linux 游戏[新闻](https://www.gamingonlinux.com/2021/09/night-school-studio-creator-of-oxenfree-joins-netflix)，夜校工作室，创造者或 Oxenfree，已被网飞收购。第一轮游戏将是专注于移动的游戏，但此次收购表明，更大的游戏——非移动或 VR 游戏——也可能会出现。

提升您的 Linux 知识水平

## 这就是本月的 Linux 新闻。想要跟上 Linux 和云的所有事物？在 YouTube 上订阅一位云专家的每周更新和各种精彩内容。你也可以在[脸书](https://www.facebook.com/acloudguru)上喜欢我们，在[推特](https://twitter.com/acloudguru)上关注我们，或者在[不和谐](http://discord.gg/acloudguru)上加入对话！

直到下一次，希望您的源代码保持开放，您的代码可以编译。继续牛逼吧，云大师们！