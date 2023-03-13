# 什么是云迁移？-策略和工具

> 原文：<https://acloudguru.com/blog/business/what-is-cloud-migration>

云迁移。这是什么意思？**云迁移是将数字资产(如数据、工作负载、IT 资源或应用程序)移动到云基础架构的过程。**云迁移通常是指将工具和数据从旧的传统基础设施或内部*数据中心迁移到云中。

* *on-premises 有时缩写为“On-prem ”,通常被称为“on-premise ”,尽管从语法角度来看这是不正确的*

虽然“云迁移”通常是指将东西从内部迁移到云中，但它也可以指从一个云迁移到另一个云。迁移可能涉及移动全部或部分资产。它还涉及到很多其他的事情。这就是我们编写本指南以涵盖云迁移所有内容的原因。

## **云迁移解释:什么、为什么和如何**指南

想了解更多关于云迁移的信息吗？这本云迁移初学者指南涵盖了从对云迁移一无所知到对云迁移有所了解的一切。

我们将从简单明了的[云基础知识](#intro)开始，带您深入了解[云迁移战略](#strategies)和[迁移工具和服务](#tools)，从更高的层面了解如何成功完成云迁移。此外，你将获得方便的资源，带你从获得要点到把它拍下来。

目录

## 云简介

* * *

## **等等。。。云到底是什么？**

### 云——通常被用作“云计算”的简称——指的是通过互联网访问的计算机服务池。该池可按需访问和自助服务，无需设置即可即时访问服务。有了云，企业曾经不得不在内部部署的计算机可以存储在世界各地的大型数据中心*中。

**“数据中心”是一个术语，用于描述专用于容纳计算机系统及其必要设备的空间。*

不同于服务器*室或服务器储藏室，你可能会在任何给定的办公室的锁着的门后找到计算机系统存储单元，数据中心主要用于存放计算机设备。它们通常都很大，是专门为保持大量技术在最佳状态下运行而设计的。

* *“轻踩刹车。什么是服务器？”你可能会问。服务器基本上是重型计算机，设计为一直运行，通常专用于单一任务，如存储、发送或处理数据。*

*[学习服务器](https://acloudguru.com/course/concepts-for-securing-your-servers)非技术环境下的安全！*

这些数据中心由专注于运行数据中心的公司管理，减少了对本地 IT 资源(即计算机，而不是人)的需求。(你可能仍然需要一些人，尤其是知道如何使用云计算的人。)

*对升级或开始云数据之旅感兴趣吗？云专家的 [AWS 数据学习路径](https://acloudguru.com/learning-paths/aws-data)提供适合初学者和高级专家的定制课程！*

* * *

**为什么叫云？**

* * *

### 当然，这些计算机服务实际上并不存在于天空中。(你可能知道，但以防万一。。。)[“云”](https://www.computerworld.com/article/2726701/where-did--cloud--come-from-.html)这个名字其实来源于 20 世纪 70 年代概念网络图中使用的符号。

云和互联网一样吗？

### 云有时与术语“互联网”互换使用，但是，从技术上来说，云不是互联网。相反，云使用互联网来传递资源。但当人们在互联网上做事情时，他们可能会使用云服务——从查看 Gmail 到上传狗狗照片到 Instagram，再到在网飞上播放亚当·桑德勒电影。

企业在云中运行哪些类型的服务？

![Screenshot of Intro to Cloud video](img/8cb5004bdc5f3df963a7cb8c629c6a79.png)

[*Explore the basics and benefits of cloud in this free course.*](https://acloudguru.com/course/intro-cloud-computing)

### 那么，你能用云做什么呢？几乎你可以用电脑或服务器做的任何事情都可以作为一项服务在云中使用。

服务的复杂性各不相同，从存储组成网页的数字片段到使用强大的硬件来执行资源密集型任务，如使用[人工智能](https://acloud.guru/learn/b8caf0e5-1776-4948-a9ba-2a80826461eb)和[机器学习](https://acloud.guru/learn/intro-machine-learning)到[分析商业数据](https://acloud.guru/learn/2e6aed11-7e20-443c-ad02-117957fe1f8a)以获得洞察力。

**为什么企业要迁移到云？**

* * *

## 企业迁移到云的原因多种多样。但是一个很大的原因是，在云中工作可以让你获得几乎无限的计算机资源。

一个非常简单的类比:**云就像电**

### 一个简单的思维练习是把这个几乎无穷无尽的计算能力和存储库想象成电力。当然，你可以通过运行发电机自己发电，但是硬件的前期成本是昂贵的。然后，您必须让它保持运行，这需要一定水平的专业知识和花费在持续维护上的时间。如果它坏掉了，你就不走运了——除非你真的挥霍了，有一台备用发电机随时待命。

但就像你(可能)消耗电力的方式一样，如果你和你周围的人都需要电力，那么将电力生产的设置和日常管理外包出去更有意义。然后，你和所有需要用电的邻居只需轻轻一按开关就能接通电。你可以自由使用你需要的东西，并且只为你使用的东西付费。有很多人要来度假吗？你可以得到他们需要的所有电力，没问题。电力公司会给你保险的。他们专注于快速高效地为您供电，因此您可以专注于您需要做的事情。(如果你不喜欢类比，就重读最后两段，把“电”换成“云”。)

简单明了的是:云提取并随时提供它。您可以获得服务器和计算机服务，而无需购买、维护和管理硬件，也无需让员工专门从事随之而来的低级管理工作。

**云计算有哪些类型？**

![Screenshot of Cloud Migration Fundamentals course](img/da473d469e69c67f3c4764adb7b1d193.png)

*[This short course will guide you through the ins and outs of cloud migrations.](https://acloud.guru/learn/3f72b5d3-596c-4540-b43c-643004dba153)*

* * *

## 如果您将云视为公用事业(如电力)，那么您基本上是在考虑公共云，这只是云部署模型的一种类型。但是公有云和私有云的[区别是什么？什么是混合云？你问得很有趣。](https://acloudguru.com/blog/business/public-cloud-vs-private-cloud-whats-the-difference)

**公有云**

### 使用公共云，服务由第三方供应商(称为云服务提供商)通过公共互联网拥有和运行。这些服务可以是免费的，也可以是对任何想使用或购买它们的人按使用付费的。[公共云的优势](https://acloudguru.com/blog/engineering/the-basic-advantages-of-public-cloud)是巨大的，这可能解释了为什么它是最常见的部署类型。

*   公有云的例子有[亚马逊网络服务(AWS)](https://acloudguru.com/blog/engineering/what-is-amazon-web-services-aws) 、[微软 Azure](https://acloudguru.com/blog/engineering/what-is-microsoft-azure) 、[谷歌云平台(GCP)](https://acloudguru.com/blog/engineering/what-is-google-cloud-platform-gcp) 、阿里云、IBM 云、甲骨文云。
*   [公共云的优势](https://acloudguru.com/blog/engineering/the-basic-advantages-of-public-cloud)包括 24/7 全天候正常运行时间、按需付费的能力(这可以节省成本)、可扩展性和简化的基础架构管理，这意味着设置非常简单，无需购买和管理内部基础架构。
*   **私有云**

### 对于私有云，云资源仅由一个组织使用和拥有。这使得寻求最大控制或定制的政府和金融行业需要这种方法。私有云可以位于现场的数据中心，也可以由远程位置的提供商托管。

*   私有云提供商包括 Hewlett Packard Enterprise (HPE)、Dell、IBM、Oracle，以及公共云提供商领域的一些熟悉的名字，包括 AWS、Google 和 Microsoft。
*   **混合云**

### 混合云结合了私有云和公共云的元素，并允许资源在两者之间移动。混合云非常适合需要私有云元素(例如，敏感数据的监管要求)但仍希望访问[公共云及其巨大优势](https://acloudguru.com/blog/engineering/the-basic-advantages-of-public-cloud)的组织。

*   与私有云一样，这种模式需要一些真正的 IT 技能，并且可能需要使用现场硬件，从而削减了公共云的一些成本优势。这也给等式增加了另一层复杂性。
*   **多云**

### 多云是在单个环境中使用多个云服务。例如，这可能意味着混合使用公共云和私有云，或者混合使用公共云提供商，以减少对单一提供商的依赖，或者实现多个提供商的优势。

*   多云是最受企业欢迎的云策略。
*   多云与混合云有何不同？多云是指使用多种服务(比如来自 AWS 和 Azure 的服务)，混合云是指使用多种部署模式(比如使用公有云和私有云)。
*   **云服务模式有哪些？**

* * *

## SaaS、PaaS 和 IaaS 之间有什么区别？它们是三种不同的云服务模式、云服务类别或云计算类型——只是三个看起来很滑稽的缩写词的不同术语。不管你想怎么称呼它们，理解这些是让你明白云能做什么的坚实一步。

“aaS”代表“作为服务”最简单的形式是，这意味着将这部分技术转移到云端。例如，**软件**即服务意味着将通常驻留在计算机上的**软件**转移到云上。

**SaaS**

### 软件即服务，或 SaaS，是通过互联网提供的软件。本地计算机、平板电脑或手机上未安装任何内容；不需要任何人来管理补丁或更新之类的事情。它只是工作。

*   SaaS 的例子包括 Dropbox、Salesforce、G Suite 应用程序(如 Gmail)和微软 365。
*   想在不出洋相的情况下说说话吗？大声说出来的时候，SaaS 要么被拼出来(S-A-A-S)，要么被读作“sass”
*   **PaaS**

### PaaS，即平台即服务，是开发者的软件构建基础。只有 BYO 应用程序和数据。PaaS 在云中提供了一块白板，让开发人员可以创建、部署和扩展应用程序，而不必担心基础架构、存储或操作系统等问题。

*   PaaS 的例子包括 AWS Elastic Beanstalk、OpenShift 和 Google App Engine。
*   Paas 怎么说？大声说出 PaaS 时，它要么被拼出来(P-A-A-S)，要么被读作“paz”或“pass”
*   **IaaS**

### 基础设施即服务(IaaS)意味着将基础设施迁移到云中。(想想:在云端租用服务器。)您的云提供商拥有硬件并负责管理和维护，因此您不必担心任何维护。

*   IaaS 的例子包括 AWS、微软 Azure、谷歌云平台、Rackspace 和 DigitalOcean。
*   IaaS 怎么发音？大声说出来的时候，IaaS 最常见的拼法是(I-A-A-S)——尽管有时会读作“eye-azz”
*   你是 IT 经理吗？Admin？IT 团队领导？一个云大师的 [AWS 高管学习路径](https://acloudguru.com/learning-paths/aws-executive)优惠 *[企业持续学习](https://acloudguru.com/platform)* *搭配* *定制课程适合初学者和高级大师！*

![Screenshot of Getting More Value from Cloud webinar](img/38e45785a551300935b94aac349c6d0a.png)

*[The shift to remote everything has accelerated cloud adoption. Watch this free on-demand webinar to see how to stay on top of it all.](https://go.acloudguru.com/how-to-get-more-value-from-cloud-adoption-webinar)* 

* * *

**迁移到云有什么好处？**

* * *

## **在基本层面上，云的优势通常围绕效率**，以最小的成本获得最大的成果。对于成功完成云迁移的[组织来说](https://go.acloud.guru/case-study-bundle)，收获的回报可能包括更高的可扩展性、更低的成本和安全性。

为了简单起见，我们将特别关注公共云的优势，尽管其中一些优势也适用于其他云部署模型。**以下是迁移到云的七大好处**。

1.**弹性和可扩展性**

### 云提高了[可扩展性](https://acloudguru.com/blog/engineering/scaling-the-hottest-app-in-tech-on-aws-and-kubernetes)，使组织能够根据需要或满足需求几乎即时地添加或删除资源。弹性与可扩展性密切相关，指的是快速扩展或减少计算机处理、内存和存储资源([数据存储优化](https://acloudguru.com/course/introduction-to-optimizing-data-storage-in-aws))以满足不断变化的需求，而无需考虑[云容量规划](https://acloudguru.com/course/linux-capacity-planning)的能力。弹性支持可伸缩性。

请这样想:用户的涌入可能会耗尽服务器的资源。使用传统的自托管硬件，请求将被拒绝。但是云实际上拥有无限的资源。这意味着服务器可以顺利地扩展以应对这一高峰。

缩放过程可以自动完成(称为自动缩放)，例如基于一天中的时间或正在使用的处理器资源量。

2.**成本节约和效率**

### 云让您能够只为自己使用的资源付费。(想想:开一辆优步而不是买车。)这使您可以访问那些需要花费太多时间和金钱才能保持的资源，这又与可伸缩性联系在一起。

传统的 IT 纵向扩展方法成本高昂。这需要计划；这可能需要几个月的时间，需要前期成本很高的硬件、维持其正常运行和冷却所需的电力，以及能够使其正常运行的熟练 it 人员。有了云，所有这些几乎都由您的云提供商瞬间完成。

但是云可扩展性真正让本地可扩展性望尘莫及的地方是大约*减少*资源。传统的 IT 基础架构可能需要足够的资源来应对高峰需求。(例如，一家零售商不得不为数据中心资源付费，以便为黑色星期五的购物高峰做好准备，尽管他们在一年中的其他 364 天都没有一半忙。)云基础架构可以随着一年、一月、一天或一小时的高峰和低谷而上下扩展。

请记住，如果没有适当的规划和执行，组织的[云支出可能会失控](https://acloudguru.com/blog/engineering/continuous-cloud-cost-optimization)，如果实施不当，云本身就不是省钱之举。然而，它无疑允许一个组织。。。

3.**从资本支出转向运营支出**

### 云将技术系统从资本支出(CapEx)转变为运营支出(OpEx)，或者从您持有几年就会贬值的投资(就像一堆收集蜘蛛网的昂贵硬件)转变为运营业务的常规持续成本(就像支付互联网费用)。对于那些希望尽可能多持有现金的企业来说，这是个好消息。(你可以和你的财务部门确认，但那可能是任何人工作的地方。)

4.**敏捷性和灵活性**

### 敏捷性在云环境中有几个不同的含义。“云敏捷性”通常用于描述快速开发、测试和启动业务应用程序的能力。但是云也让您能够灵活地快速响应需求的变化。

即使是小企业也可以使用大企业使用的强大工具。只需点击几下鼠标就可以获得新的服务，因此当新的需求、挑战或机会出现时，可以立即做出响应。

云还可以让拥有多个办公室的组织变得更加轻松，不再需要在每个位置设置基础架构。只要打开电源和网络，你的人就准备好了。这也使你的员工突然转向在家工作成为可能(看着你，2020)。

5.**性能、可靠性和弹性**

### 大型云服务提供商运营着一个世界范围的世界级设施网络，其中汇集了尖端技术。这确保了从保持低网络延迟到提供近乎无与伦比的数据备份和灾难恢复的一切。无论需要访问您的工具的人在哪里，云通常都会拉近他们的距离。

6.**安全性和合规性**

### 大多数云提供商都是大公司，大公司依赖他们。这就是他们特意考虑安全性和合规性的原因，包括保持对更新和趋势的了解，以确保您的敏感数据在云中是安全的。

公共云提供商通常会带来策略、技术和控制，这些都是对一般组织安全实践的巨大改进。这与针对几乎所有行业特定的合规性需求的考虑相匹配。

此外，如果设备被盗或放错地方，将数据保存在云中而不是硬盘上也可以防止数据受到危害。

7.**减少维护并简化 IT**

### 维护计算机硬件和软件是一项全职工作。字面上。有了公共云，您就不必让员工花费时间来维护与业务目标没有直接关系的繁琐设备。您的云服务提供商确保基础设施到位，因此您的技术奇才可以专注于推动业务成果。

准备好升级您公司的云了吗？

* * *

### 创建云创新文化，通过大规模实践学习加速云成功。使用最全面、最新的学习库、评估和[沙盒软件](https://acloudguru.com/platform/cloud-sandbox-playgrounds)对 10 或 10，000 人进行升级或再升级。

**我如何规划云迁移？**

* * *

## 如果没有[正确的战略](https://acloudguru.com/blog/business/10-slam-dunks-for-cloud-adoption)，您可能会失去实现预期云优势的机会。当公司转向云时，有许多[常见错误，拙劣的迁移可能意味着性能下降和成本增加。经常有报道称，超过一半的公司没有看到他们预期的云优势。这通常是由于迁移策略的失误和缺乏必要的云人才](https://acloudguru.com/blog/business/4-common-mistakes-when-enterprises-go-cloud)。

如果您正在寻找云迁移指南，无论您将使用何种类型的云以及何种云服务模式，都可以考虑以下三个基本原则:

**你在搬什么东西**

1.  **你为什么要移动它**
2.  你打算怎么做
3.  从更详细的层面来说，这是关于弄清楚迁移过程和给予规划足够的思考。

***需要准确了解整个组织的云计算能力？*** *从[云培训需求分析](https://acloudguru.com/platform/skills-assessments)开始，找出技能差距。尝试我们的技能评估，帮助您的团队在云计算领域取得更大成功。*

**云迁移流程是怎样的？**

![Screenshot of Cloud Migration Patterns webinar](img/f334adca4ae19dbfd01126cfab411b42.png)

*[Watch this free on-demand webinar to learn about the costs and complexities of rehosting, replatforming, and rearchitecting applications for the cloud.](https://go.acloudguru.com/cloud-migration-patterns-that-really-work-webinar)*

* * *

## **制作云迁移清单**

### 理想情况下，当迁移到云时，您不会即兴发挥。记录已经完成的工作和下一步要做的工作，以确保所有移动的部分都在它们应该在的地方结束。需要云迁移模板？这里有一些步骤要包括在您的云迁移清单中。

1.**评估“为什么”**

### 你为什么要转向云计算？这需要一个正式的商业案例！领导层必须清楚迁移的目的，并设定积极的目标来推动组织向前发展。这包括为您当前的 IT 基础架构创建一个基准，并形成一些云迁移关键性能指标(KPI)。这些将使[衡量您的云迁移成功](https://acloudguru.com/blog/engineering/measuring-cloud-success)成为可能。

2.**计划什么在移动以及如何移动**

### 评估您的环境中有什么，注意任何相互依赖，然后确定您将首先迁移什么以及如何迁移。看看哪些应用程序可以按原样迁移，哪些需要一些(或大量)返工，以及有哪些工具可以简化这些棘手工作负载的迁移。选择您的云部署模型以及各种工具和服务([参见下面的](#tools))。理想情况下，您会希望计算出将要迁移的东西的 ROI(投资回报),以及需要多长时间才能实现。

3.**迁移应用和数据**

### 是时候卷起袖子让你的手变得浑浊了。当您准备开始迁移时，通常最好从不太复杂或业务关键的东西开始。运气好的话，快速的胜利会让你兴奋不已，并在前进的道路上教会你一些东西。

应该使用下面介绍的[迁移策略之一](#strategies)来设计、迁移和验证应用程序。完成迁移后，您需要测试所有内容，并淘汰旧系统。这可能意味着一次运行两个环境，但你可以通过确保[你的云领导者](https://acloudguru.com/blog/engineering/how-to-assemble-your-cloud-migration-dream-team)准备好确认所有系统都在运行，并且能够[衡量你的云成功](https://acloudguru.com/blog/engineering/measuring-cloud-success)来避免这段时间被搁置太久。

4.现代化和前进

### 当您迁移应用程序时，继续努力找出您的新操作模型，关闭那些遗留系统，并继续向前推进。

云迁移策略有哪些类型？

* * *

## 云迁移有三种基本类型或模式。按照下面的顺序，它们从最容易和最快(有一些缺点)到更困难(有更大的好处)。

**提升和移动**

1.  **移动并改进**
2.  **淘汰并替换**
3.  让我们更深入地了解一下[云迁移策略](https://acloudguru.com/blog/engineering/the-cloud-architects-guide-to-cloud-migration)的类型以及每种策略的优缺点。

1.**提升和移位**(重新主机化)

### 一个[提升和转移](https://acloudguru.com/blog/business/what-is-lift-and-shift-cloud-migration)(也称为“再转移”)方法的优势是什么？它很快，需要最小的重构。但是(这是一个很大的但是)提升和转移的[缺点包括这样一个事实，即你可能会错过云原生的好处，因为你只执行了最少的必要更改。这意味着，从长远来看，您最终可能会为迁移的速度和方便性付出代价——至少与更彻底的方法相比是这样。](https://acloudguru.com/blog/engineering/the-lift-and-shift-shot-clock-cloud-migration)

[提升和转移](https://acloudguru.com/blog/business/what-is-lift-and-shift-cloud-migration)可用于简单、低影响的工作负载，尤其是云技术还远未成熟的组织。如果您当前的设置包含大量虚拟机，这相对简单。甚至有来自供应商的产品声称可以帮助您自动完成迁移(但是手动完成迁移过程可能是一个很好的学习练习)。好消息是，即使你匆忙地进行了升级和转移，一旦应用程序运行在云中，它们也更容易返工和优化。

2.**移动并改进**(重新平台化)

### 迁移和改进(或重新搭建平台)方法包括对应用程序进行一些现代化的更新，比如引入扩展或自动化，而不是全盘抛弃。乍一看，这种折中的方法似乎是更好的选择，但是它可能会导致迁移，在迁移中，您保留了所有的技术债务，却没有获得任何云原生的好处。

**3。推倒重来**(重构)

### 这种方法(也称为重构或重新架构)意味着从头开始重新构建您的工作负载，使其成为“云原生的”。这需要在时间和技能发展方面进行投资(特别是[更新和提升现有人才的技能](https://acloudguru.com/blog/business/build-your-own-unicorns))，但它会带来云计算的最大收益。

虽然每个组织和工作负载都是独一无二的，但是如果迁移到云的原因是为了利用其强大的优势和功能，那么拥抱云原生设计原则应该是您的方法。这意味着花时间去计划和做正确的事情:确保你的人有必要的技能来采取行动和重构你的代码。

**其他云迁移策略**

### **回购—** 获得了一个不会轻易迁移到云的传统应用程序？购买已经存在的新产品。

*   **退休—** 在审视了你周围的一切之后，你可能会发现有些事情你可以不承担任何后果。动手吧。节省资金，提高安全性，并让您的员工少一个必须学习使用的工具。

*   **保留—** 看到您还没有准备好退休，但也没有准备好迁移到云？以后再来看。不是拖延症。有些时候，让事情保持原样可能是有意义的。(毕竟，正如我们已经讨论过的，仅仅为了迁移到云而迁移到云可能会让您意识不到它可以提供的好处。)

*   **云到云的迁移** —这涉及到从一个云到另一个云的迁移，比如从 [AWS 到 Azure](https://acloudguru.com/blog/engineering/an-aws-users-guide-to-azure) 。

*   **逆向云迁移** —这种从云到现场数据中心的迁移也称为云遣返、去云或去云。

*   哪种工具用于云迁移？嗯，不止一个…多得多！像 AWS、GCP 和 Azure 这样的大型公共云提供商希望你迁移到他们的云中，所以他们为你提供了大量工具，让迁移尽可能轻松。

* * *

当然，他们也很乐意拿走你的钱，如果你想把钱投给他们的话。成本节约是迁移到云的潜在好处，但云成本也很容易失控。这就是为什么使用所有可支配的工具来规划您的需求和调整流程非常重要。在内部运行良好的东西在云中可能是代价高昂的错误。

云成本计算器可以帮助您在进行迁移之前先了解一下您的设置成本。查看您的公共云提供商提供的服务。例子包括 [AWS 定价计算器](https://calculator.aws/)、 [Azure 定价计算器](https://azure.microsoft.com/en-us/pricing/calculator/)和[谷歌云定价计算器](https://cloud.google.com/products/calculator)。

其他可以提前检查的工具包括(AWS) [AWS 可信顾问](https://aws.amazon.com/premiumsupport/technology/trusted-advisor/)和(Azure) [微软 Azure 顾问](https://azure.microsoft.com/en-us/services/advisor/)。这些为您提供关于云最佳实践的实时指导，还可以帮助您实现[成本优化](https://acloudguru.com/blog/engineering/covid-and-cost-optimization-lessons-from-leaders)，以及安全性和性能。

**AWS 云迁移工具**

## 亚马逊网络服务(AWS)提供哪些云迁移工具？如果你正在寻找亚马逊云迁移服务，这个云巨头有[一系列解决方案](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/migration-services.html)——包括大量[免费的](https://aws.amazon.com/free/migration/)——来帮助你开始迁移。

[**AWS 迁移枢纽**](https://aws.amazon.com/migration-hub/) —什么是 AWS 迁移枢纽？它可以让您跟踪 AWS 解决方案的迁移进度，帮助您选择合适的工具、跟踪指标等等。

*   [**AWS 应用交付服务**](https://aws.amazon.com/application-discovery) **—** 让 AWS 检查您的本地数据设置，为您的迁移做好规划。收集的数据经过加密，可从迁移中心访问。
*   [**AWS 服务器迁移服务**](https://aws.amazon.com/server-migration-service) —该服务可以轻松快速地将工作负载迁移到 AWS，尤其是在处理大规模服务器迁移时。
*   [**AWS 数据库迁移服务**](https://aws.amazon.com/dms) —轻松安全地将您的数据库迁移到 AWS。好处:源数据库在整个迁移过程中保持正常运行，最大限度地减少了停机时间。
*   [**云忍受迁移**](https://aws.amazon.com/cloudendure-migration/) —这种自动化的提升和转移解决方案免费 90 天。
*   还有几个迁移数据和文件的工具，包括 AWS Snowball、AWS Snowball Edge、AWS Snowmobile、AWS DataSync 和 SFTP 的 AWS Transfer。你可以从 [AWS](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/migration-services.html) 获得关于这些和其他服务的更多细节。你还可以通过认证更广泛地了解亚马逊及其服务[。](https://acloudguru.com/blog/engineering/which-aws-certification-should-i-take)

**微软 Azure 云迁移工具**

![Screenshot of AWS Cloud Migration course](img/18cfaf5c0e27dd5a1ced2b89e85b93ef.png)

*[Learn the techniques needed to migrate to AWS.](https://acloud.guru/learn/5098ebd2-3892-44b5-95c0-83c59454b6de)*

## 需要 Azure 云迁移工具？Azure 提供了大量的资源，包括工具、教程和视频。(我们也有一些[提示给那些希望将服务器迁移到 Azure](https://acloudguru.com/blog/engineering/4-tips-for-migrating-servers-to-azure) 的人。)

**[Azure Migrate](https://acloudguru.com/course/migrating-servers-to-azure)** —微软的内置迁移服务充当工具、进度跟踪、见解和指导的中心枢纽，以规划和成功迁移到云。下面介绍的大多数其他工具都集成到了这个中央仪表盘中。

*   **Azure Migrate:服务器评估**和**服务器迁移** —这些工具允许您评估服务器并将其迁移到 Azure，包括物理服务器和 VMware、Hyper-V、公共云和其他虚拟机。
*   [**数据迁移助手**](https://docs.microsoft.com/en-us/sql/dma/dma-overview) — DMA 有助于定位可能影响迁移的兼容性问题。它指出了不支持的特性、新特性，并帮助您规划数据库迁移的正确路径。
*   [**Azure 数据库迁移服务**](https://docs.microsoft.com/en-us/azure/dms/dms-overview) —将本地数据库迁移到 Azure 虚拟机。
*   [**Azure 数据盒子**](https://docs.microsoft.com/en-us/azure/databox/) —将大量离线数据移动到 Azure 云端。
*   [**Movere**](https://docs.microsoft.com/en-us/azure/migrate/migrate-services-overview#movere) —这个 SaaS 平台在 2019 年被微软收购。这是一个发现解决方案，可提高业务智能，以查看和控制整个环境。
*   如果你想在 Azure 中更全面地提高技能，[也许可以试试认证](https://acloudguru.com/blog/engineering/which-azure-certification-is-right-for-me)？

**GCP 云迁移工具**

![Screenshot of Azure Migrate course](img/25faa9f587df0b61492021b4fd7c7b85.png)

*[See how to use the Azure Migrate service to migrate workloads to Azure.](https://acloud.guru/learn/migrating-workloads-to-azure)*

## GCP 有两条不同的途径来简化云迁移规划。第一个(也是较新的选项)被称为[谷歌云快速评估&迁移计划(RAMP)](https://cloud.google.com/blog/products/cloud-migration/google-cloud-ramp-program-simplifies-cloud-migration) ，该公司将其描述为“整体的端到端迁移计划”。第二个选择是[谷歌云采用框架](https://cloud.google.com/adoption-framework)(你可以下载白皮书)和 15 分钟[云成熟度评估](https://digitalmaturitybenchmark.withgoogle.com/cloud/)。

准备好开始迁移到 Google 构建的云了吗？该公司有自己的迁移服务清单。

[**传输服务**](https://cloud.google.com/storage-transfer-service) —执行从在线和内部来源到谷歌云存储的大规模数据传输。

*   [**Transfer Appliance**](https://cloud.google.com/transfer-appliance/docs/2.0)—对于离线批量数据迁移，Transfer Appliance 允许您使用 100TB 或 480TB 型号安全地捕获、传送和上传数据。
*   [**为 Anthos**](https://cloud.google.com/migrate/anthos) 迁移—将现有工作负载迁移和现代化到容器。
*   [**为计算引擎迁移**](https://cloud.google.com/migrate/compute-engine) —让企业应用在谷歌云中运行，同时在后台迁移数据。无需返工即可验证、运行和迁移应用程序。
*   [**BigQuery 数据传输服务**](https://cloud.google.com/bigquery-transfer/docs) —让您的分析团队为 BigQuery 数据仓库奠定基础，并从您的 SaaS 应用中安排和自动化数据传输。
*   其他谷歌云迁移工具可以在[谷歌迁移中心网站](https://cloud.google.com/solutions/migration-center)上查看。如果你想更全面地了解 GCP，[也许可以试试认证](https://www.youtube.com/watch?v=YhhWBRr3iEg)？

云迁移面临哪些挑战？

![Screenshot of GCP Migration course](img/ad9a4a4d760c67af0d88e0c0a29741d9.png)

*[Get a crash course in migrating to Google Cloud.](https://acloud.guru/learn/842c8c5e-5c42-4e7c-ab5b-59e3fb872b62)*

* * *

## 预测潜在问题是云迁移策略的关键部分。有哪些常见的云迁移挑战？

**管理成本—** 云可以节省成本，但确定云的成本可能很棘手。云费用很容易被低估。不要只考虑迁移的成本，还要考虑迁移服务的成本、增加带宽的潜在需求以及未来的经常性开支。(适当的规划和[云成本优化](https://acloudguru.com/blog/engineering/continuous-cloud-cost-optimization)在这里大有帮助。)

*   **复杂性** —公共云通常更容易管理，但它可能会变得复杂(如果您开始引入混合云元素，它会变得更快)。您的人才需要能够管理您的云，并了解成功迁移所需的努力。

*   **依赖关系** —应用程序依赖关系变得非常复杂，并使迁移嘎然而止。云提供商发现工具可以确保您对他们了如指掌。

*   **传统应用** —一些应用对于云来说是一场噩梦。这就是评估*为什么*你要搬家*你要搬什么*变得至关重要的地方。决定你将保留什么，什么需要重建，什么可能值得重新购买。

*   **数据库** —将大量数据转移到云中需要时间。为了提供帮助，一些提供商提供了将您的数据物理复制到所提供的硬件上的选项，然后您就可以发货了。

*   **利益相关方的支持** —在云计算方面，你希望领导层致力于长期发展。这就是建立一个[云卓越中心](https://acloudguru.com/blog/business/3-phases-of-cloud-adoption)真正有回报的地方。
*   提升您的云计算智商

* * *

### 渴望更多的云知识？需要[自定进度的实践实验室](https://acloudguru.com/platform/labs)来获得真正的情境学习体验？无论您是希望了解更多知识的个人，还是希望提升数千人技能的组织的一部分，云专家都可以让您轻松掌握云技术。

[为您自己开始免费试用](https://acloudguru.com/pricing)，[查看您组织的计划](https://acloudguru.com/go/pricing/business)，或者仔细阅读我们轮流推出的[免费云课程](https://acloudguru.com/blog/news/whats-free-at-acg)，开始在实践中学习云。

此外，这里还有一些你可能会觉得有用的资源。

获得云认证会有很大的帮助，并且您已经获得了每个平台的途径。

关于迁移到云的其他有用资源: