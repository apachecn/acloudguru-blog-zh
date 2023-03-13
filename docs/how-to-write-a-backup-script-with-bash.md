# 如何使用 Bash 编写备份脚本

> 原文：<https://acloudguru.com/blog/engineering/how-to-write-a-backup-script-with-bash>

Linux 系统管理员经常有许多手动任务需要日常处理。让这些工作变得更容易的一个方法是自动化。Bash 脚本是一种灵活而简单的方法，可以利用您现有的命令行知识来自动化您经常运行的任务，并且以其他管理员可以合理地帮助维护的方式来实现。例如，让我们一起来看一个备份脚本。

自从 shells 出现以来，Bash 脚本就一直存在。理解其中的原因非常简单:自动化使管理员的工作变得更容易。说真的，谁想让自己的工作变得更难呢？

*What’s in store for Linux in 2021? Check out [Linux This Month](https://acloud.guru/series/linux-this-month) for that and all the latest in all things Linux.*

首先，我想说清楚，我的方法不是完美的、没有改进余地的、必须这样做的方法。我的脚本清晰易读，易于维护，但它们不是做事的唯一方式。

让我们来看看下面的脚本:

```
https://raw.githubusercontent.com/linuxacademy/the-system-admin-guide-to-bash-scripting/master/backup-blog.sh
```

第一部分是这样开始的:

```
-----
#!/bin/bash

#####
# This is a script given to users on a machine when they want to back 
# up their work to a specific backup directory (/home/$USER/work_backup)
# 
# The script requires two parameters - the first is where the log file 
# will be and the second is what directory will be backed up.
#####
-----
```

本质上要求 shebang 是第一行。它让 shell 知道我们将使用什么二进制文件来执行下面的代码。(例如，如果您要编写一个 python 脚本，将 python 二进制文件的路径放在那里是合适的)。

下一部分是一些完全被注释掉的文本，所以 shell 不会将其解析为代码(行首的#)。我用那个区域来解释脚本做什么，以及是否有任何参数需要传递给脚本。

```
-----
if [ -z "$1" ] || [ -z "$2" ]; then
	echo "You have failed to pass a parameter."
	echo "Reminder that all required files will be copied to /home/\$USER/work/work_backup."
	echo "USAGE: ./backup.sh LOGFILE DIRECTORY-TO-BACKUP"
	exit 255;
fi

MYLOG=$1
BACKUP_FROM=$2
-----
```

在这里，我们验证是否传递了所需的参数——如果没有，则使用一些用法信息退出脚本。之后，我们可以将参数赋给名字更有意义的变量。毕竟，如果您的脚本只有几百行，您是否愿意记住日志文件变量叫做 MYLOG 或 1？

这不是处理参数的唯一方法，但却是最简单的方法。对于这个简短的剧本来说，我认为这是完全合适的。你怎么想呢?

```
-----
function ctrlc {
	rm -rf /home/$USER/work/work_backup
	rm -f $MYLOG
	echo "Received Ctrl+C"
	exit 255
}

trap ctrlc SIGINT
-----
```

在这一部分，我们会问这样一个问题“如果有人试图在脚本运行时取消它，我们该怎么办？”当用户点击 Ctrl+C 时，脚本将捕获该信号并运行我们的函数，该函数将撤销到目前为止所做的所有工作，并确保用户知道脚本意外停止的原因。

```
-----
echo "Timestamp before work is done $(date +"%D %T")" >> $MYLOG

echo "Creating backup directory" >> $MYLOG
if ! (mkdir /home/$USER/work/work_backup 2> /dev/null)
then
	echo "Directory already existed." >> $MYLOG
fi
-----
```

在这里，我们确保在开始工作时进行日志记录，因为日志记录对于故障排除至关重要。如果您的系统日志在上午 10:30 开始出现磁盘错误，而您的脚本在上午 10:31 开始运行并生成错误，这可能不是脚本的错。

接下来，我们创建要将文件复制到的目录。我们使用 if 语句来实现这一点，该语句表示“如果我们未能创建目录，它将

因为它已经存在。“如果我们在一个没有权限创建目录/文件的地方运行脚本，可能会出现问题，这当然是该脚本可以改进的地方，但该设置将正常使用。

```
-----
echo "Copying Files" >> $MYLOG
cp -v $BACKUP_FROM/* /home/$USER/work/work_backup/ >> $MYLOG
echo "Finished Copying Files" >> $MYLOG
echo "Timestamp after work is done $(date +"%D %T")" >> $MYLOG
-----
```

最后，我们到达大部分工作发生的地方。首先，我们记录我们将要实际做的工作，然后运行我们的 copy 命令。至于对该脚本的潜在改进，您可以用一个循环来替换它，该循环将重命名所有文件，或者添加"-backup "标记、文件复制的日期等等。然而，在大多数情况下，这种方法就足够了。

完成后，我们记录我们完成的工作，然后记录时间戳—同样，这有助于故障排除。

就是这样！感谢你阅读这篇文章，并和我一起关注我写剧本的思考过程。从长远来看，使用 Bash 编写脚本并自动化常见任务可以(并且将会)节省时间。您可以随意使用这个脚本，并根据需要进行修改。

### 查看系统管理员的 Bash 脚本指南

想学习更多关于 Bash 脚本的技巧和诀窍吗？看看我新发布的课程[Bash 脚本的系统管理员指南](https://acloudguru.com/course/the-system-administrators-guide-to-bash-scripting)。我很乐意成为你学习冒险的一部分。

有问题吗？欢迎[联系我](https://www.linkedin.com/in/rob-marti-541230b/)！

* * *

## 提升您的 Linux 知识水平

通过接触云专家来学习 Linux 技能。看看为什么我们 85%的学习者说他们通过做能记住更多。