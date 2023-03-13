# 如何用 Amazon SageMaker |一个云专家建立一个网飞风格的推荐引擎

> 原文：<https://acloudguru.com/blog/engineering/how-to-build-a-netflix-style-recommendation-engine-with-amazon-sagemaker>

你有没有想过网飞是怎么给你推荐电影的？作为一名技术人员，我一直很好奇。我知道机器学习是背后的原因，我想知道是否同样的方法可以在云大师上推荐课程。我对这个想法非常感兴趣，以至于把它作为一个# [CloudGuruChallenge](https://acloudguru.com/blog/engineering/cloudguruchallenge-machine-learning-on-aws) 。这是一个有趣的挑战，也是探索机器学习的一个很好的方式。为了深入了解 AWS 上用于机器学习项目的服务和平台，有[亚马逊机器学习课程](https://acloudguru.com/course/aws-certified-machine-learning-specialty)。请继续阅读，查看我的推荐引擎代码。

## 品味问题:亚马逊网络服务(AWS)上的机器学习

网飞会根据你的观看历史、其他有类似爱好的成员观看的内容以及电影的元数据(如流派、类别等)来提供推荐。这些相同的原则可以很容易地应用于课程推荐。我们跟踪课程的观看历史和元数据。唯一缺少的部分是一种简单的方法来比较学生，以确定他们是否有相似的品味。幸运的是，聚类，一种机器学习技术，可以用来将每个学生分类到特定的组中。

