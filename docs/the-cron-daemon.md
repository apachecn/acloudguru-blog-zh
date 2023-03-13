# Cron 守护进程

> 原文：<https://acloudguru.com/blog/engineering/the-cron-daemon>

## 使用 Cron 在 Linux 上调度周期性任务

Cron 是一个守护进程，用于调度你能想到的任何类型的任务。发送有关系统或程序统计数据的电子邮件、定期进行系统维护、制作备份或执行任何您能想到的任务都很有用。其他操作系统上也有类似的程序。在 Mac OS X 上，cron 已经被另一个名为 launchd 的守护进程所取代。在 Windows 上，你有一个恰如其分的名字“任务调度程序”。如果你渴望 Linux 的 GUI，基于 Gnome 的系统如 Ubuntu，包括 Gnome Schedule，它是 cron 的一个很好的前端。

## Cron 守护进程，Crond

## cron 守护进程使用 crontab 文件来指定运行什么任务以及何时运行。这些文本文件指定在特定时间间隔运行的命令。每个用户都可以拥有自己的 crontab 文件。还有系统范围的 crontab 文件，用于用户之间的协作或共享。cron 守护进程将检查存储在 var/spool/cron 中的用户 crontab 文件，以及存储在*/etc/crontab*&*/etc/cron . d*中的系统范围的 crontab 文件，它每分钟都会唤醒来执行此操作。

Crontab

## Crontab 是用于列出 cron 守护进程使用的表的命令。我们也将用于加载 cron 守护进程的文件称为 crontab 文件。当我们使用*crontab–e*命令时，我们正在编辑 */var/spool* 中的 crontab。这里的文件是不同的格式，不应该直接编辑。编辑 crontab 文件也称为创建 Cron 作业让我们从编辑我们自己的用户 Crontab 文件开始:`klack@:~$ crontab -e`

第一次尝试编辑 crontab 文件时，我们会被要求选择一个编辑器。Nano 被认为是最简单的编辑器。继续，通过输入 2 选择 nano。Crontab 现在将创建 crontab 文件的临时副本，并在 nano 中打开它进行编辑。nano 启动时，重复按 Ctrl-V 向下滚动到文件底部。您现在应该在新的一行上准备输入我们的第一个 cron 命令。

```
no crontab for klack - using an empty one< Select an editor.  To change later, run 'select-editor'.1\. /bin/ed<2\. /bin/nano        <---- easiest4\. /usr/bin/vim.tinyChoose 1-4 [2]: 2
```

Crontab Format

## crontab 文件中的每一行都可以是一个变量定义或 cron 命令。不要忘记按回车键，用换行符结束最后一个命令。你也可以用%结束最后一句话。这是导致命令失败的最常见错误，在这种情况下，不会显示错误。Cron 命令有一个独特的模式，允许您指定自定义的重复时间。有五个字段用于指定运行的时间和命令。

Crontab Examples

```
(Minute 0-59) (Hour 0-23) (Day of Month 1-31) (Month 1-12) (Day of week 0-7) (Command)
```

## 这里有几个在不同时间间隔运行备份脚本的示例:`0 5 1 * * ~/backup-home.sh`我们在这里指定的是在每月的第一个^日早上 5:00 运行 backup-home.sh 脚本。*表示通配符。在本例中，任务在一周中的所有月份和任何一天运行。`0 5 1,15 * * ~/backup-home.sh`在这个修改后的示例中，我们在月份字段中使用了一个逗号来表示我们希望这个任务在每月的 1 号^(1 号)和 15 号^(12 号)运行。`0 5 1 12/3 * ~/backup-home.sh`在本例中，12/3 代表一个步长值。这意味着该命令将在每个季度的 1 号^(1 号)早上 5 点运行。`* 17-20 * * * ~/backup-home.sh`在这里，该备份脚本将在每天的 17、18、19 和 20 小时运行。`* * * * * ~/backup-home.sh`这个例子将每分钟运行一次。如果你认为你必须使用这个，请小心！`*/2 * * * * ~/backup-home.sh`结合这里的一些想法，这个命令包含一个步长值，每两分钟运行一次。这里我们使用了一个特殊的时间含义@reboot 将在每次重启后运行一次。您还可以使用其他特殊的时间关键字。以下是完整列表:

当你输入完预定的命令后，按下 **Ctrl-W** 和 **enter** ，将文件保存在 nano 中。然后按下 **Ctrl-X** 退出。Crontab 现在将检查文件中的错误。如果没有发现错误，那么 cron 守护进程使用的表将被更新，更改将立即生效。

```
@reboot     :    Run once after reboot.@yearly     :    Run once a year@annually   :    Run once a year@monthly    :    Run once a month@weekly     :    Run once a week@daily      :    Run once a day@hourly     :    Run once an hour
```

每小时一次，每天一次，每周一次，每月一次

## 为了方便使用 cron 作业，只需在/etc/中的这些目录中创建一个文件，任务将根据它所在的文件夹运行。然而，这样做让你对时间的控制更少(一周中的什么时候？肯定是某个时候)。

克朗。允许和 cron。否认

## 这些文件可能位于/etc 中，它们控制谁可以使用 crontab 命令。如果 cron.allow 存在，那么只有其中列出的用户(每行一个用户)可以运行 crontab。如果 cron.allow 不存在，则任何用户都可以拥有 crontab 文件，cron.deny 中列出的用户除外。如果这两个文件都不存在，则需要超级用户权限才能拥有用户 crontab 文件。

系统范围的 Crontab 文件

## 在较大的用户环境中，编辑/etc/crontab 或/etc/cron.d/中的文件可能更有好处。这些文件也由 cron 守护进程加载。在较大的用户环境中，协作用户可能希望在一个中心位置存储和查看所有 crontab 文件。/etc/crontab 是一个单独的文件，它包含一个额外的字段，即用户字段。这个系统 crontab 条目将以 root 用户身份运行。可以在/etc/cron.d/目录中创建任何名称的文件。许多软件包使用这个目录，因为它提供了更好的组织。

把一切都包起来

## 到目前为止，您应该能够通过脚本和 cron 守护进程(也称为 cron 作业)的组合来运行您能想到的任何任务。欢迎在下面的评论中留下任何问题。Linux Academy 成员可以在此观看讲师指导视频[。](https://linuxacademy.com/cp/lessons/lesson/course/2/lesson/6)

By now you should be able to run any task you can think of with the combination of scripts and the cron daemon (also called cron jobs).  Feel free to leave any questions in the comments below.  Linux Academy members can view instructor led video [here](https://linuxacademy.com/cp/lessons/lesson/course/2/lesson/6).