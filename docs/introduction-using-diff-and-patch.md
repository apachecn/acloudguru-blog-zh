# 使用 Diff 和 Patch 的介绍

> 原文：<https://acloudguru.com/blog/engineering/introduction-using-diff-and-patch>

命令 diff 和 patch 形成了一个强大的组合。它们被广泛用于获得原始文件和更新文件之间的差异，这样，只有原始文件的其他人可以通过仅包含差异的单个补丁文件将它们转换成更新文件。本教程解释了如何使用这些伟大的命令的基础。

难度: ***中等**本教程假设一些基本的 Linux 和命令行知识，像改变目录、复制文件和编辑文本文件。*Linux 就业市场继续增长和扩大，我们的 [LFCS](https://acloudguru.com/course/linux-foundation-certified-system-administrator-lfcs) 课程将帮助你准备一个标准的行业 Linux 管理认证。

## 使用 diff 创建简单补丁

使用 diff 最简单的方法是获取两个文件之间的差异，一个原始文件和一个更新的文件。例如，您可以在普通文本文件中写几个词，进行一些修改，然后将修改后的内容保存到另一个文件中。然后，您可以使用 diff 比较这些文件，如下所示:

```
[rechosen@localhost ~]$ diff originalfile updatedfile
```

当然，用适合您的情况的文件名替换 originalfile 和 updatedfile。您很可能会得到如下输出:

```
1c1< These are a few words. No newline at end of file---> These still are just a few words. No newline at end of file
```

*注意:为了演示一个简单补丁的创建，我使用了文件 originalfile，其内容为“这是一些单词”文件 updatedfile 的内容是“这些仍然只是几个词。”。如果您想运行教程中的命令并获得相同的输出，您可以自己创建这些文件。1c1 是一种指示行号和指定应该做什么的方式。请注意，这些行号也可以是行范围(12，15 表示第 12 行到第 15 行)。“c”告诉 patch 替换这些行的内容。还有另外两个有意义的字符:“a”和“d”，“a”表示“添加”或“附加”，“d”表示“删除”。语法是(行号或范围)(c，a 或 d)(行号或范围)，尽管当使用“a”或“d”时，其中一个(行号或范围)部分可能只包含一个行号。*

*   当使用“c”时，它左边的行号是原始文件中应该被包含在补丁中的文本替换的行，它右边的行号是内容应该在文件的补丁版本中的行。
*   当使用“a”时，左边的行号可能只是单个数字，意味着在文件的补丁版本中添加行的位置，而它右边的行号是内容在文件的补丁版本中应该在的行。
*   当使用“d”时，它左边的行号是应该被删除以创建文件的修补版本的行，而右边的行号可能只是单个数字，告诉如果这些行没有被删除，它们在文件的修补版本中应该在哪里。您可能认为最后一个数字是多余的，但是请记住，补丁也可以以相反的方式应用。我将在本教程的后面对此进行更多的解释。

“”表示应该添加该符号后的字符。当替换内容时(行号之间有一个“c”)，您会看到两个< and the >符号。添加内容时(行号之间有一个“a”)，您只会看到>符号，而删除内容时(行号之间有一个“d”)，您只会看到

```
1c1< These are a few words.---> These still are just a few words.
```

你可能已经注意到了，我省略了解释 3 -的含义。它们指示应该被替换的行的结束和应该替换它们的行的开始。它们将旧线和新线分开。您只会在替换内容时看到这些内容(行号之间有一个“c”)。如果我们想创建一个补丁，我们应该把 diff 的输出放到一个文件中。当然，您可以通过从您的控制台复制输出，并在将其粘贴到您最喜欢的文本编辑器中后，保存文件来做到这一点，但有一种更短的方法。我们可以这样让 bash 将 diff 的输出写到一个文件中:

```
[rechosen@localhost ~]$ diff originalfile updatedfile > patchfile.patch
```

同样，用适合您情况的文件名替换文件名。您可能想知道，告诉 bash 使用>将命令的输出写入文件适用于所有命令。这对于将命令输出保存到(日志)文件非常有用。

## 应用我们创建的简单补丁

那么，我们刚才是不是创造了一个补丁？简短的回答是:是的，我们做到了。我们可以使用 patchfile 将 originalfile 的副本更改为 updatedfile 的副本。当然，在我们创建补丁的文件上应用补丁没有多大意义。因此，将原始文件和补丁文件复制到另一个地方，并转到那个地方。然后，尝试以这种方式应用补丁:

```
[rechosen@localhost ~]$ patch originalfile -i patchfile.patch -o updatedfile
```

同样，在必要的地方替换文件名。如果一切顺利，patch 刚刚创建的 updatedfile 文件应该与您最初用 diff 创建补丁时的文件相同。您可以使用 diff 的-s 选项对此进行检查:

```
[rechosen@localhost ~]$ diff -s updatedfile [/path/to/the/original/updatedfile]/updatefile
```

用原始更新文件的路径替换[和]之间的部分。例如，如果创建修补程序时使用的 updatedfile 位于当前目录的父目录中，请将“[/path/to/the/original/updated file]”替换为“..”(bash 将此理解为当前工作目录的父目录)。当然，也要在适当的地方替换文件名。恭喜你！如果 diff 报告文件相等，那么您就成功地创建并使用了一个补丁！然而，我们刚刚使用的补丁格式并不是唯一的。在下一章，我将解释另一种补丁格式。

## 上下文修补

在第一章中，我们使用 diff 的标准格式创建了一个补丁。然而，这种格式不提供任何围绕要被替换的行的上下文，因此，行号的改变(某处的一个或多个额外的换行符，或一些删除的行)将使补丁程序很难确定改为改变哪些行。此外，如果一个被意外修补的不同文件在正确的位置包含与原始文件相同的行，patch 会很高兴地将 patchfile 的更改应用到这个文件。这可能会导致代码崩溃和其他不必要的副作用。幸运的是，diff 支持普通格式之外的其他格式。让我们为相同的文件创建一个补丁，但是这次使用上下文输出格式:

```
[rechosen@localhost ~]$ diff -c originalfile updatedfile
```

到目前为止，应该很清楚应该在必要的地方替换文件名=)。您应该得到这样的输出:

