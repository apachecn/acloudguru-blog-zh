# Python 2 和 3 的故事|云专家

> 原文：<https://acloudguru.com/blog/engineering/the-story-of-python-2-and-3>

我们为系统管理员开设了 [Python 脚本课程，该课程涉及 Python 2 和 Python 3。这次发布是讨论*为什么*这个版本差异如此重要以及你应该注意什么的好时机。](https://linuxacademy.com/linux/training/course/name/python-scripting-for-system-administrators)

## 关于版本控制的简短说明

如果你利用 [SemVer](https://semver.org/) 对一个软件项目进行版本控制，那么一个主要的版本变更就是做出“突破性变更”的时候了，这就是 Python 3 所做的。从版本控制的角度来看，这正是我们应该如何对我们的项目进行版本控制。

## 犯了错误…

Python 3 之所以存在，是因为 Guido 看到了该语言需要一些改进的地方，而这些改变不能在考虑向后兼容性的情况下进行。作为一个从事软件工作的人，你可以边做边学，在开始的时候，你几乎不可能知道所有的事情。一个项目的设计会经历一些后来发现不尽如人意的转折，这很有道理。Python 3 是偿还“技术债务”的一个很好的例子，但是这个决定最初并没有被很好地接受。在 Python 3 发布的时候，有很多 Python 代码在生产，既有开源的也有专有的。可以想象，当您需要潜在地更改应用程序代码的大部分时，在您的业务中升级到新版本的语言是很困难的。这是 Python 3 面临的问题，所以即使 Python 3 很棒，也很难在一夜之间移动这么大的社区。

## 主要差异

以下是我认为最有可能影响 Python 代码的两个主要版本之间的差异:

### 字符串和二进制数据(字节)

在版本 2 中，您可以将 Unicode 数据(字节)与 8 位字符串混合使用，这种方法偶尔会有效，但并不总是有效。这导致了 Python 3 中的变化；您不再能够隐式地混合文本和二进制数据。根据文件的模式，最有可能出错的地方是与文件内容的交互。这里有一个例子，可以演示同样的代码如何在 Python 2 和 3 之间产生不同的类型和错误。 *str_vs_bytes.py*

```
f = open("example.txt", 'rb') # opening in 'binary' read modedata = f.read()other_str = "other string"print("data is of type: %s" % type(data))print("other_str is of type: %s" % type(other_str))data + other_str # concatenating to see if an error occurs
```

如果我们用 Python 2 运行这个脚本，我们会得到以下结果:

```
$ python2 str_vs_bytes.pydata is of type: <type 'str'>other_str is of type: <type 'str'>
```

用 Python 3 做同样的事情，我们会看到一个错误，并且`other_str`与`data`的类型不同:

```
$ python3 str_vs_bytes.pydata is of type: <class 'bytes'>other_str is of type: <class 'str'>Traceback (most recent call last):  File "str_vs_bytes.py", line 9, in <module>    data + other_strTypeError: can't concat str to bytes
```

这里最大的障碍是确保在 Python 3 中总是以正确的模式打开文件。

### `print`语句与`print`函数

编程中最常见的事情之一是打印到屏幕上。Python 通过使用 Python 2 中的`print` *语句*和 Python 3 中的`print` *函数*，使打印变得尽可能简单。这种差别非常微妙，但是在 Python 2 和 3 之间，`print`的使用发生了变化，它是一个函数，因此需要括号。这一行在 Python 2 中运行得非常好，但是在 Python 3 中会引发一个异常: *Python 2*

```
>>> print "something"something
```

*Python 3*

```
>>> print "something"  File "<stdin>", line 1    print "something"                    ^SyntaxError: Missing parentheses in call to 'print'. Did you mean print("something")?
```

幸运的是，这个错误很好地解释了这种情况，如果您在 Python 2 `print`的用法中添加括号，就不会遇到任何问题。

### 整数除法

在 Python 2 中，2 个整数的除法总是返回一个整数。这是有意义的，因为你可能不想隐式地从`int`转换到`float`，但是作为一个程序员，当你想到除法时，你只想做普通的数学运算。这种行为在 Python 3 中有所改变，因此标准除法将返回完整的结果，而不是截断的值。 *Python 2*

```
>>> 1 / 2 == 1 // 2True>>> 1 / 20
```

下面是使用 *Python 3* 的同一个例子:

```
>>> 1 / 2 == 1 // 2False>>> 1 / 20.5
```

## 为 Python 编写代码 2**&3**

在[课程](https://linuxacademy.com/linux/training/course/name/python-scripting-for-system-administrators)中，我们利用测试驱动开发(TDD)来帮助我们设计软件，但我们得到的一个额外好处是我们有一个测试套件，可以针对多个版本的 Python 运行。这种方法使你更容易确信你正在编写支持两个主要版本的软件，但是如果你没有编写测试，那么你知道主要的区别是很重要的。