# Docker 复制 vs 添加:有什么区别？|云专家

> 原文：<https://acloudguru.com/blog/engineering/docker-copy-vs-add-whats-the-difference>

如果您使用 Docker 文件构建容器映像，您很可能会遇到 Docker 指令 ADD 和 COPY。添加和复制都提供了类似的功能，因为它们都允许您在构建时将文件夹和文件放入映像中。那么应该用哪一个呢？

在这篇文章中，我将讨论复制和添加之间的一些细微差别，并帮助您确定何时使用哪一种。

* * *

**通往更好职业的钥匙**

[立即开始 ACG](https://acloudguru.com/pricing) 通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室来改变你的职业生涯。

* * *

## 什么是 Docker ADD 指令？

首先，我们来谈谈 ADD 指令。ADD 指令一直是 Docker 的一部分。ADD 使用两个参数:源和目标。

*   source 参数适用于所有类型的文件，并且与构建上下文相关。

*   目标参数可以是 WORKDIR 的绝对路径或相对路径。

ADD 还有其他一些它可以表演的“魔术”。ADD 还支持从远程 URL 下载文件。除了远程文件支持，ADD 还可以自动提取各种类型的档案到镜像中。如果您提供的源文件是用 tar、gzip、bzip2 或 xz 压缩的档案文件，ADD 会自动将档案文件解压缩到所提供的目的地。应该注意的是，它通过内容来确定存档的类型，而不是简单地使用文件扩展名。

## 什么是 Docker 复制指令？

现在我们来看看复制说明。随着 Docker 版本 1.0 的发布，COPY 作为一个指令被添加进来。像添加一样，复制也可以让您将文件和文件夹放入映像中。

它也有两个参数:源和目的地。

然而，COPY 指令更加简单，并且没有 ADD 的一些额外特性。COPY 不能与 URL 一起工作，而且它还按原样复制归档文件，而不是试图提取它们。

## 为什么添加和复制做同样的事情？

为什么两条不同的指令做同样的事情？

很久以前，有人指出 ADD 指令并不总是像预期的那样工作。也许您有一个想要复制但不想提取的 tar 存档文件。ADD 会尝试提取它。此外，您可能有一个以无法识别的格式压缩的 tar 归档文件。您可以尝试使用 ADD 来提取它，但是因为它不被识别，所以 ADD 会将它复制为一个文件。

总的来说，大多数人认为 ADD 做得太多了。所以新的指令副本被添加到 Docker 中。ADD 是作为一个指令保存的，以免破坏向后兼容性——此外，一些开发人员喜欢 ADD 提供的附加特性。

## 什么时候应该使用 ADD，什么时候应该使用 COPY？

那么什么时候应该用 ADD，什么时候应该用 COPY 呢？根据 Docker 最佳实践指南,你通常应该使用副本——但你的里程数可能会有所不同。

您可能想使用添加的远程网址功能或解压缩的档案。无意的添加而不是复制指令可能意味着功能映像和“损坏的”映像之间的差异。例如，您需要在映像中有一个 tar 归档文件作为归档文件。如果你不小心使用了 ADD，你会得到存档的内容，而不是实际的图像。

关于 ADD 的远程 URL 特性，您最好使用 RUN 指令，并提供命令 curl 或 wget 来下载文件，然后在该命令之后使用 tar 或 unzip(如果是归档文件)，或者您可能需要为您的映像运行的其他命令。这种方法产生较少的指令，并且较少的指令创建较小的图像。

有关添加和复制的更多信息，请务必查看官方的 [Docker builder 参考资料](https://docs.docker.com/engine/reference/builder/)。

## 了解有关容器的更多信息

想了解更多关于容器的知识吗？查看我们新的 [Red Hat 容器认证专家和 Kubernetes 考试(EX180)](https://learn.acloud.guru/course/red-hat-certified-specialist-in-containers-and-kubernetes-exam/overview) 课程。它旨在帮助您获得通过 EX180 考试所需的知识和技能，并为您提供使用 Red Hat OpenShift 创建、管理和部署容器化解决方案的实践经验。

* * *

*关注 [Twitter](https://twitter.com/acloudguru) 、[脸书](https://www.facebook.com/acloudguru)、[订阅 YouTube 上的云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)，或者加入我们的 [Discord 社区](https://discord.com/invite/acloudguru)的讨论，跟上所有的科技技能。看看这个月的[免费技术培训](https://acloudguru.com/blog/news/whats-free-at-acg)的轮值名单！*