```
*** originalfile        2007-02-03 22:15:48.000000000  0100--- updatedfile 2007-02-03 22:15:56.000000000  0100****************** 1 ****! These are a few words.--- 1 ----! These still are just a few words.
```

如您所见，文件名也包括在内。这将节省我们在应用补丁时的一些输入。您可以在文件名旁边看到的时间戳是文件最后一次修改的日期和时间。带 15 *的线表示一个大块的开始。一大块描述了应该对某个文本块进行哪些更改，如替换、添加和删除。这两个数字 1 是行号(同样，它们也可以是行范围(12，15 表示第 12 行到第 15 行))、和！意味着该线应该被替换。带 a 的线！在三个字母之前(嘿，我们以前在哪里见过？)第二行应该换成 a！，在三个-'s 之后(当然，the！本身不会被包括在内；这是上下文格式语法)。如你所见，这里没有 c，a 和 d。要执行的操作由该行前面的字符决定。的！如所解释的，意味着该行应该被替换。其他可用的字符有+、–和" "(空格)。+表示添加(或追加)，–表示删除，而“”表示什么也不做:补丁将只使用它作为上下文，以确保它正在修改文件的正确部分。应用这个补丁稍微容易一些:在与之前相同的情况下(让 bash 再次将 diff 输出写入一个文件，然后将补丁文件和原始文件复制到另一个位置)，您需要运行:

```
[rechosen@localhost ~]$ patch -i patchfile.patch -o updatedfile
```

您现在可能会想:为什么我们仍然需要指定新的文件名？嗯，那是因为补丁的目的是更新现有的文件，而不是创建新的更新文件。这通常在修补程序的源代码树时很方便，这是 patch 的主要用途。这就把我们带到了下一个主题:要修补整个源代码树，patchfile 中应该包含多个文件。下一章将讲述如何做到这一点。

