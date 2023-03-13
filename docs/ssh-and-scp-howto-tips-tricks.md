# 如何使用 SCP 和 SSH Linux 命令

> 原文：<https://acloudguru.com/blog/engineering/ssh-and-scp-howto-tips-tricks>

本教程还记录了 Linux 命令之间的一些重要差异。

Linux 就业市场继续增长和扩大，我们的 [LFCS](https://acloudguru.com/course/linux-foundation-certified-system-administrator-lfcs) 课程将帮助你准备一个标准的行业 Linux 管理认证。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

难度: ***基础***

在我们开始之前:在本教程中，你将会遇到 ssh 和 SSH。区别在于:ssh 是通用协议，SSH 是 linux SSH 客户端命令。

SCP 命令

## scp 命令允许您通过 ssh 连接复制文件。如果你想在计算机之间传输文件，例如备份一些东西，这是非常有用的。scp 命令使用 ssh 命令，它们非常相似。然而，有一些重要的区别。

如何使用 SCP

### 从(远程)服务器拷贝到您的电脑

1.  从您的电脑拷贝到(远程)服务器
2.  从一台(远程)服务器复制到另一台(远程)服务器
3.  在第三种情况下，数据直接在服务器之间传输；你自己的电脑只会告诉服务器做什么。

这些选项对于许多需要传输文件的事情非常有用，所以让我们来看看这个命令的语法:

上面的 scp 命令会将文件“examplefile”传输到服务器“yourserver”上的目录“/home/yourusername/”，尝试使用用户名“yourusername”获得 ssh 访问。这是相当多的信息，但 scp 真的需要全部。嗯，几乎全部。您可以省略“您的服务器”前面的“您的用户名@ ”,但前提是您想在自己的计算机上使用当前用户名登录服务器。

```
[pineehad@localhost ~]$ scp examplefile yourusername@yourserver:/home/yourusername/
```

让我们仔细看看命令的结尾。那边有个冒号，后面有个目录。就像 Linux 的普通 cp 命令一样，scp 需要知道源文件和目标目录(或文件)。对于远程主机，文件/目录以这种方式提供给 scp 命令。您也可以将一个(或多个)文件从(远程)服务器复制到您自己的本地计算机上。让我们来看一个例子:

*注意:末尾的点表示当前的本地目录。这是一个方便的技巧，可以在 Linux 的任何地方使用。除了单点之外，您还可以键入双点(..)，是当前目录的父目录。*

```
[pineehad@localhost ~]$ scp yourusername@yourserver:/home/yourusername/examplefile .
```

这将把文件“/home/yourusername/examplefile”复制到您自己计算机上的当前目录中，前提是用户名和密码是正确的，并且该文件确实存在。您可能已经猜到，以下命令将文件从一台(远程)服务器复制到另一台(远程)服务器:

*注意:要使上面的命令工作，服务器必须能够互相连接，因为数据将在它们之间直接传输。*

```
[pineehad@localhost ~]$ scp yourusername@yourserver:/home/yourusername/examplefile yourusername2@yourserver2:/home/yourusername2/
```

如果服务器由于某种原因不能互相连接(例如，如果端口 22 在一端没有打开)，你将不能复制任何东西。在这种情况下，首先将文件复制到您自己的计算机上，然后复制到另一台主机上。或者使服务器能够彼此联系(例如通过打开端口)。这些是 scp 的主要用途。

我们将更深入地讨论 ssh 和 scp 之间的区别。实际上，您也可以像普通的 cp 命令一样使用它，而不需要任何 ssh 连接，但这完全没有用。它要求你多打一个“s”。

用 scp 指定端口

## 当涉及到端口时，scp 命令的行为稍有不同。您可能认为应该这样指定端口:

然而，这是行不通的。您将会看到如下错误消息:

```
[pineehad@localhost ~]$ scp -p yourport yourusername@yourserver:/home/yourusername/examplefile .
```

这是由 scp 的不同架构造成的。它的目标是类似于 cp，cp 也有-p 选项。然而，在 cp 术语中，它的意思是“保存”，它使 cp 命令保存诸如所有权、许可和创建日期之类的东西。

```
cp: cannot stat `yourport': No such file or directory
```

scp 命令也可以保存类似的东西，并且-p 选项启用了这个特性。应该使用-P 选项指定端口。因此，以下命令将起作用:

还要注意-P 选项*必须*在(远程)服务器的前面。

```
[pineehad@localhost ~]$ scp -P yourport yourusername@yourserver:/home/yourusername/examplefile .
```

如果您在主机语法后面加上-p，ssh 命令仍然可以工作，但是 scp 不行。为什么？因为 scp 也支持两个服务器之间的复制，因此需要知道“-P”选项适用于哪个服务器。

SSH 命令

## SSH 是某种安全 SHell 的缩写。这是一种允许计算机之间安全连接的协议。

在本教程中，我们将处理 Linux 上的 ssh 命令，OpenSSH 版本。今天，大多数 Linux 发行版都有 OpenSSH 客户端的特性，但是如果你想确定的话，可以看看你的系统上的 SSH 联机帮助页。您可以通过键入以下命令来完成此操作:

*注意:这应该在终端中完成。*

```
[pinehead@localhost ~]$ man ssh
```

如果它显示如下内容:

那么您可以非常确定您运行的是 OpenSSH 版本。有关 SSH 的更多背景信息，请参见[https://en.wikipedia.org/wiki/SSH](https://en.wikipedia.org/wiki/SSH "Wikipedia's page about SSH")。

```
NAMEssh - OpenSSH SSH client (remote login program)
```

最简单的例子

#### 在最简单的情况下，您可以使用如下语法连接到支持 ssh 的服务器:

注意:如果您附近没有可以访问的 ssh 服务器，您也可以使用自己的计算机作为服务器来尝试这个命令。为此，请将“yourserver”替换为“localhost”。当然，您的服务器应该替换为您想要连接的服务器的主机名或 ip 地址。

```
[pineehad@localhost ~]$ ssh yourserver
```

正如您在终端代码片段中看到的，我以 pineehad 的身份登录。如果您不指定用户名(我将在本教程的后面解释如何做)，SSH 将假设您希望使用当前登录的用户名登录。因此，在这种情况下，SSH 将尝试用户名 pineehad。当然，您需要确保服务器支持 ssh 连接。

ssh 客户端尝试连接到默认的端口 22。这意味着，如果您想要使用默认设置连接到远程主机，您应该确保端口 22(如果适用)被转发到您尝试连接的服务器。在本教程中，您将找到更多关于 SSH 端口的内容。

现在，回到我们运行的命令。如果服务器支持 ssh 连接，并且您可以通过端口 22 访问它，则应该提示您输入密码(如果这是您第一次尝试连接服务器，SSH 将首先询问您是否要继续连接，通常只需回答“是”)。如果您在此处键入密码，您将不会看到星号出现。不要惊慌，这是宋承宪的正常行为。这使得使用 ssh 连接更加安全，因为任何偶然的旁观者都无法看到密码的长度。

输入密码后，如果用户名和密码正确，您应该在服务器上运行 shell。如果没有，请确保您正在连接的服务器知道您应该能够使用您的用户名和指定的密码登录。您可以尝试连接到您自己的计算机(参见终端引用下面的注释),或者继续阅读以了解如何指定另一个用户名。尝试完 ssh shell 后，可以通过按 Ctrl + D 退出它。

指定用户名

## 指定不同的用户名其实很简单。你可能已经很熟悉它了。请参见以下示例:

以上将使 ssh 尝试使用用户名“yourusername”连接，而不是(在我的例子中)pineehad。许多其他协议也使用这种语法，所以了解它总是很方便的。

```
[pinehead@localhost ~]$ ssh yourusername@yourserver
```

顺便说一下，您仍然会被要求输入密码。出于安全原因，甚至不可能在语法中直接指定密码。除非您开始以高级方式配置服务器，否则您总是会被交互地询问(这正是该主题超出本教程范围的原因:本教程记录了如何使用客户机，而不是如何配置服务器)。

将 ssh 服务移动到另一个端口

## 将 ssh 服务转移到另一个端口有很多原因。其中之一是避免暴力登录尝试。某些黑客试图通过使用普通密码尝试许多普通用户名来访问 ssh 服务器(想想密码为“doe”的用户“john”)。

尽管这些黑客不太可能访问系统，但是暴力攻击的另一个方面是您通常希望避免的:系统和连接负载。暴力攻击通常在一秒钟内进行几十次甚至几千次，这不必要地降低了服务器的速度，占用了一些本可以更好地使用的带宽。

通过将端口更改为非默认端口，黑客的脚本将被拒绝，大部分带宽将被节省。由于 ssh 命令不能猜测端口，如果它不是默认的 22 端口，我们就必须指定它。你可以这样做:

当然，您必须用端口号替换“yourport”。这是 ssh 和 scp 在这一点上的重要区别。我将进一步解释它。

```
[pineehad@localhost ~]$ ssh -p yourport yourusername@yourserver
```

在远程服务器上运行命令

## 有时，尤其是在脚本中，您会想要连接到远程服务器，运行一个命令，然后再次退出。ssh 命令有一个很好的特性。您可以在选项 username 和 hostname 后指定命令。看看这个:

这将使服务器更新其搜索数据库。当然，这是一个非常简单的命令，没有参数。如果你想告诉别人你在网上读到的最新消息，该怎么办？你可能认为下面的话会给他/她传达这样的信息:

```
[pineehad@localhost ~]$ ssh yourusername@yourserver updatedb
```

然而，如果您运行这个命令，bash 会给出一个错误:

```
[pineehad@localhost ~]$ ssh yourusername@yourserver wall "Hey, I just found out something great! Have a look at www.examplenewslink.com!"
```

发生了什么事？Bash(你的 shell 后面的程序)试图解释你想给 ssh 的命令。这会失败，因为命令中有感叹号，bash 会将其解释为应该启动 bash 函数的特殊字符。

```
bash: !": event not found
```

但是我们不希望这样，我们只是希望 bash 把命令交给 ssh！有一个非常简单的方法可以告诉 bash 不要担心命令的内容，只需将它传递给 ssh 即可:用单引号将它括起来。看看这个:

单引号防止 bash 试图解释该命令，因此 ssh 接收该命令，不做任何修改，并可以将其发送给服务器。不要忘记单引号应该出现在整个命令中，而不是其他地方。

```
[pineehad@localhost ~]$ ssh yourusername@yourserver 'wall "Hey, I just found out something great! Have a look at www.examplenewslink.com!"'
```

SCP 和 SSH 的区别

## 与 ssh 不同，scp 不能用于在(远程)服务器上运行命令，因为它已经使用 ssh 的这个特性来启动主机上的 scp 服务器。scp 命令确实有一个接受程序的选项(-S 选项),但是这个程序将用于代替 ssh 来建立加密连接，并且不会在远程主机上执行。

技巧&使用 SCP 和 SSH 的技巧

## scp 的一个很方便的地方是它支持星号。您可以通过以下方式复制远程目录中的所有文件:

您也可以通过指定-r(递归)选项来复制整个目录:

```
[pineehad@localhost ~]$ scp yourusername@yourserver:/home/yourusername/* .
```

当复制到一个(远程)服务器或在一个(远程)服务器和另一个(远程)服务器之间复制时，这两种方法都有效。如果您不知道要用 scp 复制的文件的确切位置，ssh 命令就可以派上用场。首先，到(远程)服务器的 ssh:

```
[pineehad@localhost ~]$ scp -r yourusername@yourserver:/home/yourusername/ .
```

然后用 cd 浏览到正确的目录。这是必不可少的 Linux 终端知识，这里就不解释了。当您在正确的目录中时，您可以使用以下命令获得完整路径:

```
[pineehad@localhost ~]$ ssh yourusername@yourserver
```

*注意:pwd 是 Print Working Directory 的缩写，这是一种记忆命令的有用方法。*

```
[pineehad@localhost ~]$ pwd
```

然后，您可以复制这个输出，通过按 Ctrl + D 离开 ssh shell，然后在 scp 命令中粘贴完整的目录路径。这样就省去了很多记忆和打字！

您还可以限制 scp 在复制时可能使用的带宽。如果你想拷贝大量的数据，而又不想长时间受网速慢的困扰，这是非常有用的。限制带宽是这样实现的:

带宽以千比特/秒为单位。这是什么意思？八位是一个字节。如果您希望复制速度不超过 10 千字节/秒，请将该限制设置为 80。如果您希望复制速度不超过 80 千字节/秒，请将该限制设置为 640。明白了吗？您应该将该限制设置为您希望的最大千字节/秒的八倍。

```
scp -l bandwidthlimit yourusername@yourserver:/home/yourusername/* .
```

我建议您对其他人也需要使用的连接设置-l 选项。如果你使用集线器，大量的拷贝会阻塞整个 10 兆比特的网络。

提升您的云计算职业生涯

* * *

## 无论您是云新手还是专家，云专家都能让您轻松(而且非常棒)地获得认证并掌握现代技术技能。查看我们当前的 [**免费云课程**](https://acloudguru.com/blog/news/whats-free-at-acg) 或通过免费试用提升您的 [**云和 it 职业道路**](https://acloudguru.com/platform/training-paths) 。

最后的话

* * *

## 好吧，就是这样！我希望你学到了很多。当然，如果你忘记了什么，你可以再快速浏览一下这个教程。请告诉其他可能对本教程感兴趣的人，如果你这样做，你将有助于这个博客的发展=)。感谢您的阅读，并与您的新知识有很多乐趣！

Well, that was it! I hope you learned a lot. Of course, you can always have a quick look at this tutorial again if you forgot something. Please tell other people who might be interested about this tutorial, you’ll help this blog to grow if you do =). Thank you for reading and have a lot of fun with your new knowledge!