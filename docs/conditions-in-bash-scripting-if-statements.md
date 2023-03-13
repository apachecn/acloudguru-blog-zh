# Bash If 语句和脚本——Linux 备忘单

> 原文：<https://acloudguru.com/blog/engineering/conditions-in-bash-scripting-if-statements>

如果你使用 [bash 来编写](https://acloudguru.com/course/the-system-administrators-guide-to-bash-scripting-2)脚本，你无疑将不得不大量使用条件，例如一个 *if … then* 构造或者一个 *while* 循环。学习和使用这些条件的语法似乎有点令人生畏。本教程旨在帮助读者理解 bash 中的条件，并提供了一个全面的可能性列表。假设有少量的一般 shell 知识。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

难度: ***基础–中等***

## 什么是 Bash 脚本？

在我们开始之前，让我们确保我们都在同一页上。什么是 Bash 脚本？思考 Bash 脚本的一个简单方法是将它们想象成电影脚本。他们告诉演员在什么时候说什么，对吗？Bash 脚本告诉 Bash 在什么时候做什么。

Bash 脚本是一个简单的文本文件，包含一系列我们希望自动运行而不是手动运行的命令。

要记住的一件事很容易忘记:当编写自己的 Bash 脚本时，在我们试图调整脚本之前，必须记住设置文件的 execute 位。

### Bash 中使用的常见特殊字符

| “”或“” | 表示空白。单引号保留字面意思；双引号允许替换。 |
| $ | 表示扩展(用于变量、命令替换、算术替换等。) |
| \ | 转义字符。用于去除特殊字符的“特殊性”。 |
| # | 评论。该字符之后的任何内容都不会被解释。 |
| = | 分配 |
| [ ]或[[ ]] | 测试；评估 true 或 false |
| ！ | 否认 |
| >>, >, < | 输入/输出重定向 |
| &#124; | 将一个命令的输出发送到另一个命令的输入。 |
| *或者？ | 全局字符(又名通配符)。？是单个字符的通配符。 |

## Bash 编程简介

Bash 具有许多内置的检查和比较功能，在许多情况下非常方便。您可能以前见过类似下面这样的 if 语句:

```
if [ $foo -ge 3 ]; then
```

本例中的条件本质上是一个命令。这听起来可能很奇怪，但是用方括号将比较括起来与使用内置的测试命令是一样的，就像这样:

```
if test $foo -ge 3; then
```

如果$foo 等于 3，那么将执行“then”之后的块。如果您一直想知道为什么 bash 倾向于使用-ge 或-eq 而不是> =或==，那是因为这种条件类型源于一个命令，其中-ge 和-eq 是选项。

这就是 *if* 本质上所做的，检查命令的退出状态。我将在教程中进一步详细解释。还有更特定于 shells 的内置检查。这个怎么样？

```
if [ -f regularfile ]; then
```

如果文件‘regular file’存在*并且*是常规文件，则上述条件成立。常规文件意味着它不是块或字符设备，也不是目录。这样，你就可以在使用它之前确保一个可用的文件存在。你甚至可以检查一个文件是否可读！

```
if [ -r readablefile]; then
```

如果文件“readablefile”存在*且*可读，则上述条件成立。很简单，不是吗？

## bash if 语句的语法

*if … then* 语句的基本语法如下:

```
if *<condition>*; then*<commands>*fi
```

根据其类型，条件被某些特定的框包围，例如[ ]。你可以在教程中进一步了解不同的类型。您可以使用 *else* 关键字添加在条件为假时要执行的命令，如果主条件为假，则使用 *elif* (elseif)关键字在另一个条件下执行命令。 *else* 关键字总是排在最后。示例:

```
if [ -r somefile ]; then        content=$(cat somefile)elif [ -f somefile ]; then        echo "The file 'somefile' exists but is not readable to the script."else        echo "The file 'somefile' does not exist."fi
```

这个例子的简短说明:首先我们检查文件 somefile 是否可读(“if [ -r somefile ]”)。如果是这样，我们把它读入一个变量。如果不是，我们检查它是否确实存在(“elif [ -f somefile ]”)。如果这是真的，我们报告它存在，但不可读(如果是，我们会阅读内容)。如果文件不存在，我们也会报告。只有当【T2 if 的条件为假时，才会执行 *elif* 的条件。属于 *else* 的命令仅在两个条件都为假时执行。

* * *

[![Complete guide to the Cloud and Dictionary ](img/93ebf63b88ab7fbd48705a01952ba688.png)](https://get.acloudguru.com/cloud-dictionary-of-pain)

[**获得痛苦的云词典**](https://get.acloudguru.com/cloud-dictionary-of-pain)
说云不一定要努力。我们分析了数百万份回复，找出了最容易让学生出错的术语和概念。在这个[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)中，你会发现一些最令人头疼的云术语的简洁定义。

* * *

## bash 条件的基本规则

当您开始编写和使用自己的条件时，有一些规则您应该知道，以防止出现难以跟踪的错误。下面是三个重要例子:

1.  **Always keep spaces between the brackets and the actual check/comparison**. The following won’t work:

    ```
    if [$foo -ge 3]; then
    ```

    Bash 会抱怨一个“丢失的”。

2.  在输入一个新的关键字如“then”之前，总是终止该行。单词 *if* 、 *then* 、 *else* 、 *elif* 和 *fi* 是 shell 关键字，意思是不能共用一行。放一个“；”在前面的语句和关键字之间，或者将关键字放在新行的开头。如果不这样做，Bash 将抛出类似“意外标记` fi '附近的语法错误”的错误。
3.  *It is a good habit to quote string variables if you use them in conditions*, because otherwise they are likely to give trouble if they containspaces and/or newlines. By quoting I mean:

    ```
    if [ "$stringvar" == "tux" ]; then
    ```

    有些情况下你不应该引用，但这种情况很少见。在本教程的后面部分，您将会看到其中的一个。

此外，了解以下两点可能会有所帮助:

1.  *You can invert a condition* by putting an “!” in front of it. Example:

    ```
    if [ ! -f regularfile ]; then
    ```

    请务必放置“！”在括号里！

2.  *You can combine conditions* by using certain operators. For the single-bracket syntax that we’ve been using so far, you can use “-a” for *and* and “-o” for *or*. Example:

    ```
    if [ $foo -ge 3 -a $foo -lt 10 ]; then
    ```

    如果$foo 包含大于或等于 3 的整数且 **L** ess **T** han 10，则上述条件将返回 true。您可以在各自的条件语法中阅读更多关于这些组合表达式的内容。

另外，还有一件基本的事情:不要忘记条件也可以用在其他语句中，比如 *while* 和 *until* 。解释这些超出了本教程的范围，但是你可以在[初学者 Bash 指南](https://www.tldp.org/LDP/Bash-Beginners-Guide/html/sect_09_02.html "Read about the while and the until loop in the Bash Guide for Beginners")中阅读。

总之，到目前为止，我只展示了单括号中的条件。然而，还有更多的语法，您将在下一节读到。

## 不同的条件语法

Bash 为条件提供了不同的语法。我会列出他们三个:

### 1。单括号语法

这是您在前面的段落中已经看到的条件语法；这是最早支持的语法。它支持三种类型的条件:

*   **基于文件的条件**
*   **基于字符串的条件**
    *   Allows checks on a string and comparing of strings. Example one:

        ```
        if [ -z "$emptystring" ]; then
        ```

        如果$emptystring 是空字符串或未初始化的变量，则上述条件成立。例子二:

        ```
        if [ "$stringvar1" == "cheese" ]; then
        ```

        如果$stringvar1 仅包含字符串“cheese ”,则上述条件成立。有关更多基于字符串的条件，请参见下表。

*   **算术(基于数字)条件**

### 2。双括号语法

您可能已经遇到过用双方括号括起来的条件，如下所示:

```
if [[ "$stringvar" == *string* ]]; then
```

双括号语法是单括号语法的增强版本；它主要有相同的功能，但也有一些重要的区别。我将在这里列出它们:

*   *The first difference* can be seen in the above example; when comparing strings, the double-bracket syntax features shell globbing. This means that an asterisk (“*”) will expand to literally anything, just as you probably know from normal command-line usage. Therefore, if $stringvar contains the phrase “string” anywhere, the condition will return true. Other forms of shell globbing are allowed, too. If you’d like to match both “String” and “string”, you could use the following syntax:

    ```
    if [[ "$stringvar" == *[sS]tring* ]]; then
    ```

    请注意，只允许一般的 shell globbing。特定于 Bash 的东西，如{1..4}或者{foo，bar}都不行。还要注意，如果您引用了正确的字符串，那么 **globbing 将不起作用。在这种情况下，您应该不加引号。**

*   *The second difference* is that word splitting is prevented. Therefore, you could omit placing quotes around string variables and use a condition like the following without problems:

    ```
    if [[ $stringvarwithspaces != foo ]]; then
    ```

    尽管如此，引用字符串变量仍然是一个好习惯，所以我建议继续这样做。

*   *The third difference* consists of not expanding filenames. I will illustrate this difference using two examples, starting with the old single-bracket situation:

    ```
    if [ -a *.sh ]; then
    ```

    如果工作目录中有一个文件的扩展名为. sh，上述条件将返回 true。如果没有，它将返回 false。如果有几个。sh 文件，bash 将抛出一个错误并停止执行脚本。这是因为*。sh 扩展到工作目录中的文件。使用双括号可以防止这种情况:

    ```
    if [[ -a *.sh ]]; then
    ```

    只有当工作目录中有一个名为“*”的文件时，上述条件才会返回 true。嘘”，不管其他的。sh 文件存在。星号是按字面理解的，因为双括号语法不扩展文件名。

*   *The fourth difference* is the addition of more generally known combining expressions, or, more specific, the operators “&&” and “||”. Example:

    ```
    if [[ $num -eq 3 && "$stringvar" == foo ]]; then
    ```

    如果$num 等于 3，并且$stringvar 等于“foo”，则上述条件返回 true。也支持单括号语法中的-a 和-o。请注意，*和*运算符优先于*或*运算符，这意味着“& &”或“-a”将在“||”或“-o”之前计算。

*   *第五个不同点*是双括号语法允许使用“=~”操作符进行正则表达式模式匹配。更多信息参见[表格](#string-based-conditions)。

### 3。双括号语法

还有另一种算术(基于数字)条件的语法，很可能来自 Korn shell:

```
if (( $num <= 5 )); then
```

如果$num 小于或等于 5，则上述条件成立。程序员可能更熟悉这种语法。它具有所有“普通”操作符，如“==”、“ =”。它支持“&&”和“||”组合表达式(但不支持-a 和-o 组合表达式！).它相当于内置的 let 命令。

## 条件表

下表列出了单括号和双括号语法的条件可能性。除了一个例外，示例以单括号语法给出，但总是与双括号兼容。

| 

### 1。基于文件的条件:

 |
| 情况 | 如果为真 | 示例/解释 |
| [-现有文件] | 文件“existingfile”存在。 | if[-a tmp . tmp]；然后 rm -f tmp.tmp # *确保我们不会被旧的临时文件* fi 打扰 |
| [ -b blockspecialfile ] | 文件“blockspecialfile”存在，并且是块专用文件。 | Block special files 是在/dev 中找到的特殊内核文件，主要用于硬盘、光盘、软盘之类的 ATA 设备，if[-b/dev/fd0]；然后添加 if=floppy.img of=/dev/fd0 # *将图像写入软盘* fi |
| [ -c characterspecialfile ] | 文件“characterspecialfile”存在，并且是特殊字符。 | 字符特殊文件是/dev 中的特殊内核文件，用于各种目的(音频硬件、tty，还有/dev/null)。if[-c/dev/DSP]；然后 cat raw.wav > /dev/dsp # *这实际上适用于某些原始 wav 文件* fi |
| [ -d 目录] | 文件“目录”存在，并且是一个目录。 | 在 UNIX 风格中，目录是一种特殊的文件。kde]；thenecho“你好像是 kde 用户。”船方不负担装货费用 |
| [ -e 现有文件] | 文件“existingfile”存在。 | (与-a 相同，参见该条目中的示例) |
| [ -f 正则化] | 文件“regularfile”存在，并且是一个常规文件。 | 常规文件既不是块或字符特殊文件，也不是目录。bashrc]；然后 source ~/。巴什尔菲 |
| [ -g sgidfile ] | 文件“sgidfile”存在，并且是 set-group-ID。 | 当在一个目录上设置了 SGID 位时，在该目录中创建的所有文件都将继承该目录的组。选择[创建的文件正在继承组“$(ls -ld。工作目录中的&#124; awk“{ print $ 4 }”，"fi](https://acloudguru.com/blog/engineering/the-awk-command-bash-basics) |
| [-g fileownebyeffective group] | 文件“fileownedbyeffectivegroup”存在，并由有效的组 ID 拥有。 | 有效组 id 是执行用户的主要组 id。-G 文件]；然后# *感叹号反转它后面的条件的结果* chgrp $(id -g) file # *如果它不是有效的组，则更改该组* fi |
| [ -h 符号] | 文件“symboliclink”存在，并且是一个符号链接。 | if[-h $ pathtofile]；然后 pathtofile = $(read link-e $pathtofile)#*确保$ pathtofile 包含实际文件，而不是指向它的符号链接* fi |
| [ -k stickyfile ] | 文件“stickyfile”存在，并设置了其 sticky 位。 | 粘性位已经有了相当长的历史，但是现在被用来防止任何人删除全球可写目录的内容。-k/tmp]；然后# *一个感叹号反转它后面条件的结果*回显“警告！任何人都可以在/tmp 中删除和/或重命名您的文件！”船方不负担装货费用 |
| [ -L 符号链接] | 文件“symboliclink”存在，并且是一个符号链接。 | (与-h 相同，有关示例，请参见该条目) |
| [-N modifiedsinclastread] | 文件“modifiedsincelastread”存在，并且在上次读取后被修改。 | if[-N/etc/crontab]；然后 killall -HUP crond # *SIGHUP 让 crond 重新读取所有 crontabs* fi |
| [-fileownebyeffective user] | 文件“fileownedbyeffectiveuser”存在，由执行脚本的用户所有。 | if [ -O 文件]；chmod 600 file # *将文件设为私有，如果您不拥有它* fi，这是一个坏主意 |
| [ -p namedpipe ] | 文件“namedpipe”存在，并且是一个命名管道。 | 命名管道是/dev/fd/中的一个文件，只能读取一次。参见[我的 bash 教程](https://www.linuxtutorialblog.com/post/tutorial-the-best-tips-tricks-for-bash#using-several-ways-of-substitution "See")中使用它的案例. if[-p $ file]；然后 CP＄file tmp . tmp #*确保我们能够任意多次读取该文件* file="tmp.tmp" # |
| [ -r readablefile ] | 文件“readablefile”存在，并且对于脚本是可读的。 | if [-r 文件]；然后 content=$(cat file) # *将$content 设置为文件* fi 的内容 |
| [ -s 非空文件] | 文件“nonemptyfile”存在，其大小超过 0 字节。 | if [ -s 日志文件]；然后 zip 日志文件# *备份旧的日志文件*在创建新的日志文件之前，触摸日志文件# *。* fi |
| [ -S 套接字] | 文件“socket”存在，并且是一个套接字。 | socket 文件用于进程间通信，具有类似于网络连接的接口。然后 mysql–socket =/var/lib/MySQL/MySQL . sock #*见[本 MySQL 提示](https://www.tech-recipes.com/mysql_tips762.html "MySQL")* fi |
| [ -t openterminal ] | 文件描述符“openterminal”存在，并且引用了一个打开的终端。 | 在 Linux/UNIX 上，几乎所有的事情都是使用文件来完成的，终端也不例外。那里有个黑人。来自终端$(tty)的消息。”>/dev/pts/3 # *任何使用该终端的人都会看到这条消息！* fi |
| [ -u suidfile ] | 文件“suidfile”存在，并且设置为-user-ID。 | 在文件上设置 suid 位会导致使用文件所有者的凭据而不是执行用户的凭据来执行该文件。thenecho "正在以用户$(ls-l executable &#124; awk“{ print $ 3 }”)身份运行程序可执行文件。船方不负担装货费用 |
| [ -w 可写文件] | 文件“writeablefile”存在，并且可写入脚本。 | if[-w/dev/hda]；然后 grub-install /dev/hdafi |
| [ -x executablefile ] | 文件“executablefile”存在，并且可由脚本执行。 | 请注意，对目录的执行权限意味着它是可搜索的(您可以看到它包含哪些文件)。if[-x/root]；选择“您可以查看/根目录的内容。”船方不负担装货费用 |
| [ newerfile -nt olderfile ] | 文件“newerfile”比“olderfile”更新，或者如果“newerfile”存在而“olderfile”不存在。 | if[story . txt 1-nt story . txt]；thenecho "story.txt1 比 story.txt 新；我建议继续前者。”船方不负担装货费用 |
| [ olderfile -ot newerfile ] | 文件“olderfile”比“newerfile”早更改，或者如果“newerfile”存在而“olderfile”不存在。 | if[/mnt/remote/remote file-ot local file]；然后 CP-f local file/mnt/remote/remote file #*确保远程位置也有文件的最新版本* fi |
| [相同的 ef 文件] | 文件“相同”和文件“文件”指的是相同的设备/信息节点号。 | if[/dev/cdrom-ef/dev/DVD]；选择“您的主 cd 驱动器似乎也能读取 dvd。”船方不负担装货费用 |
| 

### 2。基于字符串的条件:

 |
| 情况 | 如果为真 | 示例/解释 |
| [ STRING1 == STRING2 ] | STRING1 等于 STRING2。 | if[" $ 1 " = = " moo "]；thenecho $cow # *试过执行“apt-get moo”吗？* fiNote:也可以用单个“=”代替双个。 |
| 【STRING1！= STRING2 ] | STRING1 不等于 STRING2。 | if [ "$userinput "！= " $ password "]；thenecho "拒绝访问！密码错误！”退出 1 # *在这里停止脚本执行* fi |
| [字符串 1 >字符串 2 ] | 在当前区域设置中，STRING1 在 STRING2 之后排序(按词法)。 | 尖括号前有反斜杠，因为需要对括号进行转义才能正确解释。作为一个例子我们有一个基本的[冒泡排序](https://en.wikipedia.org/wiki/Sorting_algorithm#Bubble_sort "What is a bubble sort? See wikipedia!") : *(如果你不理解这个不要觉得惭愧，这是一个更复杂的例子)* array=( linux 教程博客)swaps = 1 while((swaps>0))；doswaps = 0 for((I = 0；I<(($ { # array[@]}–1))；i++))；doif[" $ { array[$ I]} ">" $ { array[$((I+1))]} "]；然后# *这里是排序条件*tempstring = $ { array[$ I]} array[$ I]= $ { array[$((I+1))]} array[$((I+1))]= $ tempstring((swaps = swaps+1))fidonedonecho $ { array[@]} #*返回《博客 linux 教程》* |
| [字符串 1 | 在当前区域设置中，STRING1 在 STRING2 之前排序(按词法)。 |
| [ -n 非 EMPTYSTRING ] | NONEMPTYSTRING 的长度大于零。 | 这个条件只接受有效的字符串，所以一定要用引号括起你给它的任何内容。then user input = parse($ user input)#*只有当用户实际输入时才进行解析。*请注意，您也可以省略“-n”，因为只有一个字符串的括号的行为是相同的。 |
| [ -z EMPTYSTRING ] | EMPTYSTRING 是一个空字符串。 | 这个条件也接受非字符串输入，比如未初始化的变量:if[-z $ uninitializedvar]；thenuinitializedvar = " initialized " #*-z 对未初始化的变量返回 true，所以我们在这里初始化它。* fi |
| *仅双括号语法:*[[string 1 = ~ regexpartern]] | STRING1 匹配 REGEXPATTERN。 | 如果您熟悉正则表达式，可以使用这些条件来执行正则表达式匹配。_%+-]+@[A-Za-z0-9。-]+.[A-Za-z]{2，4 } b "]]；thenecho "$email 包含有效的电子邮件地址。"船方不负担装货费用 |
| 

### 3。算术(基于数字)条件:

 |
| 情况 | 如果为真 | 示例/解释 |
| [1 到 2 之间的 1-eq] | NUM1 与 NUM2 相等。 | 这些条件只接受整数。如果可能的话，字符串将被转换成整数。一些随机的例子:如果[ $？-eq 0]；然后# *$？返回前一个命令*的退出状态，显示“前一个命令成功运行”fiif[$(PS-p $ PID-o ni =)-ne $(nice)]；thenecho "Process $pid 正在使用非默认的 nice 值" fiif [ $num -lt 0 ]运行；不允许负数；退出…”退出 1fi |
| [一对二] | NUM1 是 not**e**哪个是 NUM2。 |
| [1-gt 乘以 2 ] | NUM1 是 **G** reater **T** han NUM2。 |
| [一格二] | NUM1 大于或等于 NUM2 的 T2。 |
| [编号 1 -lt 编号 2 ] | NUM1 是 **L** ess **T** 韩 NUM2。 |
| [一二三] | NUM1 比 NUM2 小或等于 num 2。 |
| 

### 4。其他条件:

 |
| 情况 | 如果为真 | 示例/解释 |
| [ -o shelloption ] | 外壳选项“shell option”已启用。 | Shell 选项修改 bash 的行为，除了一些指示 shell 状态的不可修改的选项。-o checkwinsize ] # *感叹号反转其后条件的结果* echo "Shell 选项 checkwinsize 被禁用；启用它，这样您就可以毫无问题地调整终端窗口的大小。”shopt -s checkwinsize # *此 shell 选项可修改*fiif[-o log in _ shell]；thenecho“这是一个登录外壳。”# *此外壳选项不可修改* fi |

使用双括号语法，您可以使用以下条件:

| 

### 5。双括号语法条件:

 |
| 情况 | 如果为真 | 示例/解释 |
| (第 1 季第 2 集) | NUM1 等于 NUM2。 | 这些条件只接受整数。如果可能的话，字符串将被转换成整数。一些随机的例子:if (( $？== 0 ));然后# *$？返回前一个命令*的退出状态，显示“前一个命令成功运行”fiif (( $(ps -p $pid -o ni=)！= $(nice)))；thene CHO“Process $ PID 正在以非默认的好值运行”fiif(($ num<0))；不允许负数；退出…”退出 1fi |
| (1 号！=第 2 个) | NUM1 不等于 NUM2。 |
| (编号 1 >编号 2) | NUM1 大于 NUM2。 |
| ((数字 1 >=数字 2)) | NUM1 大于等于 NUM2。 |
| (编号 1 | NUM1 小于 NUM2。 |
| (数字 1 <=数字 2) | NUM1 小于等于 NUM2。 |

在这些枯燥的信息之后，这里有一些解释给那些想知道更多的人…

## 潜得更深一点

我说过，如果本质上检查命令的退出状态，我会讲述更多关于*的事实。所以我会的。*

bash 关于条件的基本规则是 *0 等于真，> 0 等于假*。

这与许多编程语言截然相反，0 等于假，1(或更多)等于真。这背后的原因是 bash 之类的 shells 大量处理程序。按照 UNIX 惯例，程序使用退出状态来指示执行是否顺利或发生了错误。因为成功的执行不需要任何解释，它只需要一个退出状态。然而，如果有问题，知道哪里出了问题是很有用的。因此，0 表示成功执行，1-255 表示发生了哪种错误。

数字 1-255 的含义因返回它们的程序而异。

总之，*如果*在*之后执行程序块，那么*当命令返回 0 时。是的，条件就是命令。短语[ $foo -ge 3 ]返回一个退出状态，另外两个语法也是如此！因此，有一个简单的技巧可以用来快速测试一个条件:

```
[ $foo -ge 3 ] && echo true
```

在本例中，“echo true”仅在“$foo -ge 3”返回 0 (true)时执行。你可能会问，这是为什么。这是因为 bash 只在需要的时候评估一个条件。当使用*和*组合表达式时，两个条件都需要为真才能使组合表达式返回真。如果第一个条件返回 false，那么第二个条件返回什么并不重要；结果将是假的。

因此，bash 不会计算第二个条件，这也是示例中不执行“echo true”的原因。这同样适用于*或*操作符(" || ")，其中如果第一个条件为真，则不计算第二个条件。嗯，潜水到此为止。

如果你想知道更多，我想给你介绍一下[高级 Bash 脚本指南](https://www.tldp.org/LDP/abs/html/tests.html "Go")和 [Bash 参考手册](https://www.gnu.org/software/bash/manual/bashref.html#Conditional-Constructs "Read")。你也可以看看我们的课程[Bash 脚本系统管理员指南](https://acloudguru.com/course/the-system-administrators-guide-to-bash-scripting-2)。

## 结论

在本教程中，您已经能够开始理解 bash 脚本中条件的许多可能性。您已经了解了编写和使用条件的基本规则，了解了三种语法及其属性，并且可能利用这个机会进行了更深入的研究。

我希望你像我喜欢写作一样喜欢阅读。您可以随时返回此处，在[表](#h-table-of-conditions)中查找条件(将该链接标记为书签以直接查看该表)，或者刷新您的知识。感谢阅读和快乐脚本！

*想提升你的技术水平吗？[在 YouTube 上订阅一位云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)，在[脸书](https://www.facebook.com/acloudguru)上喜欢我们，在 [Twitter](https://twitter.com/acloudguru) 上关注我们，或者在 [Discord](http://discord.gg/acloudguru) 上加入对话！*