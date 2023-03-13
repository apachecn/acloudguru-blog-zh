# # CloudGuruChallenge——AWS 上的机器学习|云专家

> 原文：<https://acloudguru.com/blog/engineering/cloudguruchallenge-machine-learning-on-aws>

*什么是[#云谷挑战](https://acloudguru.com/blog/news/introducing-the-cloudguruchallenge)？在这里获得一些背景和更多信息[。](https://acloudguru.com/blog/news/introducing-the-cloudguruchallenge)*

| **话题** | AWS 上的机器学习 |
| **创建者** | [**凯莎威廉姆斯**](https://www.linkedin.com/in/java-rock-star-kesha/) |
| **目标** | 用 amazon pagemaker 建立一个网飞风格的推荐引擎 |
| **结果** | 获得真正的机器学习和 AWS 技能，同时动手操作真实世界的项目，以添加到您的投资组合中 |
| **截止日期** | 2020 年 12 月 31 日 |

## 挑战步骤

你有没有想过网飞是怎么给你推荐电影的？我一直对幕后使用的机器学习技术和算法很好奇，这些技术和算法帮助我浏览了网飞上的数千部电影。

在这个挑战中，你将通过使用亚马逊 SageMaker 构建一个网飞风格的推荐引擎来提升你的 [AWS 机器学习课程](https://acloudguru.com/course/aws-certified-machine-learning-specialty)技能。无论你是第一次接触机器学习还是机器学习大师，这个挑战的某些方面都会让你的技能更上一层楼。所以，我们走吧！

你需要访问 AWS 环境和亚马逊 SageMaker。作为 [AWS 免费层](https://aws.amazon.com/sagemaker/pricing/)的一部分，你可以免费使用亚马逊 SageMaker。如果你以前从未使用过 Amazon SageMaker，你可以免费构建和训练你的模型。如果你不熟悉机器学习，看看凯莎的科尔纳在[的第一个视频，了解一下速度。我还建议在开始这个挑战之前探索一下](https://youtu.be/NS77H80avLI) [matplotlib](https://matplotlib.org/) ， [scikit-learn](https://scikit-learn.org/stable/) 和 [*k* -means](https://scikit-learn.org/stable/modules/clustering.html#k-means) 学习算法。

### **1。确定用例并获取数据**

确定你想推荐什么——是电影、课程、视频、商品还是其他。然后，找数据或者用自己的。有几个公共数据存储库，比如 AWS Marketplace 或 T2 的 UCI 机器学习存储库可能有你需要的数据。如果你想推荐电影，查看 [IMDb 数据集](https://www.imdb.com/interfaces/)和[下载](https://datasets.imdbws.com/)你需要的文件。你可能会发现**title.akas.tsv.gz**、**title.basics.tsv.gz**和**title.ratings.tsv.gz**特别有用。

### 2.创建 Jupyter 托管笔记本

为了开始数据检查过程，您将在 Amazon SageMaker 上启动一个 Jupyter 托管的笔记本。你可以使用 Python 和各种数据科学库，如 [NumPy](https://numpy.org/) 和 [Pandas 的 DataFrame](https://pandas.pydata.org/docs/user_guide/dsintro.html#dataframe) 来处理你的数据。

### 3.检查和可视化数据

获取数据的领域知识非常重要，这样您就可以轻松地检测到异常和异常值。有许多方法可以探索和了解您的数据。检查 [Matplotlib](https://matplotlib.org/) 。

### 4.准备和转换数据

下一步是将数据转换成机器可以学习的格式。您可能需要将杂乱的数据文件合并成一个文件，删除空值，将字符串转换成数字，或者做一些功能工程

### 5.火车

现在您已经转换了数据，使用您选择的机器学习算法开始训练过程。该算法应该对你的数据进行聚类或分组，以便你能够提出建议。取决于你如何解决这个挑战，你可能会发现*k*-意味着集群是有用的。亚马逊 SageMaker 提供了一个[*k*-means clustering](https://docs.aws.amazon.com/sagemaker/latest/dg/k-means.html)算法或者你可以探索 [scikit-learn](https://scikit-learn.org/stable/) 的[版本](https://scikit-learn.org/stable/modules/clustering.html#k-means)。

### 6.推荐

现在您已经确定了您的集群，请推荐产品。如果您推荐电影，这可能是 Python 代码，它分析集群以找到共性。一旦你理解了这些共性，你就能找到其他类似的电影来推荐。恭喜你走到这一步！

### **7。源代码控制**

现在您已经完成了，将您的数据文件和 Jupyter 笔记本加载到 [GitHub](https://github.com/) 以便我们检查您的推荐引擎。

### 8.清理资源

别忘了清理你的资源！至少，停止运行你的 Jupyter 笔记本，这样你就不会因为使用 Amazon SageMaker 而产生每小时的费用。

### 9.博客帖子

(非常重要)写一篇简短的博文，解释你的收获和应对挑战的方法。在 GitHub 上链接到您的项目，以便我们可以查看它。

## 当你完成的时候

你可以自己或与他人合作完成项目要求。欢迎在论坛或社交媒体上使用#CloudGuruChallenge 标签提问[！](https://acloud.guru/forums/cloud-guru-challenge/recent?p=1&opt_id=oeu1596472190462r0.43263125574439387)

当你完成项目的所有步骤后，在指定的[论坛](https://acloud.guru/forums/cloud-guru-challenge/recent?p=1&opt_id=oeu1596472190462r0.43263125574439387)主题中发布你的博客文章的链接。然后，我将能够在 LinkedIn 上为你在这个项目中展示的技能背书:机器学习、AWS 和亚马逊 SageMaker。(您还将有机会赢得一些超酷的奖品！)

这项挑战将无限期开放，但要在 LinkedIn 上获得支持并赢得奖品，你需要在 2020 年 12 月 31 日**之前[在论坛](https://acloud.guru/forums/cloud-guru-challenge/recent?p=1&opt_id=oeu1596472190462r0.43263125574439387)上链接你的博客文章**。

最重要的是，#CloudGuruChallenge 是免费的，任何人都可以使用:你所需要的就是[一个 ACG 免费会员](https://acloudguru.com/pricing)来发表你的论坛帖子。

## 资源

准备好做一些谷歌搜索，但如果你是 ACG 会员，这里有一些资源可以帮助你更好地使用机器学习、AWS 和 SageMaker:

你不需要执行这些额外的步骤来在挑战中“宣布胜利”，但是它们*将*帮助你的项目脱颖而出，并提供令人敬畏的额外学习。

1.  对项目进行排序，以便向用户推荐最相关的项目
2.  仅推荐用户尚未观看(或购买)的项目
3.  将您的集群知识集成到前端应用程序中，以进行电影(或产品)推荐。

## 最终外卖

这个挑战将是一个探索机器学习的有趣方式！

我一直很好奇网飞是怎么给我推荐电影的。在给你创造这个挑战之前，我已经自己解决了！如果你是机器学习的新手，这会很有趣。如果你已经是一名机器学习专家，你将有机会使用亚马逊 SageMaker 探索云中的机器学习。我迫不及待地想在这个挑战结束时与你分享我的推荐引擎代码，并回顾你是如何解决这个问题的！

熬过这一关，你就能在下一次求职面试中拿出一个精彩的故事。祝你好运！