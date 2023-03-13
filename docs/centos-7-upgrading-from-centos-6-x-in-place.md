# CentOS 7:从 CentOS 6.x 就地升级

> 原文：<https://acloudguru.com/blog/engineering/centos-7-upgrading-from-centos-6-x-in-place>

CentOS 7 的最新功能之一是能够将 CentOS 6.x 就地升级到 CentOS 7。过去，升级 CentOS 主要版本的唯一官方方法是清除并重新安装所有内容。

话虽如此，总有一些过程你可以遵循，并获得不同程度的成功(基于对官方库的偏离以及你的设置和软件包列表是如何定制的)。我们已经经历了这个过程大约六次，取得了不同程度的成功，所以让我们来谈谈一些成功和失败。

**成功和失败场景**

同样，有“方法”来完成升级。在这篇文章中，我们将严格关注 CentOS 维护者所支持的官方流程。有鉴于此，这里有一个可能失败的升级的快速列表(对我们来说，所有的升级都以多种方式失败):

*   *   偏离官方资料库——如果你使用 EPEL、美国或任何其他非官方但主要的资料库，你的里程可能会有所不同，但预计会有问题。在使用 EPEL 软件包的普通安装的多台服务器的情况下，所有三台服务器都因软件包一致性、依赖性或冲突错误而失败。
    *   在运行升级前流程之前，不能确保您完全是最新的。由于某种原因，在正确运行 CentOS 6.5(截至本文发布之日，最新的 6.x 版本)之前运行预升级过程，后续的升级尝试很可能会失败。在升级到 6.5 并重新运行后，一定有一些缓存在某处的升级列表没有被正确删除/覆盖/重新生成。我们将对这个问题做进一步的研究，但是要小心。
    *   安装在存储库之外的第三方软件包——当然，有很多原因可以让您从存储库之外的不同地方下载并安装软件包，尤其是在企业环境中。不幸的是，升级过程似乎还不够成熟，无法始终捕获依赖关系，您要么以失败的升级(充其量)而告终，要么以成功的升级而告终，这破坏了您在那些存储库之外安装在其上的所有软件，并且您必须手动修复依赖关系或配置。

那么什么有效呢？嗯，一贯地，在最新的 CentOS 6.5 版本中，使用标准(即默认)存储库作为安装软件的唯一方法的安装在大多数时候都是有效的。我说大部分时间是因为根据你从那些标准软件库中安装了什么软件，各种事情仍然会失败。很明显，这对 CentOS 的维护者来说是全新的东西，就像其他任何东西一样，正在经历成长的烦恼。让我们暂时忽略所有这些，并浏览一下完成升级的正式过程。

那我该怎么做呢？

在新安装并更新到最新版本的 CentOS 6.5 上，您运行一个程序来扫描您的系统并确定您的升级状态(称为预升级助手)。打开命令提示符并键入以下内容，以查看类似于下面所示的输出:

`$ sudo preupgPreupg tool doesn't do the actual upgrade.Please ensure you have backed up your system and/or data in the event of a failed upgradethat would require a full re-install of the system from installation media.Do you want to continue? y/nyGathering logs used by preupgrade assistant:All installed packages : 01/10 ...finished (time 00:00s)All changed files : 02/10 ...finished (time 00:48s)Changed config files : 03/10 ...finished (time 00:00s)All users : 04/10 ...finished (time 00:00s)...042/100 ...done (samba shared directories selinux)043/100 ...done (CUPS Browsing/BrowsePoll configuration)044/100 ...done (CVS Package Split)...|samba shared directories selinux |notapplicable ||CUPS Browsing/BrowsePoll configuration |notapplicable ||CVS Package Split |notapplicable |...`

奇怪的是，这个特殊的过程除了让您知道升级过程中可能出现的问题之外什么也没做。它既不会执行升级，也不会帮助您解决它发现的任何问题。所有这些都是使用一个仍然以其红帽起源命名的工具完成的-*红帽升级工具命令行界面*。在运行 CentOS 7 之前，请务必从导入 CentOS 7 密钥开始，否则它将会失败，从命令提示符:`$ sudo rpm --import https://isoredirect.centos.org/centos/7/os/x86_64/RPM-GPG-KEY-CentOS-7`

现在你可以运行实际的工具了。例如，我用来成功地将我的基本 CentOS 6.5 安装升级到 CentOS 7 的命令如下:

`$ sudo /usr/bin/redhat-upgrade-tool-cli --network 7 --instrepo=https://mirror.centos.org/centos/7/os/x86_64`

此时，升级过程会检索新的启动映像，下载必要的软件包，然后要求重新启动。

在此过程中，如果您收到一个错误或升级工具拒绝运行，则可能是以下两种情况之一导致的:(1)您忘记运行 *preupg* 工具，或(2)出于某种原因，它无法识别您已经运行了。如果你不想运行这个工具或者它忘记你已经运行过了，添加*–force*标志作为第一个参数，它应该会正常运行。

**最终想法**

这是 CentOS 前进的正确方向。强制完全重新安装整个操作系统和所有软件包的旧模式以及随之而来的令人头痛的问题对于 2014 年来说太过时了。已经采取了一些小步骤将这一升级过程带入现代，尽管目前充满了问题和争议，但这一过程已经开始。请在下面的评论中让我们知道你的努力是否成功，以及你在冒险时可能遇到了哪些特殊的问题！