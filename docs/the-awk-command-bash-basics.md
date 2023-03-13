# 在 Linux 上的 Bash 中使用 AWK 命令

> 原文：<https://acloudguru.com/blog/engineering/the-awk-command-bash-basics>

当我刚开始做系统管理员时，我想知道 ***如何获得晋升*** ，有人告诉我，我需要知道 [BASH](https://acloudguru.com/blog/engineering/tutorial-the-best-tips-tricks-for-bash-explained) 实用程序，比如 AWK。Linux 就业市场继续增长和扩大，我们的 [LFCS](https://acloudguru.com/course/linux-foundation-certified-system-administrator-lfcs) 课程将帮助你准备一个标准的行业 Linux 管理认证。

我不确定 AWK 是否真的是一个实用程序——当阿尔弗雷德·艾侯、彼得·温伯格和布莱恩·柯尼根在贝尔实验室编写它时，它原本是一种数据驱动的编程语言。名字来源于他们姓氏的首字母，但是我们在 Linux 上 BASH 用的程序是(G)AWK 或者 Gnu AWK，还有很多衍生。

## **你能用 AWK 命令做什么？**

既然我们已经解决了这些琐事，那么我们能对 AWK 做些什么呢？只需在命令提示符下输入`awk`就可以调用 AWK。在命令行上，都是小写。

**AWK 最常用于处理文件。** AWK 处理一个条件，如果提供了一个条件，然后采取行动。默认操作是打印满足条件的任何内容。在文件中搜索正则表达式模式匹配:

```
 awk ‘/regex/’  /etc/passwd 
```

这将导致来自`/etc/passwd`文件的匹配行被打印到命令行。这是相当基本的，我们使用打印匹配的默认行为。

**AWK 也可以用来搜索数据列，干净利落地输出信息。**了解特定服务是否正在运行，如果找到则显示名称:

```
 ps -ax | awk ‘/systemd/ {print $5}’
```

关于`awk`的一个好处是它标记了输入其中的行。这意味着对于有分隔符的项目，您可以选择一列。您可以在命令行上指定字段分隔符。

一个例子是打印来自`/etc/passwd`的用户列表，条目由冒号(`:`)分隔，用户名在第一列。记住`$0`是整条线。

```
 awk -F: ‘{print $1}’ /etc/passwd
```

## **让 AWK 工作的例子**

这很好，但我们想和 AWK 一起工作，对吗？所以，如果你有一个目录(我们用`/etc`来表示这个目录)并且想知道这个目录的大小:

```
 ls -l /etc | awk ‘{x += $5} END {print “total bytes:” x}'
```

这里，我们获取`ls -l`命令的输出，并将每一行添加到变量`x`，因为 AWK 的变量被初始化为`0`，第五列是文件大小，当我们解析输出时，我们将每个文件的大小添加到`x`。

`END`关键字表示输入解析完成后我们想要采取的动作。在这种情况下，我们打印`x`的值。以千字节为单位，我们将结果`x`除以 1024:

```
 ls -l /etc | awk ‘{x += $5} END {print “total Kilobytes:” (x/1024)}
```

## AWK 作为一种完整的脚本语言

AWK 也可以作为一种完整的脚本语言，你可以在命令行上使用`-f`标志向它传递脚本文件。

**从哪里开始** :正如我在开头所说的，命令行的使用是求职面试中人们与其同时代人的真正区别。公司对自动化和一切代码感兴趣。这从[了解 BASH shell 脚本](https://acloudguru.com/course/the-system-administrators-guide-to-bash-scripting)的条件及其所有特性开始。

如果你想让自己与众不同，并显示出你对自己正在做的事情感到满意，你可以考虑看一看[Bash 脚本管理指南](https://acloudguru.com/blog/engineering/conditions-in-bash-scripting-if-statements)。这将带您到一个地方，在那里您可以真正地用命令行显示您的舒适程度。

* * *

## 提升您的云计算职业生涯

无论您是云新手还是经验丰富的专家，云专家都能让您轻松(而且非常棒)地获得认证并掌握现代技术技能。查看 ACG 目前的免费课程或立即开始免费试用。

* * *

### 想要更多云技术的好处吗？看看这些: