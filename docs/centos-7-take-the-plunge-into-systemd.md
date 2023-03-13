# CentOS 7:投身 SystemD 

> 原文：<https://acloudguru.com/blog/engineering/centos-7-take-the-plunge-into-systemd>

CentOS 7，连同内核、桌面、软件包和应用程序的大量更改，将“Fedora”和“Debian”带入了深层，并将守护程序和服务管理从旧的“service or /etc/init.d”范式转换为池的“systemd”端。如果你是一个现代 Linux 桌面用户，你可能完全熟悉这种方法，但是，对于那些长期使用 Red Hat 和 CentOS 的“服务”管理方法的管理员来说，这是一个相当大的变化。让我们更深入地了解一下新的做事方式。

**为什么会突然改变？**

简单来说，是时间。现在，我们的服务器已经发展到现代，它们被要求做一切事情，包括为我们做晚餐(嗯，可能还没有那么远)，有很多事情是基于旧的“init”系统(为了完整起见，“init”系统在技术上被归入“sysvinit”类别，以标记它们与很久以前的 Unix System V 的兼容性)不太擅长的，或者需要大量额外的修改。下面是 systemd 可以做的一些在“init”发行版中不受支持的事情:

*   提前阅读
*   基于套接字的服务激活
*   基于设备的服务激活(即 USB)
*   系统快照(虚拟化、ZFS 或其他
*   SELinux 完全集成(内核级，而不是服务级)
*   设备依赖性配置(udev 规则)
*   无连接中断的服务重生
*   服务 SSL 证书/LUKS 密码处理(包括控制台、墙和 Gnome 代理)
*   交互式启动(依赖于服务启动确认)
*   关闭期间用户会话的可靠终止
*   早期引导日志记录

这是 systemd 提供的一个子集，你可以点击这里的查看更全面的列表。

**如何使用**

深入研究 systemd 的最简单的方法是看一下您用来管理流程的命令，作为一个例子。假设我们想看看“sshd”服务是否在 CentOS 6(或另一个“sysvinit”发行版)上运行。我们可以发出以下命令并查看结果:`sudo service sshd statussshd (pid 2095) is running...`

很好。我们知道它在运行，但其他的就不知道了。让我们看看 systemd 如何处理相同的查询，以及它可以提供的额外内省:

`sudo systemctl status sshdsshd.service - OpenSSH server daemonLoaded: loaded (/usr/lib/systemd/system/sshd.service; enabled)Active: active (running) since Sun 2014-08-03 16:08:44 CDT; 1h 11min agoProcess: 761 ExecStartPre=/usr/sbin/sshd-keygen (code=exited, status=0/SUCCESS)Main PID: 776 (sshd)CGroup: /system.slice/sshd.service└─776 /usr/sbin/sshd -DAug 03 16:08:44 centos7vm systemd[1]: Started OpenSSH server daemon.Aug 03 16:08:44 centos7vm sshd[776]: Server listening on 0.0.0.0 port 22.Aug 03 16:08:44 centos7vm sshd[776]: Server listening on :: port 22.Aug 03 16:44:26 centos7vm sshd[2191]: Accepted password for USER from 192.168.1.XX port 60818 ssh2`

`哇！这比我们以前除了问之外不用做任何事情就能得到的信息要多一点。让我们快速看一下新的 systemd 命令以及它们所替代的等效 sysvinit 命令:`

``SYSTEMD SYSVINIT======= ========systemctl start httpd service httpd startsystemctl stop httpd service httpd stopsystemctl restart httpd service httpd restartsystemctl status httpd service httpd statussystemctl enable httpd chkconfig httpd onsystemctl disable httpd chkconfig httpd offsystemctl is-enabled httpd N/Asystemctl mask httpd N/A``

``Now, in general, most modern distributions still “support” the older sysvinit way of doing things. You will see the following message though (for now) if you use the old way:`sudo service sshd restartRedirecting to /bin/systemctl restart sshd.service```

``请记住，这种支持并不保证会一直存在，我怀疑最终会消失。确保您知道新命令。``

``**最终想法**``

``自 2011 年初创建以来，Sysytemd 已经获得了所有主要发行版的支持。以这种方式管理系统的额外功能和灵活性将为您提供以前所缺少的信息和使用的一致性(注意，相同的命令用于做所有事情，例如，没有在 service 和 chkconfig 之间来回切换)。在您开始安装自己的服务或者想要改变系统的默认运行级别之前，这种转换并不困难。我们将在以后的文章中讨论这些话题。如果您有任何疑问或问题，请在下面留下您的评论，我们将尽力帮助您解决！``