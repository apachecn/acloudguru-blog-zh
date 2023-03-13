# 数据准备的 5 个常见 Python 陷阱

> 原文：<https://acloudguru.com/blog/engineering/5-common-python-pitfalls-for-data-preparation>

Python 是一种强大的数据准备语言，但是人们可能会遇到一些常见的错误或陷阱。在这篇博文中，我将讨论人们在使用 Python 进行数据准备时遇到的五个最常见的问题。

## 1.将缺少的值(` NaN `)视为 false。

False、None 和 0(任何数值类型)的计算结果都为 False。

这组对象和值被称为“falsy ”,其计算结果为 false。NaN 或 missing 值不为 false，因此将 *not* 评估为 false。这可能会导致许多操作的混乱和意外行为。

## 2.尝试比较缺失值

看起来很简单，`NaN == NaN`将返回 true。这两个值“看起来”一样。

然而，由于不可能知道两个丢失的值是否相同，所以该操作将总是返回 false。

## 3.认为 all()只有在所有元素都为真的情况下才返回真。

如果 iterable 的所有元素都为真(或者 iterable 为空)，则`all()`方法返回真。

不要把它想成“如果 iterable 的所有元素都为真，则返回真”，而是“如果 iterable 中没有假元素，则返回真。”

当 iterable 为空时，其中不能有 false 元素，这意味着`all([]`的计算结果为 True。

* * *

## 通往更好职业的钥匙

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## 4.转换为布尔值

Pandas 遵循 numpy 惯例，当您试图将某个东西转换为 bool 时会引发一个错误。当使用布尔运算 and、or 或 not 时，在 if 或 or 中会发生这种情况。

不清楚结果应该是什么。因为不是零长所以应该是真的吗？假是因为有假值？

现在还不清楚，所以相反，熊猫养了一只`ValueError`

`ValueError: The truth value of a Series is ambiguous. `

`Use a.empty, a.bool() a.item(),a.any() or a.all().`

## 5.了解 isin()操作的结果。

`isin()`操作返回一个布尔序列，显示序列中的每个元素是否都包含在传递的值序列中。

```
 s = pd.Series(['dog', 'cat', 'fish'])
>>> s.isin(['bird'])
0    False
1    False
2    False
dtype: bool
```

请注意,“鸟”在该系列中不存在。

```
>>> s.isin(['bird', 'cat'])
0    False
1     True
2    False
dtype: bool
```

注意“cat”确实存在于序列的第二个值中。

## 了解更多关于使用 Python 进行数据准备的信息

Python 是一种功能强大的语言，但是在缺少值和布尔值的情况下会产生混淆。请记住，缺少的值被认为是错误的，不能进行比较。

当使用`all()`方法时，记住当 iterable 中没有 false 值时，它返回 true。如果所有值都丢失了，就像在空数组的情况下，`all()`也返回 true，因为丢失的值不被认为是 false。

如果您在尝试转换为 bool 值时收到一个`ValueError`,请务必采纳有用的建议并使用建议的方法之一。

想了解更多关于使用 Python 进行数据准备的信息吗？查看我们的 Python 课程的[数据准备(导入和清理)。](https://acloud.guru/overview/data-preparation-for-python)