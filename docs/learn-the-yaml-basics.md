# 了解 YAML 基础知识|云专家

> 原文：<https://acloudguru.com/blog/engineering/learn-the-yaml-basics>

随着 YAML 越来越多地与各种敏捷语言和应用程序一起使用，学习这种数据序列化语言的基础知识将让您投入并开始使用各种工具，如 Ansible、Kubernetes 和 Salt。

幸运的是，YAML 很容易让人读懂，也很容易掌握，所以这里有一个快速的“五分钟 YAML”纲要:

## YAML 文件的组成部分

YAML 文件由三个核心组件组成:映射、列表和标量。

*映射*是简单的键值对，就像`ip: 10.0.4.0`一样。

*列表*像任何纯文本项目符号列表一样工作，每个项目在一个新行上，并以破折号开始。

最后，*标量*是字符串、布尔或数字；列表中的一个项目是它自己的标量，而键值对的`key`和`value`都是单独的标量。

映射和列表也可以合并。

```
name: Dana Scully username: dscullyroles:   - FBI Agent - Medical doctor
```

## YAML 和空白

在组成 YAML 的点点滴滴之外，我们看不见的东西也很重要。即间距。在 YAML，空格表示一个“集合”或一组相关的线条。例如，上面例子中的`roles`下的所有内容都是一个集合。

YAML 的空格应该是空格。在许多情况下，它*必须*是空格。尤其是缩进，仅限于两个单独的位置，但是在冒号和键值对中的值之间以及在列出的项目中的破折号之后也必须使用空白。

## 就是这样！

这是对 YAML 基本知识的五分钟概述。是的，YAML 确实有更多我们在[动手 YAML 基础课程](https://acloudguru.com/course/yaml-essentials)中谈到的特性，但是对于配置文件，这就是你真正需要的所有 YAML。

渴望了解锚点和制表符、块样式和流程？然后查看 [*YAML 要领*](https://acloudguru.com/course/yaml-essentials) 了解更多！