为了开始这个学习冒险，我和我的同事[朱莉·埃尔金斯](https://twitter.com/julieaelkins)合作，使用机器学习和[亚马逊 SageMaker](https://aws.amazon.com/sagemaker/) 来解决这个挑战。在这次冒险中，我们学到了很多东西，并制作了一个引擎的概念证明(POC ),该引擎使用机器学习向学生推荐课程！我们的 POC 会根据您观看和掌握的内容，以及您所分配的学习群中的其他人观看和掌握的内容，向您推荐标题。真的很酷！

## 课程推荐引擎的好处

为什么首先要考虑建立一个课程推荐引擎？当然是为了个人学习挑战！

随着个人成长和发展，一位云专家最近推出了与 Linux Academy 的新组合平台[，提供比以前多 250%的课程、470 多个测验和考试以及 1，500 多个实践实验室！您将如何浏览所有这些内容？支持机器学习的推荐引擎可能就是帮助你的工具。](https://acloudguru.com/blog/news/announcing-the-new-a-cloud-guru)

我们的总体希望是，支持机器学习的推荐引擎将提高课程的收视率和学生参与度，因为我们推荐的课程是根据您的兴趣和掌握程度专门定制的。

## 大局

如果你不熟悉 AWS 机器学习，它允许计算机研究数据，并找到可能隐藏的趋势和模式。

* * *

*提示:要了解更多关于机器学习的知识，请观看[这一集凯莎的《科尔纳》](https://youtu.be/NS77H80avLI)来了解速度。*

* * *

让这个解决方案起作用的关键是我们选择的机器学习技术，它允许我们像学生一样分组(或群集)。有几种机器学习技术(监督、非监督、强化、转移等。)以及可供选择的学习算法。我们根据可访问的数据点选择我们的技术，并根据我们预期的结果(即学生分组)选择学习算法。我们采用无监督学习作为我们的技术，因为我们的数据没有被标记，并且 [K-means](https://scikit-learn.org/stable/modules/clustering.html#k-means) 作为学习算法，因为我们需要根据相似性将我们的学生分组到特定数量(或 **k** 数量)的簇(或组)中。

我们选择的构建机器学习模型的工具是亚马逊 SageMaker。我们选择亚马逊 SageMaker 是因为它提供运行 [Jupyter 笔记本](https://jupyter.org/)的计算实例。幸运的是，SageMaker 设法创建了实例和所需的所有相关资源。我们使用笔记本实例来准备数据并运行聚类算法。

那么，它是如何工作的呢？K-means 学习算法接收学生在所选类别(如 AWS、Python、containers、DevOps、机器学习等)的课程上取得的进展。

然后，学习算法根据其识别的相似性将学生聚类(或分组)到学习组中。想象一下，每个学生通过一个神奇的漏斗进行评估。魔法漏斗决定了学生应该被放在哪个学习小组(或集群)里。

在机器学习算法评估了每个学生之后，我们就剩下了截然不同的群体。

展望未来，我们称这些集群为学习小组。课程推荐将基于学生的指定学习小组。

## 产生学习小组的步骤

让我们回顾一下创建学习小组的步骤。首先，我们获取数据，然后准备数据，最后，我们将数据输入机器学习算法，以产生分组。下面详细说说每一步。

### 我们的数据

机器学习项目最重要的部分是拥有可信的数据。在这个概念验证中，我们使用了员工数据。为云专家工作的一个很酷的好处是，我们可以免费访问我们创建的内容！我们总是在学习新的东西，所以我们有大量的数据输入到机器学习算法中！我们从两个数据文件开始:**课程. csv** 和**学生. csv** 。

*注意:我想强调的是，在这篇博文中，这个例子中提供的数据文件已经被匿名化并稍微简化了。*

#### 课程清单

[**Courses.csv**](https://github.com/linuxacademy/content-recommendation-engine/blob/master/data/courses.csv) 包含课程及其相关类别的列表。

#### 学生名单

[**Students.csv**](https://github.com/linuxacademy/content-recommendation-engine/blob/master/data/students.csv) 包含我们的员工已经观看的课程以及相关进度的列表。

### 数据准备

数据点提供了一个很好的起点。虽然我们有这些数据，但是这些文件对机器学习来说还不够好。我们需要处理和准备数据，以便学习算法可以轻松找到趋势和模式。SageMaker 足够灵活，允许我们这样做，所以我们推出了 SageMaker Jupyter 托管的笔记本实例，并开始编写 Python 代码。

为了处理数据，我们导入了必要的库。然后，我们将 **courses.csv** 导入到一个名为 pd 的 [Pandas DataFrame](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html) 中，并显示前几行。

提示:Pandas 是一个 Python 数据分析库，它提供了一个表格数据结构，用于通过 DataFrame 操作数据。

```
# Import the course data
courses_df = pd.read_csv('data/courses.csv')

#review first few records to verify import
courses_df.head()
```

![](img/03d1241357f556bbf329439070e080d9.png)

*Image 14: Initial records from courses.csv*

然后，我们检查数据中的空记录并删除它们。我们不希望学习算法从丢失数据的记录中学习，因为这可能导致算法找到不正确的模式。

```
#View records that are NaNcourses_df[courses_df.categories.isnull()]
```

![](img/e9e930e487f68445874c621e6051d800.png)

*Image 15: Rows with empty records*

```
courses_df.dropna(subset=['categories'], inplace=True)
```

接下来，我们将 **students.csv** 导入到 Pandas DataFrame 中，并通过打印前几行来验证数据。

```
students_df = pd.read_csv('data/students.csv')students_df.head()
```

![](img/d99a8b15d529f46c60138dd51cbd8e28.png)

*Image 16: Student watch data*

### 数据检查和可视化

在处理数据时，掌握领域知识非常重要，因为这有助于您轻松发现和解决问题。有许多方法可以探索和了解您的数据。我们决定使用[Matplotlib](https://matplotlib.org/)——一个基于 Python 的数据可视化库——和其他技术来更好地理解我们的数据，特别是寻找模式和异常值。

#### 数据分布

我们使用直方图来更好地理解数据集上**课程 id**和**学生 id**的分布。

```
plt.hist(students_df.courseId)
```

![](img/791d88ef0a82f3e9676473bfa3b90662.png)

*Image 17: Course Id histogram*

```
plt.hist(students_df.studentId)
```

#### ![](img/b2a180d1059a5116ec523b8fd96254b3.png)

*图 18:学生 Id 直方图*

#### 学生水平分析

我们对课程的受欢迎程度很好奇，所以我们打印了观看课程#73 的学生。

```
students_df[students_df.courseId == 73]
```

![](img/278f7f9c2626efe4e69afc7962599bfc.png)

*图 19:课程 73 成绩*

接下来，我们想了解每个学生观看了哪些课程。我们建立了一个交叉列表，用来显示某组数据出现的频率。

```
pd.crosstab(students_df.studentId,students_df.courseId)
```

![](img/e81be685894ba95d0b6ef1bd8932b2f7.png)

*图 20:课程 73 成绩*

接下来，我们想了解哪些学生看了最多的内容。我们统计了学生 Id 在数据集中出现的次数。

```
students_df.groupby('studentId').size()
```

![](img/cf469b748e0d51bf8ba79cc66a324d45.png)

*图 21:按学生 Id 计数*

接下来，我们想了解学生层面的活动。例如，我们选择了 61 号学生来了解他们的手表历史。

```
students_df.loc[students_df['studentId'] == 61]
```

![](img/98e4b15a3905b97568392ae70d8d41da.png)

*图 22:学生活动*

#### 课程水平分析

接下来，我们想找出哪些课程最受欢迎。我们统计了 courseId 在数据集中出现的次数。

```
students_df.groupby('courseId').size()
```

![](img/db7cb2269e18bcc02572458122b1a95b.png)

*图 23:按 id 统计球场看球次数*

最后，我们想了解哪些学生观看了特定的课程。在这种情况下，我们选择了课程#5。

```
students_df.loc[students_df['courseId'] == 5]
```

![](img/cb4d55e57d64d02a538542b754523161.png)

*图 24:课程#5 的详细信息*

### 数据转换

现在我们对数据有了很好的理解，我们可以进入下一步，即转换数据供机器使用。不幸的是，机器学习算法无法在当前呈现的数据文件中找到趋势和模式。这两个文件是脱节的，需要合并成一个文件，显示所有学生和所有类别的类别观看时间。为了做到这一点，需要一点 Python 代码。

我们创建了一个函数来返回不同类别的列表。

```
def get_list_of_categories(courses):
    category_list = []

    for category in courses.categories.str.split('|'):
        for name in category:
            if name not in category_list: 
                category_list.append(name.strip())

    return category_list
```

我们还创建了一个函数，为每个类别创建一个唯一的列名。

```
def get_column_name_list(category_list):
    column_name = []

    for category in category_list:
        column_name.append('avg_' + category.strip() + '_watch')

    return column_name
```

然后，我们使用我们创建的带有附加逻辑的两个函数来计算所有学生和类别的观看时间。

```
#category watch time across ALL students across ALL categories
def get_all_category_watch_time(students, courses):
    category_progress = pd.DataFrame(columns = ['studentId'])
    category_list = get_list_of_categories(courses)
    column_names = get_column_name_list(category_list)

    #add studentId to list of columns
    column_names.insert(0,'studentId')

    for category in category_list:        
        course_categories = courses[courses['categories'].str.contains(category)]

        #determine the average watch time for the given category; retain the studentId
        avg_watch_time_per_user = students[students['courseId'].isin(course_categories['courseId'])].loc[:, ['studentId', 'progress']].groupby(['studentId'])['progress'].mean().round(2).reset_index()      

        #merge the progress for the given catetgory with the prior categories
        category_progress = category_progress.merge(avg_watch_time_per_user, on='studentId', how='outer')

    category_progress.columns = column_names
    return category_progress

# Calculate the average rating all categories per user
category_watch_time_df = get_all_category_watch_time(students_df, courses_df)
category_watch_time_df 
```

### ![](img/79a608450a092e1c1fdf7f3d9b8c7e33.png)

*图 25:所有学生和类别的类别观看时间*

然后，我们分析了我们最喜欢的学生#61 的手表时间。

```
category_watch_time_df.loc[category_watch_time_df['studentId'] == 61]
```

![](img/05c9e1602ba176fcc888fba7d12c4d51.png)

*图 25:学生#61 的类别观看时间*

在查看数据时，我们注意到学生没有观看的课程的值为 NaN 因此，我们将 NaN 转换为 0 手表时间。机器听不懂 NaN，但它能听懂 0。

```
#replace NaN with 0
category_watch_time_df = category_watch_time_df.fillna(0)
```

然后我们删除了 studentId，因为它在聚类(或分组)过程中没有任何好处。

```
#remove student id from dataframe
category_watch_time_list = category_watch_time_df.drop(['studentId'], axis=1)
```

我们只剩下最终的训练数据。一台机器可以从中学习！

![](img/d451aacea02e2d9c8dabb3d2361db672.png)

*图 26:最终转换数据的摘录*

### 培养

现在我们已经有了机器学习算法可以学习的格式的数据，我们开始使用 K-means 学习算法的训练过程。我们选择 [Scikit-learn](https://scikit-learn.org/stable/) 是因为它对于初学者来说非常容易学习，并且它们的 K-means 实现对于我们的数据集来说简单而高效。

根据 K-means 的要求，我们将数据转换为列表。

```
# Turn our dataset into a list
category_watch_time_list = category_watch_time_list.values
print(category_watch_time_list)
```

![](img/6b2d34caf1ee5e7458d44bd709583262.png)

*Image 27: Data as a list *

然后我们引入了 K-Means。

```
# Import KMeans
from sklearn.cluster import KMeans
```

接下来，我们创建了 K-Means 的一个实例，并将算法设置为查找 20 个聚类(或组)。使用 K-means 时，结果可能会随着每次运行而变化。为了抵消变化的结果，我们将 random_state 设置为 0，这使得我们的结果是可重复的。

```
# Create an instance of KMeans to find 20 clusters
km = KMeans(n_clusters=20, random_state=0)
```

然后，我们使用该实例对学生进行聚类，并将结果存储在预测中。预测将包含为每个学生分配的分类。

```
# Use fit_predict to cluster the dataset
# Returns a cluster prediction for each student / ie cluster labels
predictions = km.fit_predict(category_watch_time_list)
```

最后，我们打印了指定的集群。

```
print(predictions)
```

### ![](img/237eeaa2780972efb839880756205136.png)

*图 28:分配的集群*

### 将学生 ID 映射到集群编号

现在我们有了集群，我们需要将这些集群映射回 studentId。首先，我们将 [NumPy](https://numpy.org/) 数组转换为 Dataframe。

```
cluster_df = pd.DataFrame(data=predictions)
cluster_df.columns = ['assigned_cluster']
cluster_df
```

然后，我们合并数据帧以确定分配的簇。我们还删除了不必要的列。

```
student_cluster_df = pd.DataFrame(columns = ['studentId', 'assigned_cluster'])
student_cluster_df = pd.concat([cluster_df, category_watch_time_df], axis=1)
student_cluster_df = student_cluster_df[student_cluster_df.columns[student_cluster_df.columns.isin(['studentId', 'assigned_cluster'])]]
student_cluster_df
```

![](img/a8be57a96c036ab5124ccfd393df4130.png)

*Image 29: Assigned clusters by studentId*

### 聚类分析

接下来，我们希望更多地了解机器学习算法定义的每个聚类。我们使用了多种方法来确定这一点。

首先，我们计算一个聚类在数据集中出现的次数。

```
#count the amount of times a cluster appears in the dataset
student_cluster_df.groupby('assigned_cluster').size()
```

![](img/223f61f3fd3e7795c77c65430f668363.png)

*Image 30: The most popular clusters*

#### 绘图簇

然后我们绘制了聚类图来观察可视化效果。

```
#plot the data
plt.scatter(category_watch_time_list[:,0],category_watch_time_list[:,1], c=km.labels_, cmap='rainbow')
```

#### ![](img/377589c2821938d0cb97fdaf430522ed.png)

*图 31:聚类图*

#### 探索集群#6

然后我们选择了第 6 类，沿着已知的维度进一步探索和研究学生的特征。我们对第 6 组学生之间的共性感到好奇。

```
#What are the commonality between the students in cluster 6
#show students assigned to Cluster #6
student_cluster_df = student_cluster_df.loc[student_cluster_df['assigned_cluster'] == 5]

#Get only the student progress records that appear in cluster 6
cluster6_students_df = students[students['studentId'].isin(student_cluster_df['studentId'])]

#print students
cluster6_students_df
```

![](img/6ebd4dc0f3a2cfe2bf4ad0cc5a2f1e96.png)

*Image 32: Students assigned to cluster #6*

然后我们把那个集群的学生看的和掌握的课程都抽了出来。我们利用 90%以上的观察百分比来做出这一决定。

```
#convert progress percentage string to numeric data
cluster6_students_df['progress'] = cluster6_students_df['progress'].str.rstrip('%').astype('float') / 100.0

#limit to only courses that are above a 90% watch rate
cluster6_students_df = cluster6_students_df.loc[cluster6_students_df['progress'] > .90]

cluster6_students_df
```

#### ![](img/dd3444ca6e9d5f4388ea89a525feca41.png)

*图 32:观看率超过 90%的球场*

#### 跨集群浏览类别

现在我们有了第 6 组学生观看和掌握的课程列表。接下来，我们通过获取学生观看的课程类别来研究集群中的类别。

```
#Get the course categories for courses watched (course Id) by students in cluster 

cluster6_courses_watched_df = courses[courses['courseId'].isin(cluster6_students_df['courseId'])]

category_list = get_list_of_categories(cluster6_courses_watched_df)
print("The amount of categories for Cluster 6: ", len(category_list))
print("The categories in Cluster 6", category_list)
```

![](img/89e64de78bbf1bbb0bdb2dc2c15451b7.png)

*Image 33: Course categories for cluster 6*

第 6 组的学生喜欢 AWS、认证、云、开发、无服务器、编程、数据库和人工智能课程。

现在，我们已经了解了用户被分配到哪个群以及与该群相关联的课程类别，我们可以在每个学生访问平台时根据他们被分配的群向他们推荐课程。例如，如果登录的学生是集群#6 的成员，那么我们向该学生推荐跨 AWS、认证、云、开发、无服务器、编程、数据库和 AI 的课程。该建议说明了他们所观看和掌握的内容，以及他们的集群成员所观看和掌握的内容。

### 代码示例

完整的代码和数据文件可以在 GitHub 的[内容推荐引擎](https://github.com/linuxacademy/content-recommendation-engine)中找到。

### 未来的增强

未来可以对 POC 课程推荐引擎进行多项增强:

*   该引擎不仅可以推荐课程，还可以推荐动手实验、项目、博客帖子、网络剧集等等。
*   目前，分组仅仅基于学生的进步；然而，学生对课程的评价也可以用来做出明智的决定。
*   聚类也可以在开始观察日期和最后观察日期被告知，以确定某人是否真正喜欢一门课程。例如，他们是在周末狂看一门课程，还是花了几个月才完成？这些信息对聚类很有用。
*   集群可以用来和你的同行组成学习小组。想象一下在未来的会议上能够见到您的集群成员？多酷啊。

## 下一步:了解机器学习的更多信息

你准备好开始机器学习了吗？探索 A Cloud Guru 库中的以下课程，了解更多关于机器学习的知识。

**[机器学习入门](https://acloud.guru/overview/intro-machine-learning)**
在你的第一个机器学习项目上感觉头大？纠结于所有的数学术语？ACG 的[机器学习简介](https://acloud.guru/overview/intro-machine-learning)将教你机器学习词汇和你需要快速掌握的技能。

**[AWS 认证机器学习专业 2020](https://acloud.guru/overview/aws-certified-machine-learning-specialty)** 通过 [AWS 认证机器学习专业](https://acloud.guru/overview/aws-certified-machine-learning-specialty)考试，并获得数据工程、数据分析、机器学习建模、模型评估和 AWS 部署的最佳实践。不需要数学博士学位！

**[绝对初学者的机器学习](https://acloud.guru/overview/machine-learning-for-absolute-beginners)** 不需要技术诀窍。这门 ACG 课程目前是免费的，它将为你提供理解[什么是机器学习](https://acloud.guru/overview/machine-learning-for-absolute-beginners)(什么不是)——以及它能为你的业务或职业带来什么的基础知识。