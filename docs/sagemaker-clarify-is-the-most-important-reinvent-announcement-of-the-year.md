# SageMaker Clarify  re:Invent 2020 最重要的公告

> 原文：<https://acloudguru.com/blog/engineering/sagemaker-clarify-is-the-most-important-reinvent-announcement-of-the-year>

我们正处于 2020 年 AWS re:Invent 的第二周，这是机器学习第一次有单独的主题演讲！作为一名 AWS 机器学习英雄，我迫不及待地观看了主题演讲，以了解更多关于正在推出的新机器学习服务的信息。

当 Swami Sivasubramanian 宣布 [Amazon SageMaker Clarify](https://aws.amazon.com/sagemaker/clarify/) 通过检测和减轻数据集和模型中的偏差来扩展 SageMaker 的功能时，我简直欢呼雀跃。我相信亚马逊 SageMaker Clarify 是**今年 AWS re:Invent 最重要的公告**鉴于人工智能的广泛社会影响，更具体地说， [AWS 机器学习](https://acloudguru.com/course/aws-certified-machine-learning-specialty)。

## 为什么偏差检测在机器学习中如此重要？

SageMaker 在帮助机器学习从业者和数据科学家准备数据集、构建和训练定制模型以及在生产中部署和监控模型方面做得很好。然而，还没有简单的方法来检测偏差。

机器学习中的偏见最近一直处于许多讨论的前沿。我们已经看到像面部识别(其核心是机器学习)这样的尖端技术因偏见而被禁止；当面部识别系统准确地识别出除了有色人种之外的所有人时，偏向表面。为了让社会充分认识到机器学习的好处，必须在过程的早期检测和减轻偏见——在机器学习模型投入生产之前。

我总是警惕地测试我的模型的偏差，但现在有了一种可扩展和可重复的方法来检测和减轻偏差，这是非常令人兴奋的。Amazon SageMaker Clarify 允许您在机器学习模型开发过程的每个阶段评估偏差——在数据分析期间、训练之后和推断期间。

## 训练前检测偏差

有时，当处理新数据集时，需要花费时间来构建所需的领域级知识，以便检测可能导致偏差的异常和不平衡。亚马逊 SageMaker Clarify 承诺通过在训练的 之前检测数据集 ***中的偏差来提供帮助。这是非常令人兴奋的，因为一个有严重偏差的数据集首先不应该被用来训练一个模型！训练机器学习模型的时候别忘了，“垃圾进，垃圾出”！***

为了让 Amazon SageMaker Clarify 检测数据集中的偏差，您需要上传已经预处理和清理的数据(使用 Amazon SageMaker DataWrangler 等工具)。亚马逊 SageMaker Clarify 还承诺在 训练后检测模型 ***中的偏差。最重要的偏差检测特性——精确度差异(AD)——检测一组模型是否比另一组模型更精确！所有面部识别机型都应该使用该功能。***

## 预测的透明度

但是亚马逊 SageMaker Clarify 不止于此！过去，我很难解释为什么我的模型在推理过程中会做出某种预测。亚马逊 SageMaker Clarify 承诺通过帮助我“*解释特征值如何对预测结果做出贡献来解决这个问题，包括整体模型和个体预测*。这种透明度是真正的游戏规则改变者，有助于与使用我的模型的人建立信任。

总的来说，我对机器学习的未来感到非常兴奋，因为偏见检测处于最前沿！我迫不及待地想使用亚马逊 SageMaker Clarify 重新训练我现有的模型，并与您分享我的经验教训！如果你有兴趣探索其他 AWS re:Invent 机器学习会议(在 Swami 的主题演讲之外)，请查看我的[机器学习英雄指南](https://virtual.awsevents.com/playlist/1_eemqdcp9/188376503)。

*[投入你的邮箱](https://get.acloudguru.com/reinvent2020)获得一个 TL；ACG 发明的每一天的总结。*