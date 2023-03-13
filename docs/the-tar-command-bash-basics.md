# TAR 命令| Bash 基础知识

> 原文：<https://acloudguru.com/blog/engineering/the-tar-command-bash-basics>

![](img/13e67874d50aab13e6edbdcc285e3763.png)我正坐在[埃尔·马尔克斯](https://linuxacademy.com/blog/docker/its-okay-to-be-new/?utm_source)在[西北](https://www.linuxfestnorthwest.org/conferences/2019)Linux 节上做报告，在她的报告开始时，有一个[漫画](https://xkcd.com/1168/)。在这幅漫画中，它表明，要拆除炸弹，你必须能够输入一个焦油命令，而不用谷歌搜索。当然都是注定的。由于我们已经介绍了一些可以用 [AWK](https://wpengine.linuxacademy.com/linux/the-awk-command-bash-basics/?utm_source) 和 [SED](https://wpengine.linuxacademy.com/linux/the-sed-command-bash-basics/?utm_source) 以及[导航](https://wpengine.linuxacademy.com/linux/navigating-in-bash-bash-basics/?utm_source)和[事件指示器](https://wpengine.linuxacademy.com/linux/event-designators-bash-basics/?utm_source)完成的很酷的技巧，这一次，我们将确保在使用[磁带存档](https://linux.die.net/man/1/tar)命令时，您能够拯救世界。如果你熟悉 ZIP，那么你也会熟悉 TAR。基本上，这是用来归档文件到一个单一的，希望是更小的，文件。有时你会听到这些被称为[【tarball】](https://whatis.techtarget.com/definition/tarball-tar-archive)。

### **找出 TAR 存档中的内容**

因此，通常情况下，当您收到一个“tarball”时，您可以去获取它，然后将它提取到您的系统中。这就提出了问题，文件将在哪里创建，将创建什么？我们可以检查`.tar`文件以确定其中的内容。请记住，当我们使用 TAR 时，我们希望它是 **V** erbose，所以我们添加了`v`标志，这样我们就可以看到它在做什么。在列出档案内容的情况下，添加`verbose`或`v`与通过添加`-l`在`ls`命令中请求长列表是一样的。

```
tar --list --verbose --file <name of file here>
```

好了，现实点吧，没人这么做；如果您阅读了手册页并决定键入所有内容，它看起来会是这样。我很懒，喜欢用最少的打字量来完成工作。你在这里看到的和这个一样:

```
tar -tvf <name of file here>
```

这里唯一奇怪的是`--list`被`-t`代替，然后我们可以将所有的标志添加到同一个`-`语句中。这意味着对于其余的例子，我将向你展示简写，你可以决定你想怎么做。现在让我们来看一些实际的输出。

```
$ tar -tvf ./example.tar drwxr-xr-x 0 mmcclaren staff  0 May 2 14:37 ./example/ -rw-r--r-- 0 mmcclaren staff  210 May 2 14:23 ./example/._examplefile1 -rw-r--r-- 0 mmcclaren staff  899 May 2 14:23 ./example/examplefile1 -rw-r--r-- 0 mmcclaren staff  210 May 2 14:23 ./example/._examplefile2 -rw-r--r-- 0 mmcclaren staff  15033 May 2 14:23 ./example/examplefile2 -rw-r--r-- 0 mmcclaren staff  210 May 2 14:23 ./example/._examplefile3 -rw-r--r-- 0 mmcclaren staff  14957 May 2 14:23 ./example/examplefile3 
```

在这种情况下，我们可以看到所有的示例文件都包含在一个示例目录中。这意味着当我们提取它时，我们将在输出中得到那个目录。如果路径只有文件，而没有包含目录，那么文件将最终位于您所在的目录中，除非您指定了提取点。

### **提取一个焦油档案**

现在我们知道了里面有什么，我们想把它弄出来。这是运行 e **X** tract 标志和 **F** ile 标志的问题。记住，我们可以添加 **V** erbose 标志，这样我们就可以看到它正在做什么。

```
 $ tar -xvf ./example.tar   x ./example/  x ./example/._examplefile1  x ./example/examplefile1  x ./example/._examplefile2  x ./example/examplefile2  x ./example/._examplefile3  x ./example/examplefile3 
```

在本例中，我们将文件提取到示例目录中。

```
 $ ls -l ./example  total 72  -rw-r--r--@ 1 mmcclaren staff 899 May 2 14:23 examplefile1  -rw-r--r--@ 1 mmcclaren staff 15033 May 2 14:23 examplefile2  -rw-r--r--@ 1 mmcclaren staff 14957 May 2 14:23 examplefile3 
```

如果我们想要指出我们想要将归档文件提取到哪里，这将需要添加-C 标志和一个位置作为参数。可以认为这是将提取的文件“复制”到指定的位置。

```
 $ tar -xvf ./example.tar -C ./location  x ./example/  x ./example/._examplefile1  x ./example/examplefile1  x ./example/._examplefile2  x ./example/examplefile2  x ./example/._examplefile3  x ./example/examplefile3  $ ls -l ./location  total 0  drwxr-xr-x 5 mmcclaren staff 160 May 2 15:08 example 
```

我想说的最后一件事是只从存档中提取一个文件。如本例所示，这采用了`tar -xf ( archive name ) ( file name )`的形式。

```
 $ tar -xvf ./example.tar ./example/examplefile2  x ./example/examplefile2  $ ls  example example.tar location  $ ls ./example  examplefile2 
```

### **创建档案**

咻，这是一个长的！但是，我们不能在不知道如何创建归档的情况下离开。最简单的方法是将 TAR 指向一个目录，并使用`-c`标志来创建 **C** ,格式如下:

```
tar -cf <name of archive> <directory to archive>
```

我们一直使用的示例归档文件就是这样创建的:

```
 $ tar -cvf example.tar example  a example  a example/examplefile1  a example/examplefile2  a example/examplefile3  $ tar -tf ./example.tar   example/  example/._examplefile1  example/examplefile1  example/._examplefile2  example/examplefile2  example/._examplefile3  example/examplefile3 
```

最后一件事:让我们将一个文件添加到现有的归档文件中。`-r`标志用于追加到目录中，其语法与“create”相同；归档文件的名称，然后是文件的名称。

```
$ tar -rf example.tar examplefile4 $ tar -tf example.tarexample/example/._examplefile1example/examplefile1example/._examplefile2example/examplefile2example/._examplefile3example/examplefile3examplefile4
```

如您所见，`examplefile4`被添加到我们一直使用的前一个归档文件中。

### 我不敢相信我读完了整本书！

我知道这是一篇疯狂的长文，但是如果你想更深入地了解 TAR 命令，请查看位于 [Linux 学院](https://linuxacademy.com/?utm_source)的 [LPI Linux 基础知识](https://linuxacademy.com/linux/training/course/name/lpi-linux-essentials?utm_source)。如果你想了解更多，请前往[报名参加为期 7 天的免费试用](https://linuxacademy.com/pricing?utm_source)，看看#1 边做边学培训平台如何帮助你提高技能。我们还有一个[免费社区版](https://linuxacademy.com/join/community?utm_source)并提供最好的[实践学习](https://linuxacademy.com/features/labs_exercises?utm_source)培训！直到下次，继续学习！