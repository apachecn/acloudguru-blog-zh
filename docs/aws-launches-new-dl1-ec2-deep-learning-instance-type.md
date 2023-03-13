# AWS 推出新的 DL1 EC2 实例类型

> 原文：<https://acloudguru.com/blog/engineering/aws-launches-new-dl1-ec2-deep-learning-instance-type>

AWS 已经发布了一个令人兴奋的新 EC2 实例类型，称为 DL1 实例。[亚马逊 EC2 DL1 实例](https://aws.amazon.com/ec2/instance-types/dl1/) s 旨在以低得多的成本训练深度学习模型。

与当前一代基于 GPU 的实例相比，DL1 实例为训练深度学习模型提供了高达 40%的性价比。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

这些对于训练自然语言处理、对象检测和图像识别用例的深度学习模型来说将是非常棒的。

但这些新实例类型真正酷的事情是，它们由来自 [Habana Labs](https://habana.ai/) 训练处理器的高迪人工智能驱动，而不是 GPU，它们是从头开始设计的，旨在优化人工智能性能。他们还支持[机器学习](https://acloudguru.com/blog/engineering/what-is-machine-learning-as-a-service-mlaas) (ML)框架，如 [TensorFlow](https://acloudguru.com/course/tensorflow-developer-certificate-exam-prep) 和 PyTorch。

以下是 AWS 博客提供的 dl 1.24 x 大型实例的规格:

*   **高迪加速器**–每个实例配备 8 个高迪加速器，共有 256 GB 高带宽(HBM2)加速器内存和加速器之间的高速 RDMA 通信
*   **系统内存**–768 GB 的系统内存，足以在内存中保存非常大的训练数据集，这是我们的客户经常要求的
*   **本地存储**–4tb 的本地 NVMe 存储，配置为四个 1 TB 的卷
*   **处理器**–带有 96 个 vCPUs 的英特尔 Cascade Lake 处理器
*   **网络**–400 Gbps 的网络吞吐量

* * *

*想了解更多关于在 AWS 上设计和部署机器学习解决方案的信息吗？云专家的 [AWS 机器学习](https://acloudguru.com/learning-paths/aws-machine-learning)学习路径提供适合初学者和高级专家的定制课程！*

* * *

新的 DL1 实例目前在美国西部(俄勒冈州)和美国东部(N. Virginia)地区按需提供和现货提供；您还可以购买保留的实例和储蓄计划。点击此处了解更多详情。

这些实例是由[安迪·杰西](https://acloudguru.com/blog/business/7-aws-predictions-as-jassy-moves-up-whats-next-for-aws)在 [re:Invent 2020](https://acloudguru.com/blog/tag/reinvent2020) 上宣布的，所以看到这些实例类型现在普遍可用是非常令人兴奋的。

## 准备好迎接 re:发明 2021

[![2021 re:Invent Pre-Show](img/6994ee477a5fa539a7bf90638d62f67e.png)](https://acloudguru.com/content/reinvent-2021-aws-heroes-on-what-to-know-before-the-show-webinar)

说或回答:发明。。。回复:发明 2021 就在眼前！

11 月 17 日周三，请加入我们，我们将现场直播 re:Invent 2021 预告: *[re:Invent 2021: AWS 英雄们在](https://acloudguru.com/content/reinvent-2021-aws-heroes-on-what-to-know-before-the-show-webinar)* 节目开始前要知道什么。AWS 的英雄们本·凯霍、瑞安·克鲁宁堡、马特·路易斯、马克·努恩尼克霍文、凯莎·威廉姆斯和德鲁·弗曼特将对未来进行预测，并分享他们最期待的主题演讲。

此外，不要忘了查看我们的[re:Invent 2021](https://acloudguru.com/blog/business/the-ultimate-guide-to-aws-reinvent-2021)终极指南，了解您需要了解的关于云领域最大会议之一的所有信息。

### 跟上 AWS 的所有事情

想要跟上 AWS 的所有事情？在推特[上关注 ACG](https://twitter.com/acloudguru)和[脸书](https://www.facebook.com/acloudguru)，[在 YouTube 上订阅云专家](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)的每周 AWS 更新，并在 [Discord](http://discord.gg/acloudguru) 上加入对话。也可以看看我们的[免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)，每月更新！

本周 AWS 还发生了什么？查看下面的视频，了解有关 Babelfish for Aurora PostgreSQL 和 EC2 支持访问 Red Hat 知识库的详细信息。继续牛逼吧，云大师们！