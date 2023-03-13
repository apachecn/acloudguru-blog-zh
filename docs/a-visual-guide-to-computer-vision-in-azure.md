# Azure 中的计算机视觉视觉指南

> 原文：<https://acloudguru.com/blog/engineering/a-visual-guide-to-computer-vision-in-azure>

什么是计算机视觉？如何使用 Microsoft Azure 将计算机视觉功能集成到您的应用程序和工作流中？在本帖中，我们将用一种为视觉学习者设计的方法来解释这一点。

之前，我已经在 ACG 博客上分享了 Azure 基础知识的视觉介绍和 Azure 数据工厂的视觉指南。今天，我们将在微软 Azure 中分解计算机视觉。

#### 关于视觉辅助线

我们中 65%的人有视觉学习能力，这意味着我们可以更快地从图像中吸收信息，因此可以更长时间地保留和回忆信息。视觉指南是高分辨率(海报大小)的图像，它使用文本和插图的组合来概述主题或内容资源。你可以把它们想象成 [*sketchnotes*](https://en.wikipedia.org/wiki/Sketchnoting) (视觉笔记)，它们在学习之旅开始时提供主题的“全景”视图，帮助你建立联系并确定模式，以提高你对所学内容的理解、回忆和记忆。

想要发现其他可视指南或获得新指南的通知吗？在推特上关注 [@SketchTheDocs](https://twitter.com/sketchthedocs) 。

## 微软 Azure 中的计算机视觉是什么？

Azure 中的计算机视觉视觉指南利用了两个主要资源:同名的[微软学习模块](https://docs.microsoft.com/en-us/learn/paths/explore-computer-vision-microsoft-azure/?WT.mc_id=mobile-30244-ninarasi)，以及认知服务下的[微软文档页面](https://docs.microsoft.com/en-us/azure/cognitive-services/computer-vision/overview?WT.mc_id=mobile-30244-ninarasi)。**你可以在这里** **下载高分辨率(海报大小)版本** [**。**](https://aka.ms/visual/azure-computer-vision/download)

本指南最适合用来预定您的学习旅程。在进入用代码强化概念的[动手练习](https://docs.microsoft.com/en-us/learn/paths/explore-computer-vision-microsoft-azure/?WT.mc_id=mobile-30244-ninarasi)之前，把它作为预读材料(让你的头脑准备好相关的术语和工作流)。然后，将它作为复习后的资源来测试您的回忆，并找出覆盖范围或理解方面的差距。或者直接打印出来挂在墙上——或者用作桌面壁纸。把它当作一个方便的、简略的参考，可以补充你从其他来源学到的知识。现在让我们深入技术领域！

## 计算机视觉和 Azure 认知服务

**计算机视觉**是人工智能的一个领域，软件系统被设计成*使用相机、图像和视频来视觉感知世界*。

这里的挑战是，当人类和计算机看同一个物体时，他们会看到不同的东西。当人类看到一个苹果(物体)时，机器会看到一组像素值(图像*颜色*数据)。为了让机器更好地理解图像数据*代表什么*，我们使用像素值作为*数字特征*来训练机器学习模型。

该模型的行为类似于模式检测功能，以概率方式将计算机友好的特征(像素值)映射到人类友好的标签(对象、属性)。当我们给这个模型输入图像时，它现在可以用相关的*置信度*值*预测*一个相关的标签。在某种意义上，我们已经教会了计算机像人类一样“看”图像。

[**Azure 认知服务**](https://docs.microsoft.com/en-us/azure/cognitive-services/what-are-cognitive-services?WT.mc_id=mobile-30244-ninarasi) 是 Azure 基于云的服务的总括产品类别，帮助您将这种智能构建到您的应用程序或产品中。服务有客户端库 SDK(针对 Java 和 JavaScript 等流行语言)和 REST APIs(针对其他语言)，它们被分为五个领域:*视觉、语音、语言、决策和搜索。*我们的重点是 Vision，目前有三项服务:

*   [Azure 计算机视觉](https://docs.microsoft.com/en-us/azure/cognitive-services/computer-vision/?WT.mc_id=mobile-30244-ninarasi)——使用*已有的*高级图像分析算法。
*   [Azure Custom Vision](https://docs.microsoft.com/en-us/azure/cognitive-services/custom-vision-service/?WT.mc_id=mobile-30244-ninarasi) 构建、改进和部署*您自己的*图像分类器。
*   [人脸](https://docs.microsoft.com/en-us/azure/cognitive-services/face/?WT.mc_id=mobile-30244-ninarasi)——使用预先存在的先进的*人脸*算法来检测和识别人脸。

[**Azure Computer Vision**](https://docs.microsoft.com/en-us/azure/cognitive-services/computer-vision/overview?WT.mc_id=mobile-30244-ninarasi)是一种云规模的服务，提供对一组图像处理高级算法的访问。给定一个输入图像，该服务可以返回与感兴趣的各种*视觉特征*相关的信息。根据您的主要目标，您可以通过以下功能探索这项服务:

视觉指南(以及相关的[学习路径](https://docs.microsoft.com/en-us/learn/paths/explore-computer-vision-microsoft-azure/?WT.mc_id=mobile-30244-ninarasi))探索了以下练习子集:

* * *

## 获得更好的职业生涯所需的 Azure 技能。

掌握现代技术技能，获得认证，提升您的职业生涯。查看我们当前的[免费课程](https://acloudguru.com/blog/news/whats-free-at-acg-june-2021)或[获得 7 天免费试用](https://acloudguru.com/pricing)，与 ACG 一起推进您的云计算职业生涯。

* * *

### Azure 应用人工智能服务

快速浏览一下可视化指南，就可以看到第六个应用场景— [用表单识别器分析收据。但是 Azure 认知服务下没有列出这样的服务。那么，这在 Azure 机器学习服务生态系统中处于什么位置呢？](https://docs.microsoft.com/en-us/learn/modules/analyze-receipts-form-recognizer/?WT.mc_id=mobile-30244-ninarasi&ns-enrollment-type=LearningPath&ns-enrollment-id=learn.wwl.explore-computer-vision-microsoft-azure)

答案就在 2021 年 5 月微软大会上推出的[新产品类别](https://docs.microsoft.com/en-us/azure/applied-ai-services/?WT.mc_id=mobile-30244-ninarasi)中:**应用人工智能服务。**目标是 [*通过*](https://techcommunity.microsoft.com/t5/azure-ai/accelerating-the-time-to-value-with-azure-applied-ai-services/ba-p/2377309)*[在 Azure 认知服务](https://docs.microsoft.com/en-us/azure/applied-ai-services/why-applied-ai-services#what-is-the-difference-between-applied-ai-services-and--cognitive-services?WT.mc_id=mobile-30244-ninarasi)的基础上构建，同时将技术与特定任务的人工智能或针对特定用例定制的业务逻辑相结合，加快人工智能的应用时间* 。结果是一个*开箱即用的人工智能解决方案*来解决常见的业务挑战，而不需要开发人员每次都以编程方式将它们连接起来。然而，由于它们建立在 Azure 认知服务之上，开发者总是可以选择从头开始创建可比较的定制解决方案。

目前，有六个应用人工智能服务选项，包括:

*   [表单识别器](https://docs.microsoft.com/en-us/azure/applied-ai-services/what-are-applied-ai-services?WT.mc_id=mobile-30244-ninarasi#azure-form-recognizer)–自动从图像和文档中提取和输入结构化数据。
*   [Metrics Advisor](https://docs.microsoft.com/en-us/azure/applied-ai-services/what-are-applied-ai-services?WT.mc_id=mobile-30244-ninarasi#azure-metrics-advisor)–在时序数据中执行数据自动化和异常检测。
*   [认知搜索](https://docs.microsoft.com/en-us/azure/applied-ai-services/what-are-applied-ai-services?WT.mc_id=mobile-30244-ninarasi#azure-cognitive-search)–云级搜索，内置人工智能功能，可搜索所有类型的内容。
*   [沉浸式阅读器](https://docs.microsoft.com/en-us/azure/applied-ai-services/what-are-applied-ai-services?WT.mc_id=mobile-30244-ninarasi#azure-immersive-reader)–旨在提高所有学习者阅读理解能力的包容性工具。
*   [机器人服务](https://docs.microsoft.com/en-us/azure/applied-ai-services/what-are-applied-ai-services?WT.mc_id=mobile-30244-ninarasi#azure-bot-service)–使用预建组件快速创建可定制的对话体验。
*   [视频分析器](https://docs.microsoft.com/en-us/azure/applied-ai-services/what-are-applied-ai-services?WT.mc_id=mobile-30244-ninarasi#azure-video-analyzer)–构建由视频智能支持的自动化应用。

## 在 Microsoft Azure 中使用计算机视觉

视觉指南的结构与[学习路径](https://docs.microsoft.com/en-us/learn/paths/explore-computer-vision-microsoft-azure/?WT.mc_id=mobile-30244-ninarasi)提供的六个示例(模块)相匹配。在这一节中，我们将简要探讨每个应用程序，并为动手练习做好准备。

### **1。使用计算机视觉服务分析图像**

[本模块](https://docs.microsoft.com/en-us/learn/modules/analyze-images-computer-vision/?WT.mc_id=mobile-30244-ninarasi)关注计算机视觉服务的核心价值主张— *图像分析*。使用这个服务端点，您的应用程序(客户机)提交一个图像，并获取图像中各种可视特征(和属性)的详细信息。客户端还可以执行一系列与图像处理相关的任务。您可以做的事情包括:

*   **生成字幕:**获取你的图片的人性化*描述*(对 *alt-text* 有用)
*   **标记视觉特征:**获取可以作为图像元数据的*属性*
*   **检测物体:**认为有标记，但用*定位*被识别的物体(包围盒坐标)
*   **检测品牌:**针对*商业标识*(参考数据库)进行专项对象检测
*   **检测人脸:**想专门检测对象为*的人脸*(预测年龄，识别名人)
*   **对图像进行分类:**使用父子层次结构对图像进行分类(类别选项的有限集合)
*   **检测特定领域内容:**支持的领域模型包括*地标*和*名人*
*   **光学字符识别:**从图像中打印或手写的内容区域读取*文本*

请注意，这是一个基本的人脸图像分析服务。对于高级人脸算法，可以直接使用 Azure Cognitive Services 的 **Face** 服务端点，并执行更复杂的任务，如检测情绪、头部姿势或是否有面罩。

作为开发人员，从创建相关资源开始——您有两种选择。如果您计划只使用图像分析功能，或者希望单独跟踪每个认知服务的成本和利用率，请使用 Azure 计算机视觉资源(有针对性的)。如果您计划使用许多认知服务功能，并希望方便地一起管理它们，请使用 Azure 认知服务(broad)资源。对于**图像分析**用法的实践代码教程，[从这里开始](https://docs.microsoft.com/en-us/learn/modules/analyze-images-computer-vision/3-analyze-images?WT.mc_id=mobile-30244-ninarasi)。

### **2。使用自定义视觉服务对图像进行分类**

[本模块](https://docs.microsoft.com/en-us/learn/modules/classify-images-custom-vision/?WT.mc_id=mobile-30244-ninarasi)关注定制视觉服务的核心价值主张— *图像分类*。这是一种学习技术，您为机器提供训练数据(图像和相关类别)，并训练它检测和发现将数字特征(像素数据)与人类概念(类别标签)联系起来的模式。经过训练的模型可以*发布*以向客户公开服务端点。使用这个服务，客户端发布一个图像，并获得一个*预测的*类(带有相关的置信度得分)。

使用自定义视觉服务，您可以通过以下两种方式之一上传训练数据来训练您的图像分类器:使用门户(基于无代码 UI 的工作流)或使用 SDK 或 REST API(代码优先的方法)。使用包括两个步骤:*训练*(创建模型)和*预测*(发布模型)。和以前一样，您可以使用专用的定制视觉服务资源，或者通用的 Azure 认知服务资源，用于任一阶段或两个阶段。你甚至可以随意混合搭配。对于**图像分类**用法的实践代码教程，[从这里](https://docs.microsoft.com/en-us/learn/modules/classify-images-custom-vision/?WT.mc_id=mobile-30244-ninarasi)开始。

* * *

* * *

### **3。使用定制视觉服务检测物体**

[该模块](https://docs.microsoft.com/en-us/learn/modules/detect-objects-images-custom-vision/?WT.mc_id=mobile-30244-ninarasi)主要是为*物体检测*创建自定义模型。通常，这需要深度学习技术的高级知识和大型训练数据集，但使用定制视觉服务可以让我们在没有数据科学专业知识的情况下用更少的图像实现这一点。与上面的自定义视觉服务示例中采取的步骤类似，这涉及准备您的训练图像集、将数据上传到 Azure(通过门户或使用 SDK)、训练和验证模型，然后将其发布到服务端点供客户端使用。

关键区别在于，对象检测涉及识别图像中对象的*位置*及其分类。这意味着需要准备训练集(图像)来识别对象的边界框(坐标)，这可能很耗时。使用自定义视觉，您可以将图像上传到门户网站，并获得关于检测到对象的区域的建议；只需拖动或调整边界框区域即可提高精确度。一旦你有了一个训练好的初始集合，尝试一个*智能标签*方法，使用 Azure 计算机视觉服务为剩下的部分建议标签和边界框。对于**对象检测**用法的实践代码教程，[从这里开始](https://docs.microsoft.com/en-us/learn/modules/detect-objects-images-custom-vision/?WT.mc_id=mobile-30244-ninarasi)

### **4。使用人脸服务检测和分析人脸**

[这个模块](https://docs.microsoft.com/en-us/learn/modules/detect-analyze-faces/?WT.mc_id=mobile-30244-ninarasi)着重于使用高级算法进行*面部分析*，这些算法超越了 Azure 计算机视觉中获得的基本属性。这就像对象检测的一个特例，其中感兴趣的对象是人脸。通过人脸算法，您可以执行人脸*检测*(返回包含人脸的图像区域)、人脸*分析*(返回鼻子、眼睛、眉毛、嘴唇等位置的面部标志。)和人脸*识别*(以基于人脸的认证应用为例)。

Azure Cognitive Services 为检测和分析人脸提供了不同的选项-用于基础分析的计算机视觉(age)，用于视频内容中人脸分析的视频索引器，以及用于最广泛的人脸分析功能的 face。

人脸服务可以检测、识别和验证人脸。它可以找到其他相似的人脸，或者根据相似性对人脸进行分组。面部服务分析返回属性，包括年龄、情绪、面部毛发、眼镜、头发、头部姿势、化妆、遮挡以及图像相对于检测到面部的模糊和曝光。对于**面部分析**用法的实践代码教程，[从这里开始](https://docs.microsoft.com/en-us/learn/modules/detect-analyze-faces/3-create-face-solutions?WT.mc_id=mobile-30244-ninarasi)

### **5。使用计算机视觉服务阅读文本**

这个[模块](https://docs.microsoft.com/en-us/learn/modules/read-text-computer-vision/?WT.mc_id=mobile-30244-ninarasi)专注于 Azure 计算机视觉服务的光学字符识别能力，以*读取图像中的印刷和手写文本*。基于所涉及的文本量，有两个 API 可以使用:T4 OCR API 和读取 API T5。

### **6。使用表单识别器服务分析收据**

这个[模块](https://docs.microsoft.com/en-us/learn/modules/analyze-receipts-form-recognizer/?WT.mc_id=mobile-30244-ninarasi)侧重于一个更加实用的人工智能解决方案，该解决方案将 OCR 文本阅读能力与特定领域的*预测模型*相结合，用于解释表单数据，实现智能表单处理和收据和发票等文档的自动化工作流。
T5[表单识别器](https://docs.microsoft.com/en-us/azure/cognitive-services/form-recognizer/)既提供了*预建的收据模型*，又支持*定制模型。*预建模型被训练为识别在美国地区流行的基于英语的普通收据格式。它提取并返回交易的时间/日期、商家信息、税款和支付总额等属性。相比之下，定制模型识别并提取被分析文档中的键/值对和表数据。它可以使用您自己的数据进行训练，定制返回的属性以匹配表单的结构和上下文，基本训练需要至少 5 个表单样本。对于**收据分析**用法的实践代码教程，[从这里开始](https://docs.microsoft.com/en-us/learn/modules/analyze-receipts-form-recognizer/3-analyze-receipts?WT.mc_id=mobile-30244-ninarasi)

* * *

[![Complete guide to the Cloud and Dictionary ](img/93ebf63b88ab7fbd48705a01952ba688.png)](https://get.acloudguru.com/cloud-dictionary-of-pain)

[**获得痛苦的云词典**](https://get.acloudguru.com/cloud-dictionary-of-pain)
说云不一定要努力。我们分析了数百万份回复，找出了最容易让学生出错的术语和概念。在这个[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)中，你会发现一些最令人头疼的云术语的简洁定义。

* * *

## 总结和后续步骤

这是对[六模块学习路径](https://docs.microsoft.com/en-us/learn/paths/explore-computer-vision-microsoft-azure/?WT.mc_id=mobile-30244-ninarasi)和[可下载的](https://aka.ms/visual/azure-computer-vision/download)视觉指南的快速回顾，该指南提供了“大图”快速参考，以补充您在 Azure 中学习计算机视觉的实践练习。想继续吗？以下资源可以提供帮助:

此外，请查看这些 ACG 课程和动手实验:

#### 关于作者

Nitya Narasimhan 是计算机工程博士，拥有超过 20 年的软件研发经验，涉及分布式和普适计算、移动和 web 应用程序开发。她目前是微软开发人员关系团队的云倡导者，在那里她花时间进行移动和跨平台开发(针对 Azure 和微软 Surface Duo)、可视化故事讲述以及支持我们出色的开发人员社区。她是 ACG 第 21 批蓝色建设者之一。