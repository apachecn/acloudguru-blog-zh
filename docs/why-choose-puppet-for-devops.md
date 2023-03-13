# 为什么要为 DevOps 选择木偶？|云专家

> 原文：<https://acloudguru.com/blog/engineering/why-choose-puppet-for-devops>

如果您像 DevOps 世界中的大多数人一样，您总是对自动化任务和保护您的基础设施感兴趣。但重要的是找到不会牺牲质量或损失效率的方法。

## DevOps 的木偶

42%的 DevOps 企业目前使用这个方便的工具，理由很充分。Puppet for DevOps 是独一无二的，因为它允许您实施自动化，增强组织，提高安全措施，并提高整个基础架构的整体速度。傀儡的特殊能力显然是改变游戏规则的。这种快速设置的很大一部分是由于模块创作过程的初始化。

## **什么是木偶模块？**

傀儡模块是一组独立的关键组件。这可以包括类、清单、数据等等。通过 Puppet 模块，我们可以定义特定的资源。每个 Puppet 模块最终帮助我们回收 Puppet 代码，并随着时间的推移保持代码组的组织。清单由一个类或定义的类型组成，它是一个 Puppet 代码(用 Puppet DSL 编写)。一个人想要创作的模块必须首先在头脑中有一个最终目标——知道目的是首要的。

Puppet 环境也可以容纳大量的模块——如果需要的话，有时会超过数百个。一系列专用于特定任务的特定命名类充当必须创建的程序。这些程序然后导致清单的生成。

**清单**是包含描述如何配置资源的 Puppet 配置语言的文件。它们声明定义节点上要实施的状态的资源；以扩展名`.pp`保存

此外，必须利用名为`modulepath`的配置变量定义模块类的外壳位置，然后设置安装参数。在下面的示例中，类命令的创建通常是这样构造的:

`sudo pdk new class install`

例如，清单可以是一个 `nginx` 模块的`install.pp`文件。

它包含由包资源类型组成的 `nginx::install class`，包资源类型规定了这个类在应用到节点上后将执行的操作:`class nginx::install {`

`package {nginx:`

`ensure => present,`

`}`

`}` `install.pp` 文件，即“安装类”所在的位置，保存着资源的中心位置。此外，类主要帮助减少清单文件中重复代码的回收时间。代码块也分散在几个清单中；因此，模块是一个完整的救命稻草。

## 为什么木偶很重要？

Puppet 对于处理大量的服务器非常有用。它消除了耗时的手动配置管理步骤带来的额外压力。我们的[Puppet Professional Certification–Elle Krout 的 PPT206](https://acloudguru.com/course/puppet-professional-certification-ppt206) 课程深入到 [Puppet Enterprise](https://acloudguru.com/hands-on-labs/installing-puppet-enterprise) plus 开源 Puppet，如果您希望了解更多关于 Puppet 模块创作、最佳实践以及如何利用附加功能的实现的信息，它将为您提供极大的帮助。

对于任何组织来说，配置中断和爬行速度都是代价高昂的。Puppet Enterprise (PE)可以使 IT 网络服务部署和维护项目变得轻而易举。-代码管理和基础设施策略不再那么令人头疼，因为 PE 还提供了一些优秀的内置工具。

## 从哪里开始？

现在，您已经对什么是 DevOps 的 Puppet 以及如何使用它有了一个基本的概念，接下来您就可以看到它的实际应用了。请务必订阅该博客，以了解课程发布、安全提示和技巧，以及更棒的 Linux 学院内容。如果你对课程、Puppet 模块或其他任何东西有任何疑问，请随时通过商务社交网站 LinkedIn 与 Elle 联系。另外，别忘了参加 Linux 学院[社区 Slack](https://linuxacademycommunity.slack.com/) 频道的对话！我们希望您喜欢本课程—准备将您的 Puppet Enterprise 技能提升到一个新的水平。