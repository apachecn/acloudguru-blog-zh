# Salt 入门

> 原文：<https://acloudguru.com/blog/engineering/getting-started-with-salt>

任何对 DevOps 稍有兴趣的人可能都熟悉配置管理和各种可用于服务器大规模配置和编排的选项:Puppet、Chef、Ansible，当然还有 Salt。Salt 本身是一个基于 Python 的配置管理平台，它利用高速数据总线允许用户管理他们的基础设施。Salt 有两种风格:SaltStack Enterprise，它提供了一个管理 Salt 的图形界面 Salt Open，它从某些竞争对手中脱颖而出，因为它不限制您管理多少个爪牙。在本文中，我们将使用 Salt Open 来快速了解 Salt 的核心特性和功能。如果您正在考虑在未来的项目中使用 Salt，或者只是好奇 Salt 与其他“基础设施即代码”选项相比如何，那么这篇文章就是为您准备的。

## 启动测试环境

在这个演示中，我们将使用[流浪者](https://vagrantup.com)和[虚拟盒子](https://virtualbox.org)来设置一个基本的 Salt 环境。如果你不熟悉流浪者，看看[这篇文章](https://linuxacademy.com/blog/linux/vagrant-cheat-sheet-get-started-with-vagrant/)开始吧！此外，请确保为 Virtual Box 安装了来宾工具。导航到要存储 Salt 环境的目录。我们将使用 SaltStack 员工 David Boucha 提供的演示流浪环境，该环境位于 GitHub 库的[中。然后，克隆 Git repo:](https://github.com/UtahDave/salt-vagrant-demo)

```
$ git clone https://github.com/UtahDave/salt-vagrant-demo.git
```

进入提供的目录，然后启动流浪环境:

```
$ cd salt-vagrant-demo$ vagrant up
```

请注意，这可能需要几分钟的时间来调配流浪者环境。我们的环境有三台 Ubuntu 16.04 机器:一台 Salt Master(“Master”)和两台 guest(“minion 1”和“minion2”)。登录到主服务器:

```
$ vagrant ssh master
```

我们现在准备运行我们的第一个命令！

## 使用 Salt 进行编排

Salt 的主要功能之一是它可以用于编排——这意味着在多台计算机上运行一个命令，而不必登录每台计算机。Salt 通过使用**执行模块**来实现这一点。Salt】有一个很大的预制执行模块列表，但是你也可以使用 Python 自己制作。因为我们只是在试用 Salt，所以我们将使用一些预制的，看看它们是如何工作的。首先，让我们通过测试来看看命令结构，以确保我们的爪牙做出响应:

```
$ sudo salt '*' test.pingminion2:    Trueminion1:    True
```

正如我们所看到的，minion1 和 minion2 都报告了值“true”这意味着我们的服务器工作正常，并连接到我们的主服务器。但是，在我们进一步深入之前，让我们分解一下刚刚运行的命令: [![Salt breakdown](img/31a5018877dfad7eef9cbc45c1b9573e.png)](https://linuxacademy.com/site-content/uploads/2018/02/gs-salt-exmod.png)

*   `sudo`当然是给用户授予超级用户权限的 Linux 程序。
*   `salt`是主服务器上使用的 Salt 平台的主要命令。这个命令用于在我们所有的服务器上并行运行执行模块和状态(下面讨论)。
*   `'*'`是*的目标*。目标是*，在那里*我们可以运行我们的命令。我们可以通过 minion 名称、服务器事实(如操作系统)或正则表达式来确定目标。在我们的示例命令中，我们使用正则表达式“all”来定位我们的每一台服务器。
*   `test.ping`是执行模块本身。在这种情况下，它确保我们的服务器能够 *ping* ，或者回复我们的主服务器。执行模块也可以带参数，这些参数会出现在模块名之后，但是我们在这个例子中没有使用任何参数。

现在，让我们试试另一个。假设我们想在我们的 minion1 服务器上只安装 Apache *和*。我们将使用`pkg.install`模块:

```
$ sudo salt minion1 pkg.install apache2
```

注意，我们必须已经知道包的名字，在 Ubuntu 上是 *apache2* 。但是我们并不总是想要运行命令来更新一个插件。相反，我们经常想要描述某件事情的*结束状态*，并让我们添加的任何服务器使用这个蓝图来达到期望的状态。为此，我们需要盐。

## 使用盐状态

首先，让我们进入`/srv/salt`目录:

```
$ cd /srv/salt
```

如果我们看一看，我们可以看到已经有一个文件和目录在那里！

```
$ lscommon  top.sls
```

`top.sls`文件是我们想要在什么服务器上运行什么状态的映射。让我们来看看这里提供的一个:

```
$ cat top.slsbase:  '*':    - common
```

`base`是我们的主要环境，而`'*'`行——很像我们的执行模块示例——意味着这个行下面列出的所有内容都被添加到所有服务器。在这种情况下，将添加`common`州。但是什么是“共同”状态呢？进入`common`目录，列出可用文件:

```
$ cd common$ lsinit.sls  packages.sls
```

这里我们有两个以`.sls`结尾的文件；`.sls`表示它是一个状态文件。在这种情况下，`init.sls`文件是允许状态通过它们的目录名运行的文件(记住，在我们的`top.sls`文件中，我们称之为“公共”状态，这是我们整个目录的名称)。该文件列出了我们希望包含在状态中的任何附加文件。这个特定的`init.sls`文件调用`packages.sls`文件，后者安装 htop、strace 和 vim:

```
$ cat packages.slscommon_packages:  pkg.installed:    - pkgs:      - htop      - strace      - vim
```

正如我们所看到的，这个状态文件是用 YAML 语言编写的，这是 Salt 的默认配置语言。因此，让我们创建自己的状态文件。移回`/srv/salt/`目录，然后创建一个`users`目录，并移入这个新目录:

```
$ cd ..$ mkdir users$ cd users
```

让我们创建一个名为`fox.sls`的用户。使用您喜欢的文本编辑器，打开该文件并添加以下信息:

```
fox:  user.present:    - fullname: Fox Mulder    - home: /home/fox/    - shell: /bin/zsh/
```

但这意味着什么呢？让我们一行一行地看一下:

*   `fox:`:这是*参考 ID* ，意思是这个州的名字。稍后，当我们将这个文件添加到我们的用户的`init.sls`中时，我们将通过调用它“fox”来添加它；此外，由于这是 YAML 的姓名键，所以以冒号结尾。
*   这是我们的状态模块，这是一个预先配置好的状态，可以供 Salt 使用。在这个例子中，我们确保我们的用户(fox)在场。
*   `- fullname: Fox Mulder`:这里我们有了`user.present`状态的第一个参数。在这种情况下，我们确保用户的全名是“Fox Mulder”
*   `- home: /home/fox`:另一个参数，这个参数定义了我们用户的主目录。
*   最后一个参数，为我们的用户定义默认的 shell。

保存并退出文件。接下来，添加第二个文件`init.sls`，并添加以下内容来调用我们的`fox`状态:

```
include:  - users.fox
```

注意前缀`users.`。保存并退出。我们现在可以使用这些状态将*狐狸*用户添加到我们的爪牙中！我们可以通过两种方式做到这一点。首先，让我们使用`salt`命令将其手动添加到 minion1:

```
$ sudo salt minion1 state.apply users
```

或者，我们可以将我们的*用户*状态添加到`top.sls`文件中，然后运行一个*high state*——这意味着，Salt 将基于我们在`top.sls`文件中提供的映射运行我们的所有状态。回到`/srv/salt`目录，打开`top.sls`，添加`- users`:

```
base:  '*':    - common    - users
```

将更改应用到所有服务器:

```
$ sudo salt '*' state.apply
```

就是这样！你现在已经接触到盐了！您可以继续进一步试验，或者使用`exit`命令退出主服务器。要完全停止您的环境，运行`vagrant halt`。