# 人工智能和机器学习:AWS vs Azure vs GCP

> 原文：<https://acloudguru.com/blog/engineering/aws-vs-azure-vs-gcp-artificial-intelligence-and-machine-learning>

我们的[云提供商比较](https://acloudguru.com/videos/cloud-provider-comparisons)系列中的这篇文章进入了云提供商的超级动态空间——人工智能和机器学习。人工智能(AI)和机器学习(ML)将海量数据处理与几乎无限的计算能力和按需付费的经济模式相结合。要了解 AWS、Azure 和 GCP 的人工智能和人工智能服务，请继续阅读。

* * *

* * *

## 启动你的职业发展

[从 ACG](https://acloudguru.com/pricing) 开始，通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室来启动您的机器学习生涯。(你将开发的智能没有半点虚假！)

* * *

## AI 和 ML 是一回事吗？

主流媒体经常交替使用人工智能和机器学习。但它们不是一回事。人工智能是我们对以自动化方式模拟人类思维和决策的追求。正如 Arthur Samuel(他在 1959 年创造了这个术语)解释的那样，ML 是“在没有明确编程的情况下赋予计算机学习能力的研究领域。”换句话说，ML 是我们可以用来尝试实现人工智能的一种方法。

* * *

## 机器学习的成分是什么？

那么，让一个 ML 系统运转起来需要哪些核心要素呢？

简而言之:

1.  大量数据。
2.  对数据应用计算或算法方法。
3.  知识(知道自己在做什么)。

不太久以前，机器学习的能力是高度专业化的，而且非常昂贵。只有政府和几所大学负担得起。

但是云计算已经成功地将这些工具带到了任何有网络连接的人的身边。今天，您可以使用云提供商开发的点击式工具来管理海量数据并利用巨大的计算能力。最棒的是，您只需为您需要的特定部分付费。云提供商也创造了一些交钥匙服务，让我们通过一个简单的 API 调用就可以利用非常强大的 ML 技术。

我们将在三个不同的领域比较 AWS、Azure 和 GCP 的 AI 和 ML 产品:**机器学习构建模块服务**、**机器学习平台**和**机器学习基础设施**。

### 机器学习构建模块服务

机器学习构建模块是您可以使用的服务，而无需首先了解很多关于机器学习的知识。大多数人从机器学习积木开始，因为进入的门槛太低了。

这些块可以通过 API 调用或使用云提供商的 SDK 获得。我们将在下面讨论的所有提供者都为他们的机器学习服务提供 rest APIs。

让我们看看他们各自带来了什么:

#### 语音到文本和文本到语音

对于语音转文本，AWS 有一项名为[亚马逊转录](https://aws.amazon.com/transcribe/)的服务。Azure 和 GCP 都将他们的产品命名为(或许很明显)语音转文本。

对于将文本转换为语音，AWS 服务名称是 [Amazon Polly](https://aws.amazon.com/polly/) ，而 Azure 和 GCP 有文本到语音。

#### 聊天机器人

不管你喜不喜欢，聊天机器人作为客户支持的第一线已经变得司空见惯。云提供商正在通过创建服务来支持和改进聊天机器人，从而帮助聊天机器人提供更好的体验(或者至少不那么令人失望)。

AWS 称其 chatbox 服务为 [Amazon Lex](https://aws.amazon.com/lex/) ，Azure 有[语言理解](https://azure.microsoft.com/en-us/services/cognitive-services/conversational-language-understanding/)，GCP 提供 [Dialogflow](https://cloud.google.com/dialogflow) 。

#### 翻译

值得庆幸的是，翻译服务已经走过了漫长的道路。).它们现在是非常标准的产品。云提供商翻译服务的名字非常简单:AWS 有[亚马逊翻译](https://docs.aws.amazon.com/translate/latest/dg/what-is.html)，Azure 包括[翻译器](https://docs.microsoft.com/en-us/azure/cognitive-services/translator/translator-overview)，GCP 提供[翻译](https://cloud.google.com/translate)。

#### 文本分析

文本分析服务采用自然语言(我们经常相互交谈的方式)，并从中提取某些主题、话题和情感。AWS 的文本分析服务是[亚马逊理解](https://aws.amazon.com/comprehend/)，Azure 的是[文本分析](https://azure.microsoft.com/en-us/services/cognitive-services/text-analytics/)，而 GCP 的是[自然语言](https://cloud.google.com/natural-language/docs)。

#### 文件分析

文本分析的发展是文档分析。在文档分析中，机器学习用于总结文章或检测表格中的信息。AWS 产品名为 [Amazon Textract](https://aws.amazon.com/textract/) ，Azure 有[文本分析](https://azure.microsoft.com/en-us/services/cognitive-services/text-analytics/)和[表单识别器](https://azure.microsoft.com/en-us/services/form-recognizer/)用于数据提取，GCP 有[文档 AI](https://cloud.google.com/document-ai) 。

#### 图像和视频分析

这些服务可以识别图像中的物体和人物，绘制人脸地图，或者检测潜在的不良内容。

AWS 在其 [Rekognition](https://docs.aws.amazon.com/rekognition/latest/dg/what-is.html) 产品下捆绑了图像和视频分析。与此同时，Azure 提供[计算机视觉](https://azure.microsoft.com/en-us/services/cognitive-services/computer-vision/)和 [Azure Face](https://docs.microsoft.com/en-us/azure/cognitive-services/face/overview) 索引器服务。GCP 分别称他们的图像和视频服务为视觉服务和视频服务。

#### 异常检测

计算机非常擅长检测异常情况，但通常你必须告诉它们要注意什么。云提供商使用机器学习来创建服务，这些服务可以观察一系列事件或数据，并找出数据集中的不同之处。这个过程称为异常检测。

你会在 AWS 中通过 [Amazon Lookout](https://aws.amazon.com/lookout-for-metrics/) 系列服务和[欺诈检测器](https://aws.amazon.com/fraud-detector/)找到这一功能。在 Azure 上，这个服务是[异常检测器](https://azure.microsoft.com/en-us/services/cognitive-services/anomaly-detector/)和[度量顾问](https://azure.microsoft.com/en-us/services/metrics-advisor/)，GCP 的版本是[云推理](https://cloud.google.com/inference)。

#### 个性化

推荐引擎正在成为电子商务网站的一个流行补充。难怪云提供商试图在这方面做一些繁重的工作。

AWS 基于他们为其商业网站开发的相同技术为亚马逊提供个性化服务。同时，Azure 有[个性化器](https://azure.microsoft.com/en-us/services/cognitive-services/personalizer/)，GCP 有[推荐 AI](https://cloud.google.com/recommendations) 。

有一点要记住:你的建议只有在你能把数据输入到你的系统中的时候才是好的。

事实上，上述所有服务都是如此。如果您的源数据是粗略的，最终结果可能会非常令人失望！

* * *

### 机器学习平台

当我们谈论机器学习平台时，我们指的是 ML 从业者使用的工作台和工具。这类似于开发人员使用 IDE 和一些库来编写代码。

对于机器学习来说， [Jupyter Notebook](https://jupyter.org/) 是数据科学家事实上的工作台。不出所料，所有三家云提供商都提供 Jupyter 笔记本电脑或一些稍微更名的版本作为其平台的一部分。

另一个全面的一致性是支持主要的机器学习框架，包括 TensorFlow、MXNet、Keras、PyTorch、Chainer、SciKit Learn 等。云提供商在其平台中集成了安全性、协作和数据管理等功能。

![](img/72a57644649887c2a262d429c9b176b0.png)

#### 指导模型开发

对于那些刚刚开始 ML 之旅的人来说，云提供商已经投资了一些温和的介绍。比如 AWS 的“刚刚入门”服务叫做 [SageMaker Autopilot](https://aws.amazon.com/sagemaker/autopilot/) ，Azure 有 [Automated ML](https://azure.microsoft.com/en-us/services/machine-learning/automatedml/) 和一个叫做[Azure Machine Learning designer](https://azure.microsoft.com/en-us/services/machine-learning/designer/)的拖拽工具，GCP 有一系列指导模型创建工具，他们称之为 [AutoML](https://cloud.google.com/automl) 。

#### 全 ML 工作台

如果你是一个经验丰富的专业人士，不需要训练轮，AWS 提供 [SageMaker Studio](https://aws.amazon.com/sagemaker/studio/) ，Azure 有[机器学习笔记本](https://docs.microsoft.com/en-us/azure/machine-learning/samples-notebooks)，GCP 提供 [AI 平台](https://cloud.google.com/ai-platform/docs/technical-overview)。

* * *

* * *

#### MLOps

另一个最近得到很多关注的功能是 MLOps，相当于机器学习的 DevOps。AWS 把他们的[叫做 SageMaker MLOps](https://aws.amazon.com/sagemaker/mlops/) ，Azure 的简单来说就是 [MLOps](https://azure.microsoft.com/en-us/services/machine-learning/mlops/) ，GCP 有[管道](https://cloud.google.com/resources/mlops-whitepaper)。

#### 增强人工智能

AWS 还拥有[增强人工智能(亚马逊 A2I)](https://aws.amazon.com/augmented-ai/) ，这是我们在其他平台上还没有看到的东西(尽管这肯定只是时间问题)。增强人工智能是一种利用真实、活生生、会呼吸的人类的力量来帮助改善机器学习服务的方式。

这里有一个*非常实用的*例子:

比方说，你已经确定你的机器学习模型在识别愤怒的雪貂的图像方面大约有 95%的准确性，但你需要有 100%的准确性。对于 ML 模型的可信度低的情况，你可以把有问题的雪貂图片交给一个活生生的人，他可以判断雪貂是否生气。

【添加 Scott 的《ACG 计划》剧集中愤怒的雪貂形象？]

* * *

### 机器学习基础设施

所有的云提供商都非常喜欢各自机器学习平台的容器，这是有充分理由的。集装箱相对较轻，便于携带，可以方便地搬运。

这三个提供者都为特定版本的 ML 框架提供了按钮式容器部署，并针对训练、验证和推理进行了优化。如果你更喜欢 DIY，所有的提供商都有针对所有主要框架的平台优化虚拟机。后者是大多数人使用的，如果他们已经有一个在内部训练的模型。

#### 五金器具

机器学习有点像云提供商的军备竞赛。这三家公司都倾向于优化硬件，每家提供商都声称具有卓越的性能和经济性。所有提供商都提供不同级别的 CPU 和 GPU 虚拟机类型。此外，一些公司还投资了专用集成电路(ASIC)和现场可编程门阵列(FPGA)形式的专用硬件。

像往常一样，这里有一个权衡。这些专门的硬件平台确实擅长机器学习任务，但从经济角度来说，它们对其他任何事情都不太有用。基于 CPU 和 GPU 的机器更加灵活，并且通常是人们在开发和改进他们的 ML 模型时首先使用的。

#### 机器学习的可解释性和偏见

尽管其固有的承诺和机会，开发高质量的 ML 模型确实很难。如果你碰巧做错了，那么 ML 产生的决定可能会从稍微尴尬到完全不道德，既有道德原因，有时也有监管原因。

我们需要能够解释我们的 ML 模型如何做出决策。从业者称之为可解释性，幸运的是，云提供商有工具来帮助解决这个问题:

* * *

## 更多 ACG ML 培训资源

机器学习是一个快速发展和迭代的空间，云甚至加速了这一过程。如果你刚刚开始你的人工智能之旅，请在 ACG 平台上查看[机器学习简介](https://acloudguru.com/course/introduction-to-machine-learning)(由你真正的)。

然后，在你有了基本的东西之后，选择你的云并深入研究。我们在 AWS、Azure 和 GCP 有很多关于 ML 产品的课程和动手实验。

* * *

![studying for certifications](img/83945e1f8b70362e52b1f1832e910ee4.png)

*The AWS Certified Machine Learning Specialty is one of the most valuable certs out there. ACG Training Architect Scott Pletcher shares [his tips and tricks](https://acloudguru.com/blog/engineering/recertification-experience-aws-certified-machine-learning-specialty) on how to get certified (and re-certified).*

* * *

您也可以开始您的 [ACG 免费试用](https://acloudguru.com/pricing)或查看[本月的免费云培训](https://acloudguru.com/blog/news/whats-free-at-acg)。在 YouTube 上订阅云专家[的每周云新闻，在](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1)[脸书](https://www.facebook.com/acloudguru)上关注我们，在 [Twitter](https://twitter.com/acloudguru) 上关注我们，在 [Discord](http://discord.gg/acloudguru) 上加入对话。