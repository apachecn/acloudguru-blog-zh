# 2021 年的 Linux:回顾之年

> 原文：<https://acloudguru.com/blog/engineering/linux-in-2021-the-year-in-review>

在这篇文章中，我们回顾了 Linux 的这一年——通过对 Linux 历史的概述来庆祝 Linux 的 30 年和开源的辉煌。我们还将报道本月围绕 [ Linux 的重大新闻，包括红帽企业版 Linux 9 Beta 和 Linux 内核 5.14 EOL。](https://acloudguru.com/videos/linux-this-month)

请继续阅读了解更多信息！

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## Linux 历史:**Linux 三十年**

2021 年，Linux 岁了！芬兰计算机科学学生 Linus Torvalds 早在 1991 年就创造了 Linux。他开始做这个是作为一个爱好，因为他当时想为新的 386 处理器开发一个类似 Unix 的操作系统。

他甚至在他的原始邮件中提到这只是一个爱好，他没有计划让它成为像 GNU 一样的专业。嗯，惊喜吧…你做得很好，莱纳斯，我们非常高兴你接手了这个小项目！

我第一次接触 Linux 是在 1999 年的大学里。我参加了一个 Shell 脚本入门课程，Fedora 被安装在实验室服务器上，因为它是免费的且易于扩展。我对 Linux 充满热情，因为它改变了世界处理信息的方式，并且它通过允许我在一个社区中分享对增长的热情而改变了我个人的生活。

没有 Linux，我们就不会有技术与我们今天所知道的世界交织在一起。

它的创新精神和适应性与我们在这里所做的一切产生了共鸣，让 Linux 在我们心中占据了一个非常特殊的位置。为 Linux 的 30 多年干杯！

## 2021 年 Linux 更新和发布回顾

聚焦去年，2021 年对于一些主要的内核更新和新的发行版来说是重要的一年。

今年发布了内核版本 5.12 和 5.14——都有许多新的驱动程序和性能及支持改进。现在，它们都已寿终正寝，长期支持内核 5.15 已作为新的 LTS Linux 内核发布。

Ubuntu [今年发布了几个版本](https://ubuntu.com/about/release-cycle)，包括版本 20.04 长期支持、20.10 和 21.04，它们基于内核 5.11，包括更好的硬件支持和 gnome shell 增强。

Ubuntu 21.10 于 8 月发布，它基于 5.13 linux 内核，为处理器和 GPU 增加了更多的硬件支持。尽管 5.13 在 9 月份停止使用，但 Ubuntu 21.10 将在 2022 年初得到支持，新的 22.04 长期支持版本也将在那个时间段发布。你可以在 ubuntu.com/about/release-cycle.找到 Ubuntu 发布的细节

Fedora 在四月份发布了带有全新标志的第 34 版!更新包括新的 gnome 40 桌面，它被重新设计以使交互更加直观。还包括默认情况下的 BTRFS 压缩，以减少写入放大并节省空间，以及对默认情况下启用的基于交换的操作和 systemd-oomd 的改进，这可以实现更好的内存不足处理，从而减少资源短缺。

Fedora 支持每个版本大约 13 个月，所以在下一个版本发布之前，您还有一些时间来测试这个新的 OS。你可以在 fedoraproject.org 下载。

Debian 在 4 月份发布了 project Bullseye，即 Debian 11。它基于 Linux 5.10 长期支持内核。更新包括超过 11294 个新包，总共超过 59551 个包。其他更新包括对不需要驱动程序的打印机和扫描仪的更多支持，ExFAT 文件系统支持，对本地系统帐户密码的更多加密，以及 systemd 日志中的更多细节。

下一个稳定的靶心版本，11.2，定于 2021 年 12 月 18 日发布。你可以在 release.debian.org 找到更多关于发布的信息。

* * *

*查看[本月免费的 ACG 课程](https://acloudguru.com/blog/news/whats-free-at-acg)了解云学习，包括如何获得 Linux 工作和 Linux 操作系统基础知识。[创建一个免费账户](https://acloudguru.com/pricing)，然后开始玩吧。不需要信用卡！*

* * *

## 2021 年 12 月 Linux 新闻综述

### Red Hat Enterprise Linux 9 Beta 现已正式发布

[红帽企业版 Linux 版本 9 Beta](https://www.redhat.com/en/blog/whats-new-rhel-90-beta) 现已 GA。它基于上游内核版本 5.14，专为要求苛刻的混合多云部署而设计。支持的硬件架构包括 Intel/AMD64、ARM 64 位、IBM Power LE 和 IBM Z。

此版本更新了简化的自动化和管理，包括增强的 web 控制台性能指标，这使得检测性能瓶颈和向通用报告工具提供这些数据变得更加容易。现在可以通过 web 控制台使用实时内核修补功能，并且对映像构建器进行了一些改进，使您可以从单个构建节点构建 RHEL 8 和 9 映像。

安全性和合规性也有所改进，包括 web 控制台中的智能卡身份验证、附加的安全配置文件、SSSD 日志中的更多详细信息以更好地分析性能和配置问题、集成了 openssl 3 和新的安全加密算法以及 IMA 数字哈希和签名。它还包括一个更新，不允许用户通过 SSH 以 root 身份登录。

还有改进的容器开发，有更多的 UBI 容器映像，现在它与 cgroup2 和 Podman 一起发布。除了一长串的更新，用户在学习如何完成新的管理任务方面不会有太多的惊喜。

按照 Red Hat 的说法，如果你熟悉 RHEL8，你会有宾至如归的感觉。如果你想了解一下，可以注册一个免费的开发者账户，在[redhat.com](https://redhat.com/)下载。

### Linux 内核 5.14 是 EOL，5.15 发布

[Linux 内核 5.14 即将寿终正寝](https://www.linuxtoday.com/developer/linux-kernel-5-14-reached-end-of-life-users-urged-to-upgrade-to-linux-5-15-lts/)而 [LTS 内核 5.15](https://www.kernel.org/category/releases.html) 已经发布。

Linux 内核 5.14 于 8 月发布，具有大量新功能，包括更好的硬件支持以及更新的显卡驱动程序、秘密内存空间和核心调度，以帮助消除现代 CPU 漏洞。

5.15 现已发布，并被指定为长期支持内核。

更新的功能包括一个改进的 NTFS3 驱动程序，它为 NTFS 文件系统提供了更多的功能和更好的性能，使您可以像支持原生 Linux 文件系统一样支持 NTFS。为 AMD CPUs 添加了温度监控支持，并为梵高 APU 添加了新的音频驱动程序。

如果你以前没有听说过 APU，它代表加速处理单元，这基本上是一组充当 CPU 和图形处理单元的处理器，通常在游戏控制台上可以找到，所以如果你运行的是支持 Linux 的 Steam Deck 之类的东西，你会喜欢这个更新。
对英特尔 Alder Lake 处理器、英特尔独立显卡和苹果 M1 芯片支持进行了额外的更新，并对 EXT4 和 BTRFS 文件系统进行了改进和优化。鼓励用户在[kernel.org](https://www.kernel.org/)下载最新的稳定内核 5.15.5。

今年到此为止！愿您的源代码保持开放，您的代码可以编译。继续牛逼吧，云大师们！

杰里米·摩根对本文也有贡献。

* * *

*[在 YouTube 上订阅一位云大师](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每周云新闻，在[脸书](https://www.facebook.com/acloudguru)上喜欢我们，在[推特](https://twitter.com/acloudguru)上关注我们，在[不和谐](http://discord.gg/acloudguru)上加入对话。*