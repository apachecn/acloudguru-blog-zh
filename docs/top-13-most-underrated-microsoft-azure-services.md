# 13 大最被低估的微软 Azure 服务

> 原文：<https://acloudguru.com/blog/engineering/top-13-most-underrated-microsoft-azure-services>

最近，我问了互联网一个问题。(不，如果我把毕生的积蓄都投在 NFTs 上就不会。)我想看看人们认为最被低估的微软 Azure 服务是什么。

为什么？因为有大约 200 种 Azure 产品和服务可供使用，并且深入了解一些我们可能有时甚至忘记存在的模糊玩具是很好的。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

要深入了解 Azure 提供的一些最佳服务，请观看 Azure 服务聚焦系列。但是要想浅尝一些被低估的天蓝色宝石，请继续阅读！

## 最被低估的微软 Azure 服务是什么？

众所周知，就科学准确性而言，Twitter 民意调查的排名仅高于预测体育赛事结果的[海牛](https://www.heraldtribune.com/story/news/local/sarasota/2021/02/02/bucs-chiefs-florida-manatees-and-otters-make-super-bowl-lv-picks/4345167001/)。因此，在这篇文章中，我想分享我对值得关注的默默无闻的[微软 Azure](https://acloudguru.com/blog/engineering/what-is-microsoft-azure) 服务进行的极其系统和深入研究的分析结果——以及一些理所当然被忽视的服务。

没有一个突出的选择，甚至没有前三名。但是当然，在互联网上，只有一个人是对的，其他人肯定都是非常非常错误的，所以我挑选了我最喜欢的建议，并给自己最后的发言权。(这么大功率！)

你可以在 Twitter 上看到完整的讨论[。或者你可以继续阅读这篇博文！你已经来了。为什么不多呆一会儿呢？我们有饼干…](https://twitter.com/larsklint/status/1430002588045381637)

排名不分先后，以下是有史以来最被低估的 Azure 服务的人民选择提名！

### 1.**事件网格**

如果“喜欢”是一种暗示的话，[事件网格](https://acloudguru.com/hands-on-labs/use-azure-event-grid-with-cloud-shell-powershell-and-cli)是一个受欢迎的选择，受到了[@汤姆克霍夫](https://twitter.com/TomKerkhove)和[@蒂亚戈科斯塔普](https://twitter.com/tiagocostapt)等人的支持，他们写道，“肯定是事件网格。我不再数我向客户演示的次数，以解决实际问题是一种简单的方法，但仍有许多专业人员不知道它的存在……”

他接着举了一个最近的例子来说明他是如何使用它的。“我用过微软。KeyVault . CertificateNearExpiry 事件来跟踪即将过期的证书，并通过调用证书提供商的 API 来自动续订。

事件网格爱 fest 继续， [@lars_almen 添加](https://twitter.com/lars_almen/status/1430448796299825157)，“事件网格。说真的，那是一个发电站。想做一个索赔核对模式吗？就利用这个事件。需要对成功的资源部署进行回调吗？这里，利用这个事件！需要推动数以百万计的自定义事件非常便宜，快速？把自己的话题勾起来！”

我的观点:我同意以上所有观点。Event Grid 是一项服务，初看起来复杂、令人生畏且难以掌控。然而，一旦你打开它的宝藏，可能性是巨大而有效的。

### 2. **Azure App 配置**

[@BenCurranDev](https://twitter.com/BenCurranDev) 建议 Azure 应用程序配置，[说](https://twitter.com/BenCurranDev/status/1430105525522362369)“当你正确使用它时，它是如此强大，从部署工作流中删除了如此多的 BS，但每个人和他的狗都在一个庞大的 json 文件中隐藏在一个公共存储帐户中。”

**我的观点**:虽然这绝对是真的，并且可以在调试应用程序时节省大量的时间，但是这也是一项相当昂贵的服务，尤其是对于较小的分布式系统。

### 3. **Azure 存储**

[@gmantri 说](https://twitter.com/gmantri/status/1430068568461234176)“[Azure Storage](https://acloudguru.com/course/azure-storage-deep-dive)——人们只是不知道这项服务有多重要，因为大量其他服务都依赖于它。”

[@flytzen 补充道](https://twitter.com/flytzen/status/1430633138997321737)，“Azure storage 拥有一些鲜为人知的漂亮特性，比如不可变 blobs、索引标签、伪 CDN 功能、客户端加密等。当我设计高性能、可扩展和弹性应用时，充分利用存储绝对是关键。”

**吾取**:完全同意。Azure 存储不仅是云基础设施的基础部分，也是持续提供的服务。如果使用得当，它非常便宜，而且非常稳定可靠。不要只把存储当回事，也不要看面值。

### 4.**蔚蓝堡垒**

ACG 自己的斯蒂芬·塞尼特(Stephen Sennett)提供了 T2 的蓝色堡垒(Azure Bastion)作为他的首选，[说:“这是完美的微软服务。AWS 会说“只需构建自己的”，GCP 会说“肮脏的非自动化农民”，不需要构建和修补虚拟机、配置规则或任何东西。只是给公司一些东西，让他们的云生活更轻松。”

**我的 take** :没错，堡垒很神奇。它从公共互联网中移除了基础设施的另一个元素，而公共互联网是任何云系统的最大攻击媒介。](https://twitter.com/ssennettau/status/1430405218391388167)

* * *

[![Complete guide to the Cloud and Dictionary ](img/93ebf63b88ab7fbd48705a01952ba688.png)](https://get.acloudguru.com/cloud-dictionary-of-pain)

[**得到痛苦的蔚蓝字典**](https://get.acloudguru.com/cloud-dictionary-of-pain)
说云不一定要硬。我们分析了数百万份回复，找出了最容易让学生出错的术语和概念。在这个[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)中，你会发现一些最痛苦的 Azure 术语的简洁定义。

* * *

### 5.**静态网络应用**

[@John_Papa](https://twitter.com/John_Papa) 提名静态 Web 应用，[说](https://twitter.com/John_Papa/status/1430322480091123712)“对开发者来说太棒了，甚至还有更多潜力！！!"三个感叹号很难辩驳！！！！(看到我在那里做了什么吗？)

[@TomVerhoeff](https://twitter.com/tomverhoeff) [同意](https://twitter.com/tomverhoeff/status/1430339031422930945)，补充“静态 app 与 CDN 的结合似乎也不太为人所知。”当被问及在静态网络应用前添加 CDN 可能有用的时候，他甚至更进一步提供了一些数据。

### 6. **Azure 政策**

[@skyalin](https://twitter.com/skyalin) [提名](https://twitter.com/skyalin/status/1430065437190942723)蔚蓝政策。当我追问是因为没人关心还是因为没人使用而低估了这一点时，他们补充道，“A 列有一点，b 列有一点。这是应该控制配置的第一件事，通常是在其他一切都实施后才考虑的，由于潜在的影响，进行更改为时已晚。”

[@ BenCurranDev](https://twitter.com/BenCurranDev)[补充](https://twitter.com/BenCurranDev/status/1430134922203656196):“你用 Azure Policy 能做的最好的事情，真的被很多人误解了。允许您根据治理规则部署核心基础架构的 DINE 策略对于大规模环境来说非常强大。”

### 7. **Azure SQL**

[@eHougaard](https://twitter.com/eHougaard) 建议 [Azure SQL](https://acloudguru.com/course/sql-deep-dive) 说:“这个简单:Azure SQL。它是在所有“花哨的”非 SQL 东西出现的时候出现的，但 Azure SQL 真的很棒！”

**我的观点**:这不是一个精彩的论点，但我确实同意 Azure SQL 是一个可靠的托管解决方案，它从 Azure“就能工作”。不过，这并没有影响 NoSQL，它也有自己的位置。

### 8.**蔚蓝地图**

[@jimbobbennett](https://twitter.com/jimbobbennett) [说](https://twitter.com/jimbobbennett/status/1430034639624630277)“我很少看到太多 [@AzureMaps](https://twitter.com/AzureMaps) 的内容，这很遗憾，因为里面有一些很棒的东西。”

**我的观点**:我认为我们太习惯于看到和使用谷歌地图，以至于很少使用 Azure 地图。然而，它有很好的功能与 Azure 的其他服务相结合，如 Azure Active Direction 和 Power Apps——更不用说 Azure Maps Creator 为您的项目定制地图了。

### 9. **Azure 桌面储物**

@flytzen 为 [Azure 桌子储物](https://acloudguru.com/course/azure-storage-deep-dive)做了一个强有力的案例，他说:“Azure 桌子储物在一个国家里。可扩展性极强，速度惊人，超级可靠，而且如此便宜，还不如免费。难怪微软试图假装它不存在，所以你用 100 倍价格的宇宙版本代替(是的，真的)。。。我构建了一个系统，在表存储中有 2000 多万辆汽车的大约 1.3 亿英里记录。成本是一两杯咖啡，检索时间大约是 4 毫秒。”

@ Jordan sonfire 附议。“就这么多这个。我们在一个表中有 210 亿个分区键，但性能仍然和第一天一样。”

**我的服**:是的，全部！

### 10. **Azure 搜索**

[@kjeld264](https://twitter.com/kjeld264) 和 [@merill](https://twitter.com/merill) 都提名了 Azure Search，或者 Azure Coginitive Search，因为它的正式名称是。这是一项“内置人工智能功能的云搜索服务，可以丰富各种类型的信息，帮助你大规模地识别和探索相关内容。”它基本上是将机器学习的魔力注入数据集，以找到相关的和有上下文联系的东西。非常酷。

### 11. **AAD 应用代理**

[@cgill](https://twitter.com/cgill) 觉得是 AAD App 代理“轻而易举”， [@mabster](https://twitter.com/mabster) 同意，[说](https://twitter.com/mabster/status/1430033526393430017)“App 代理对我们来说是天赐之物！我们有一堆 Windows-auth 本地遗留应用，我们能够通过 AADAP 非常轻松地使用 Azure AD auth(包括 MFA)将它们呈现到网络上。”我要告诉你一个秘密。我没用过 AAD App 代理，所以不能投稿。听起来不错！

### 12. **Azure 语音识别**

[@ christosmatkas](https://twitter.com/ChristosMatskas/status/1430006596751421443)建议 Azure 语音识别，随着 [@azwildfire1](https://twitter.com/azwildfire1) [在](https://twitter.com/azwildfire1/status/1430056075189915648)打卡，“情感分析是炸弹！如果你是单身，并且也在试图理解短信背后的含义，这很有用。因此，我开始对我的垃圾邮件进行情感分析。🤷‍♂️

### 13.**日志分析**

[@devlead 说](https://twitter.com/devlead)“[日志分析](https://acloudguru.com/hands-on-labs/implementing-azure-monitor)，很少有人知道你可以摄取自定义数据，这让你可以通过 KQL 查询以新的方式快速查看它。”

* * *

我们做到了！不同意上面的列表？让我知道我错过了什么，或者用大写字母键入我，告诉我我在 [Twitter](https://twitter.com/larsklint) 或 [ACG 不和谐社区](https://discord.com/invite/acloudguru)中犯了多大的错误。

你也可以通过在 YouTube 上订阅一位云专家的每周微软 Azure 新闻(以及来自其他云提供商的新闻)来了解 Azure 的一切。你也可以在[脸书](https://www.facebook.com/acloudguru)上喜欢我们，在[推特](https://twitter.com/acloudguru)上关注我们，或者在[不和谐](http://discord.gg/acloudguru)上加入对话！

* * *

### 提升你的 Azure 技能

我们的易于使用、解释得很清楚的 Azure cloud 课程将帮助你磨练技能，让你从新手快速成为大师。查看 ACG 目前的[免费云课程](https://acloudguru.com/blog/news/whats-free-at-acg)或[立即开始免费试用](https://acloudguru.com/pricing)。