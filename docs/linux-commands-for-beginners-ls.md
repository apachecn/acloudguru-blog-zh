# 面向初学者的 Linux 命令:LS 

> 原文：<https://acloudguru.com/blog/engineering/linux-commands-for-beginners-ls>

对于你们中的一些人来说，这是一个基本的命令，你几乎一直在使用，如果这是你，那么这个教程不适合你。但是如果你是 Linux 新手或者刚刚接触命令行,“ls”是一个你会非常熟悉的命令。在表层，ls 是一个简单的命令，如果在任何目录或命令行的任何地方键入，它所做的只是列出当前工作目录的内容。但是如果我离开它，我不会帮你任何忙。事实上，我将告诉你一些关于 ls 的提示和技巧，如果你幸运的话，我们甚至可以提供一个 grep 命令！

*学习[如何一步一步制作《我的世界》服务器](https://acloudguru.com/course/creating-your-own-minecraft-server)！*

## LS–不仅仅是看上去的样子

LS 列出了当前工作目录的内容。如果你有一个只有几个文件的目录，这很简单，如果你有一个有成百上千个文件的目录，这就很难使用了。不仅如此，默认情况下 Linux 隐藏了所有以点(.)因为 Linux 把这些解释为配置文件，只有超级用户，或者真正知道自己在做什么的用户才应该定期看到这些。简单地在命令行上使用 ls 命令实际上不会显示这些点文件，如果您是 Linux 初学者，这可能会令人沮丧。以为你完事了？也许我们还有一些你没有想到的其他用例。例如，如果您希望列出所有文件扩展名为.的文件，该怎么办呢？txt？或者您可能只想列出所有目录，而不是单个文件？如果您需要将标准输出结果输出到文本文件呢？或者您是否需要查看大小细节、所有权细节、修改日期、权限以及兆字节格式的大小？见鬼，我们甚至可以列出位于我们刚刚列出的文件内部的所有文件(递归)！！如果你感到惊讶，不要担心，我们只需要看例子。你的外卖？了解 ls 命令只会让您走得更远，阅读手册页会让您走得更远，而本教程会让您走得更远。它会教你关于 ls 命令的一切吗？不，事实是这就是为什么 Linux 如此深入和灵活。如果你认为你已经做到了或者知道了，任何事情都有更多的方法，甚至是最简单的命令。这就是为什么 Linux 是服务器的首选操作系统，而 UNIX/Linux 在 90%的智能手机上都能找到(iOS 是 UNIX，Android 是 Linux)。不要让它吓倒你——它只会让你变得更聪明。

## 示例和使用案例

*   列出 Linux 目录中的所有文件，包括隐藏(点)文件和目录

> [anthony@linuxacademy.com $]ls-a

*   列出文件并显示权限、用户所有者、组所有者、上次修改/创建日期

> [anthony@linuxacademy.com $]l ls-l-l 代表“长列表”,它将向您展示所有对 Linux 系统重要的关于 Linux 文件的细节。

*   列出所有文件，以及目录中的所有文件(或者只是递归地列出文件夹

> [anthony@linuxacademy.com $]l ls-R

*   列出所有文件，按文件大小排序

> [anthony@linuxacademy.com $]l ls-S

> [anthony@linuxacademy.com $]l ls-d

*   人类可读–以 MB 或 GB 为单位的大小

> [anthony@linuxacademy.com $]ls-h

*   按文件扩展名的字母顺序排序

> [anthony@linuxacademy.com $]ls-X

## 现在让我们看看一些组合

*   以“人类可读格式”详细列出“所有”文件。

> [anthony@linuxacademy.com $]ls-alh

*   列出“所有”文件并将内容输出到文本文件

> [anthony@linuxacademy.com $]ls-a > contents . txt note:>将创建一个文本文件或覆盖现有文件>>如果文件存在，将追加到文件中，如果文件不存在，则创建文件。

*   列出“所有”文件，但只显示那些以结尾的文件。文本文件（textfile）

> [anthony@linuxacademy.com $]ls-a | grep *。文本文件（textfile）

## 还有更多，但从简单开始

看看 LS“man LS”的 man 文件，你会看到更多的选项。但是，冒着让您不知所措的风险，我刚刚创建了最常见的 LS 命令/标志的组合。这是给初学者的一个实用的使用指南，告诉我们如何经常使用 LS 命令。99%的情况下这将是你所需要的，如果你需要更多，那么你不是初学者，这个教程不适合你！[![Hands-On Linux Training](img/04e134a98ece57f278b7255f7c75d427.png)](https://linuxacademy.com/search/?categories)