## 获取多个文件之间的差异

获得多个文件之间的差异的最简单的方法是将它们都放在一个目录中，并让 diff 比较整个目录。您可以只指定目录而不是文件，diff 会自动检测您给它的是文件还是目录:

```
[rechosen@localhost ~]$ diff originaldirectory/ updateddirectory/
```

*注意:如果你比较的目录也包括子目录，你应该添加-r 选项让 diff 也比较子目录中的文件。*这将产生如下输出:

```
diff originaldirectory/file1 updateddirectory/file11c1< This is the first original file.---> This is the first updated file.diff originaldirectory/file2 updateddirectory/file21c1< This is the second original file.---> This is the second updated file.14d13< We're going to add something in this file and to delete this line.26a26> This is line has been added to this updated file.
```

注意:对于这个例子，我创建了一些示例文件。可以在这里下载包含这些文件的存档:[https://www . linuxtutorialblog . com/post/introduction-using-diff-and-patch-tutorial/diffpatchamplefiles . tar . gz](https://www.linuxtutorialblog.com/post/introduction-using-diff-and-patch-tutorial/diffpatchexamplefiles.tar.gz)*。*正如你所看到的，当比较多个文件时，正常的输出格式只指定文件名。您还可以看到添加和删除行的示例。现在，让我们来看看上下文格式的相同比较的输出:

```
diff -c originaldirectory/file1 updateddirectory/file1*** originaldirectory/file1     2007-02-04 16:17:57.000000000 +0100--- updateddirectory/file1      2007-02-04 16:18:33.000000000 +0100****************** 1 ****! This is the first original file.--- 1 ----! This is the first updated file.diff -c originaldirectory/file2 updateddirectory/file2*** originaldirectory/file2     2007-02-04 16:19:37.000000000 +0100--- updateddirectory/file2      2007-02-04 16:20:08.000000000 +0100****************** 1,4 ****! This is the second original file.SO--- 1,4 ----! This is the second updated file.SO****************** 11,17 ****CE- We're going to add something in this file and to delete this line.SO--- 11,16 ----****************** 24,28 ****--- 23,28 ----CE+ This is line has been added to this updated file.Something will be added above this line.
```

你应该注意的第一件事是长度的增加；上下文格式提供了比普通格式更多的信息。这在第一个例子中并不明显，因为没有包含任何上下文。然而，这一次有了背景，这无疑延长了补丁很多。您可能还注意到，文件名每次都被提到两次。这样做可能是为了让 patch 更容易识别何时开始修补下一个文件，或者是为了提供更好的向后兼容性(或者两者兼而有之)。让 diff 比较多个文件的另一种方法是编写一个 shell 脚本，多次运行 diff，并将所有输出正确地添加到一个文件中，包括带有 diff 命令的行。我不会告诉你如何做到这一点，因为另一种方法(把文件放在一个目录中)更容易，而且被广泛使用。用 diff 创建这个补丁相当容易，但是目录的使用带来了一个新的问题:patch 是只修补当前工作目录中提到的文件，而忘记它们在创建补丁时所在的目录，还是修补补丁中指定的目录中的文件？看看下一章就知道了！

## 修补多个文件

在这一章之前的章节中，我们创建了一个可以用来修补多个文件的补丁。如果您还没有这样做，请将 diff 的输出保存到一个实际的补丁文件中，如下所示:

```
[rechosen@localhost ~]$ diff -c originaldirectory/ updateddirectory/ > patchfile.patch
```

*注意:我们将在这里使用上下文格式补丁，因为使用提供上下文的格式通常是一种好的做法。*是时候尝试使用我们的补丁文件了。将原始目录和修补文件复制到另一个位置，转到该位置，并使用以下命令应用修补程序:

```
[rechosen@localhost ~]$ patch -i patchfile.patch
```

啊？它报告说找不到要修补的文件！是的，没错。它试图在当前目录中查找文件 file1(默认情况下，patch 会删除文件名前面的所有目录)。当然，这个文件不在那里，因为我们试图更新 originaldirectory 目录中的文件。因此，我们应该告诉 patch 不要删除文件名中的任何目录。可以这样做:

```
[rechosen@localhost ~]$ patch -p0 -i patchfile.patch
```

*注意:您可能认为您也可以移动到 originaldirectory 并在那里运行 patch 命令。不要！这是一种不好的做法:如果 patchfile 在子目录中包含任何要修补的文件，patch 将在工作目录中查找它们，显然，找不到它们或者找到错误的文件。使用-p 选项使修补程序在子目录中正常运行。*-p 选项告诉 patch 应该在文件名前去掉多少斜线(包括它们前面的内容，通常是目录)(注意，在我们的例子中，当使用-p0 选项时，patch 在 originaldirectory 和 updateddirectory 中查找要修补的文件)。在这种情况下，我们将其设置为 0(不删除任何斜杠)，但您也可以将其设置为 1(删除第一个斜杠及其之前的所有内容)，或 2(删除前两个斜杠及其之前的所有内容)，或任何其他数量。如果你有一个使用不同目录结构的补丁，这将非常有用。例如:如果您有一个使用如下目录结构的补丁:

```
(...)*** /home/username/sources/program/originaldirectory/file1     2007-02-04 16:17:57.000000000 +0100--- /home/username/sources/program/updateddirectory/file1      2007-02-04 16:18:33.000000000 +0100(...)
```

您可以只计算斜线(/(1)home/(2)username/(3)sources/(4)program/(5))并使用-p 选项给出该值。如果使用-p5，patch 会同时查找 originaldirectory/file1 和 updateddirectory/file1。请注意，补丁将两个相邻的斜杠(如/home/username//sources)视为一个斜杠。这是因为脚本有时(不管是不是偶然)会在目录之间多加一条斜线。

## 反转已应用的补丁

有时应用了不该应用的补丁。比如:一个补丁在某些代码中引入了一个新的 bug，发布了一个修复的补丁。然而，您已经应用了旧的、有缺陷的补丁，并且您想不出快速的方法来再次获得原始文件(可能它们已经被打了几十次补丁)。然后，您可以用一种可逆的方式应用有缺陷的补丁。patch 命令将尝试通过交换块来撤消它所做的所有更改。您可以通过向 patch 传递-R 选项来告诉它尝试反转:

```
[rechosen@localhost ~]$ patch -p0 -R -i patchfile.patch
```

通常，此操作会成功，并且您会得到您拥有的原始文件。顺便说一句，还有另一个你想要反转补丁的原因:有时(特别是在困倦的时候)，人们发布一个交换了文件的补丁。你有一个很大的机会，补丁将自动检测到这一点，并询问你是否希望它尝试修补可逆。但是，有时 patch 会检测不到它，并怀疑为什么文件似乎不匹配。然后，您可以通过将-R 选项传递给 patch，尝试以相反的方式手动应用补丁。这是一个很好的做法，在你尝试之前做一个备份，因为有可能补丁弄糟了，给你留下不可恢复的损坏文件。

## 统一格式

diff 命令还可以用另一种格式输出差异:统一格式。这种格式更加紧凑，因为它省略了冗余的上下文行，并对行号指令等内容进行了分组。不过目前只有 GNU diff 和 patch 支持这种格式。如果你以这种格式发布补丁，你应该确保它只被 GNU 补丁用户应用。几乎每个 Linux 版本都有 GNU 补丁。统一格式类似于上下文格式，但远非完全相同。您可以通过以下方式创建统一格式的修补程序:

```
[rechosen@localhost ~]$ diff -u originaldirectory/ updateddirectory/
```

输出应该是这样的:

```
diff -u originaldirectory/file1 updateddirectory/file1--- originaldirectory/file1     2007-02-04 16:17:57.000000000 +0100+++ updateddirectory/file1      2007-02-04 16:18:33.000000000 +0100@@ -1 +1 @@-This is the first original file.+This is the first updated file.diff -u originaldirectory/file2 updateddirectory/file2--- originaldirectory/file2     2007-02-04 16:19:37.000000000 +0100+++ updateddirectory/file2      2007-02-04 16:20:08.000000000 +0100@@ -1,4 +1,4 @@-This is the second original file.+This is the second updated file.SO@@ -11,7 +11,6 @@CE-We're going to add something in this file and to delete this line.SO@@ -24,5 +23,6 @@CE+This is line has been added to this updated file.Something will be added above this line.
```

如您所见，行号/范围被分组并放在@ '之间。另外，在+或-之后没有多余的空格。这样可以节省一些字节。另一个区别是:统一格式没有特殊的替换标志。它只是删除了旧的行(–号),并添加了修改过的行(+号)。添加/删除和替换之间的唯一区别在于行号/范围:当替换一行时，它们是相同的，而当添加或删除时，它们是不同的。

## 格式对比

阅读了三种格式后，您可能想知道选择哪一种。这里有一个小对比:

*   正常格式具有最好的兼容性:几乎每个 diff/patch-like 命令都应该识别它。然而，缺乏上下文是一个很大的缺点。
*   上下文格式得到了广泛的支持，尽管不是每个 diff/patch-like 命令都知道它。然而，能够包含上下文的优势弥补了这一点。
*   统一格式也以上下文为特征，并且比上下文格式更紧凑，但是只受一种 diff/patch 类命令的支持。

如果你确定这个补丁只被 GNU diff/patch 用户使用，unified 是最好的选择，因为它尽可能的保持你的补丁的紧凑。然而，在大多数其他情况下，上下文格式是最好的选择。只有当您确定有一个用户不支持上下文格式时，才应该使用普通格式。

## 改变上下文行数

可以使 diff 在应该更改的行周围包含更少的上下文行。特别是在大的补丁文件中，这可以去掉很多字节，使你的补丁文件更容易移植。但是，如果包含的上下文行太少，补丁可能无法正常工作。引用 GNU diff 手册页:“为了正确操作，patch 通常至少需要两行上下文。”可以通过多种方式指定上下文行数:

*   If you want to use the context format, you can combine it into one option, the -C option. Example:

    ```
    [rechosen@localhost ~]$ diff -C 2 originaldirectory/ updateddirectory/
    ```

    上面的命令将使用带有 2 个上下文行的上下文格式。

*   If you want to use the unified format, you can combine it into one option, the -U option. Example:

    ```
    [rechosen@localhost ~]$ diff -U 2 originaldirectory/ updateddirectory/
    ```

    上述命令将使用具有 2 个上下文行的统一格式。

*   Regardless which format you choose, you can specify the number of lines like this:

    ```
    [rechosen@localhost ~]$ diff -2 originaldirectory/ updateddirectory/
    ```

    但是，这只有在您还指定了上下文支持格式的情况下才有效。您必须将该选项与-c 或-u 结合使用。

### 让我们开始您的云之旅

希望获得认证或提升您的云计算职业生涯？通过 ACG 的课程、实验室、学习路径和[沙盒软件](https://acloudguru.com/platform/cloud-sandbox-playgrounds)学习按需云技能。

## 最后的话

尽管本教程描述了 diff 和 patch 的许多特性和工作方式，但它并没有描述使用这些强大的工具可以做的所有事情。它是以教程的形式介绍的。如果你想了解更多关于这些命令的信息，你可以阅读它们的联机帮助页和关于 diff 和 patch 的 GNU 文档。那么，我希望这篇教程对你有所帮助。感谢您的阅读！如果你喜欢这个教程，浏览这个博客，看看是否有更多你喜欢的。请在这里和那里留下链接来帮助这个博客发展，并让其他人从这个网站不断增长的知识中受益。提前感谢，祝修补愉快！