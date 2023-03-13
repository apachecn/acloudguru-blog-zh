# 我有多少代码？DevSecOps 故事

> 原文：<https://acloudguru.com/blog/engineering/how-much-code-do-i-have-a-devsecops-story>

by Darwin Sanoy
[博客](https://missionimpossiblecode.io) | [推特](https://twitter.com/DarwinTheorizes)|[LinkedIn](https://www.linkedin.com/in/darwinsanoy)|[git lab](https://gitlab.com/DarwinJS)

### **开发警察的时代即将来临**

作为 GitLab 解决方案架构师，我与许多客户一起考虑他们对 DevSecOps 的前瞻性计划。随着新的威胁和漏洞不断被发现，每个人都理所当然地关注代码安全性。不幸的是，计算中的坏人有一个非常敏捷的发布周期。

我看到所有类型的组织都在努力改进他们的 DevSecOps 游戏。由于 DevSecOps 完全是关于 App Sec 程序中可以自动化的部分，所以这种转变的很大一部分是评估什么工具选择是最相关和最划算的。

在许多情况下，这意味着将扫描工具的使用从早期采用者推进到所有代码都被扫描的程度。

我鼓励客户制定一个 DevSecOps 成熟度和 TCO 计划，该计划预测他们对成熟 DevSecOps 的总成本。出于多种原因，同时规划成熟度和总体拥有成本至关重要。令人惊讶的是，许多组织还没有计划好“成熟的 DevSecOps”对他们来说意味着什么——他们已经抓了一些工具，并开始进行一些扫描。对 DevSecOps 的无计划的有机方法的总拥有成本可能导致非常不均衡和不断上升的成本，以及在知道整个操作何时对公司和手边的代码库来说是“成熟的”时缺乏远见。

### **预测成熟开发团队的安全扫描成本**

作为评估的一部分，许可的安全扫描工具有各种各样的许可模式。许多流行的扫描工具按扫描的代码量收费。

以下是一些流行的基于音量的模型:

*   扫描的代码行
*   扫描的兆字节代码
*   扫描的应用程序数量

有些可能根据对相同代码的每次扫描的累计来收费，有些可能根据“受管理的唯一代码行/MB”来收费，因此重复扫描相同代码不会产生成本。

组织可能需要预测这一成本的几个关键转折点:

*   评估使用基于卷的工具提升开发成本的真实成本
*   考虑到代码库的增长，尝试为 DevSecOps 做预算
*   当比较各种扫描工具选择的总拥有成本时
*   在评估整合安全工具的真实成本或节约时
*   当考虑扫描处于“仅安全修复”状态的代码的频率时
*   当大型代码库被继承时——比如在公司收购期间

请注意，上面的列表意味着对代码进行计数可能是一项持续的需求。

在所有这些情况下，一个核心挑战是获得扫描工具用来确定欠什么的代码库指标，而不必在所有存储库上配置他们的工具。

如果您参与了一个比较扫描工具的项目，那么拥有统计数据和在不产生设置每个正在考虑的工具的成本的情况下获得统计数据更为重要。

### 数数能有多难？

我们中的绝大多数人在记事之前就被教会了数数。那么，用一个快速脚本将几行或几兆字节的源代码加起来会有多难呢？

如果您的存储库中只有源代码(没有二进制文件和非代码文件),并且如果您只打算扫描代码的默认分支，这可能相当简单。

但是，如果您需要消除二进制文件或任何其他文件类型(例如，markdown)，这可能会变得很有挑战性。此外，如果您不打算扫描 monorepo 中的所有内容，这可能很难管理。

作为第一步，我们将使用 Git 命令来消除二进制文件和其他非代码文件。您可以使用扩展名排除列表来指明不是代码文件的文件。

之后，我们将看看如何使用专门计算代码行的实用程序，包括消除空白和注释。

无论您使用什么来计算代码，Git 命令优化不仅将签出文件的范围扩大到代码文件，而且使扫描大型存储库和大量存储库的速度更快、成本更低。

### **通过排除优化计数“带蓝色的东西”**

想象你正从城市公寓搬到一个新家。你的家庭用品被装在一个集装箱里，随时可以运走。就在这时，你收到新居所在地政府的通知，通知你新居民必须为他们的一些物品缴税。这个地方有点奇怪，他们只是想让你在任何有蓝色的物品上每磅支付 5 便士。(不，美国新泽西州没有这个要求，但这是一个合理的猜测。)

对于称重过程，你需要将箱子搬回你的公寓，打开它们，找到蓝色的物品，称重，并跟踪总重量。

幸运的是，你已经能够从工作中借用一套高速机器人，你可以给他们关于选择和处理物品的具体指示。不幸的是，他们没有配备秤，所以你必须做称重和计数。

有两种方法可以让机器人优化你的任务:

1.  让他们把箱子带到公寓，只打开含有蓝色的东西，以便称重。
2.  让他们在卡车上找到盒子里的蓝色东西，只把这些东西带到公寓。

事实证明，我们有这两个选项和一些更新的 Git 功能。

![](img/7bb0af10129e2f1b455fed6288ef43c8.png)

### **两次我们取一个尺寸，时间命中**

我们将要讨论的优化可以节省磁盘空间和时间。如果您计划在许多存储库上运行它，那么这两者都会显著地影响这个过程。磁盘空间可能会溢出，或者需要对一次可以处理多少个存储库进行繁琐的管理，以避免溢出。如果你在一个付费的 CI 系统上运行，那么运行时间长度就等于实际花费。

在使用 Git 存储库时，有两种可能的情况，您可能会因为二进制内容或其他不需要的文件而受到大小和时间的影响:

1.  当从远程接收 git 历史数据(Git 克隆或获取)时，默认情况下，传输所有存储库历史的所有分支的所有文件。
2.  当将 Git 文件解包(git checkout)到工作目录中时，提取目标分支的所有文件。

下面的一些 Git 优化命令关注的是根本不要从服务器复制数据，而其他一些命令关注的是不要提取假定存在于传输数据中的数据。

在下面的例子中，我们将假设这个克隆明确地用于计数的目的，并将在之后被丢弃。为了使它也能用于构建活动，需要额外的 Git 命令来将克隆重新配置为更可用的状态。

### **让 Git 做繁重的工作**

Git 将在克隆期间选择要转移的历史，并选择要检出的内容。结果应该只是我们默认分支上的当前代码。这使得总大小估计或按文件扩展名的大小估计变得更加容易，因为我们只有想要计数的文件。

### **优化测试**

对于我们的示例代码，我们将使用存储库 www-gitlab-com，因为它包含许多 web 图形文件形式的二进制文件和重要的 Git 历史，并且它是公开可用的。选择较大的文件可以更容易地根据文件大小判断命令是否正确执行。

以下是判断命令是否正确执行的方法:

| 常规尺寸 | 优化尺寸 | www-gitlab-com .git folder |
| --- | --- | --- |
| 4.2 GB | 111 MB | git 克隆时间(无检验) |
| 21 分钟 | 46 秒 | www-gitlab-com 文件(除。git 文件夹) |
| 2.7 GB  | 260 MB | git checkout time |
| 27 秒 | 19 秒 | 检出的对象 |
| 15546 | 4467 | 计算代码行数 |
| 207925 | 206658* | **部分克隆到部分拯救** |

**Note: sparse-checkout reduces the ruby file count and therefore the lines count. I was not able to discover why before the publishing due date.*

### 每次从远程 Git 服务请求 Git 克隆时，Git 服务都会准备一个包文件发送给客户机。部分克隆是许多公司和个人开发的一项新功能，它通过传递排除特定对象的指令来利用这一准备步骤。

如果后续的本地 Git 命令需要，最初被部分克隆排除的对象将被自动从远程设备中取出。因此，如果您进行部分克隆以防止二进制文件出现，但随后签出包含二进制文件的分支，则该二进制文件将在签出过程中被删除。排除过滤器规范不会在所有后续的本地 Git 命令上强制实施。这是一种自动行为，旨在防止部分克隆中断当前工作流。

下面的部分克隆从中筛选出所有文件。git 历史记录:

要使部分克隆工作，您必须安装 Git 2.22 或更高版本。

```
```bash
git clone --filter=blob:none --no-checkout https://gitlab.com/gitlab-com/www-gitlab-com.git
```
```

**浅层克隆优化更多**

### 对于代码计数，我们不需要完整的 git 历史记录，因此我们可以在克隆或获取时使用–depth 1 来减少。git 文件夹甚至更多，用于我们将要下载的文本文件。为此，我们将在 Git 命令中添加“深度 1 ”,如下所示:

**稀稀拉拉的结帐去营救剩下的人**

```
```bash
git clone --depth 1 --filter=blob:none --no-checkout https://gitlab.com/gitlab-com/www-gitlab-com.git
```
```

### Git 的稀疏签出特性是我们如何防止我们从历史中移除的不需要的文件在签出期间被动态地从原点拉出来。

稀疏签出允许使用与相同配置的文件。gitignore，它会在执行 checkout 命令时过滤哪些内容将被检出，哪些内容不会被检出。

我们需要启用稀疏检出，然后用非代码文件的文件规范配置稀疏检出文件。您可能想要完善一个非代码/二进制文件的主列表，您可以在所有存储库中重用该列表作为稀疏签出文件。还有一个聪明的方法来存储这个文件。git 并将其用于部分克隆和稀疏检验。对于该方法，请通读以下文档并扫描文件名。gitfilterspec": [GitLab 部分克隆](https://docs.gitlab.com/ee/topics/git/partial_clone.html#filter-by-file-path)。

这段代码将我们设置好，然后检查 master。

为了让稀疏校验正常工作，您必须至少拥有 Git 2.25。

```
```bash
git sparse-checkout init
echo -e '*.* \n!**/*.idx \n!**/*.mp4 \n!**/*.gif \n!**/*.pdf \n!**/*.png \n!**/*.jpg \n!**/*.jpeg \n!**/*.eps \n!**/*.md \n' > .git/info/sparse-checkout
git checkout master
```
```

**计算代码行数**

### 由于多种原因，计算代码行数具有挑战性，最值得注意的是代码中的注释不算一行。此外，有必要知道您使用什么语言，因为您的安全工具需要覆盖所有语言。

出于文档的目的，这里有一些通用的 shell 代码，用于计算所有文件的行数。但是，如果您将它与下面的计数实用程序的输出进行比较，您会发现这种方法有很大的误差，并且很可能需要专门针对文件类型。

即使对于我们最基本的代码计数版本，使用专门的代码计数实用程序也是有意义的。

```
```bash
 find . -type f -exec wc -l {} \; | awk '{ SUM += $0} END { print SUM }'
```
```

我对可用于这项任务的开源工具做了一个调查，最终选择了本·博伊特(Ben Boyte)r 的“[sloc cloc code](https://github.com/boyter/scc/)”——简称 scc。它在现代编码语言(Go)中得到积极维护。如果您有自定义需求，它还允许您扩展语言支持。下面是处理测试存储库后的输出示例:

语言

| 文件 | 线 | 空白 | 评论 | 密码 | 复杂性 | Ruby HTML |
| --- | --- | --- | --- | --- | --- | --- |
| 1179 | 119432 | 33420 | 948 | 85064 | 14177 | 挽救（saving 的简写） |
| 1077 | 18822 | 621 | 194 | 18007 | 3 | 低增生性急性髓细胞性白血病 |
| 782 | 39804 | 3648 | 204 | 35952 | 0 | 亚姆 |
| 723 | 116946 | 8626 | 2066 | 106254 | 0 | 厚颜无耻 |
| 324 | 52671 | 9090 | 3578 | 40003 | 88 | 红宝石 |
| 136 | 11068 | 2094 | 626 | 8345 | 486 | Java Script 语言 |
| 125 | 31952 | 3917 | 3739 | 24296 | 3437 | 超文本标记语言 |
| 12 | 1231 | 101 | 123 | 1007 | 0 | 视图(view) |
| 11 | 1519 | 79 | 0 | 1440 | 89 | 纯文本 |
| 4 | 7 | 2 | 0 | 5 | 0 | 半铸钢ˌ钢性铸铁(Cast Semi-Steel) |
| 3 | 926 | 155 | 四 | 767 | 0 | 壳 |
| 3 | 86 | 20 | 七 | 59 | 9 | JSON |
| 2 | 278 | 0 | 0 | 278 | 0 | 降价 |
| 2 | 65 | 15 | 0 | 50 | 0 | 战斗支援车 |
| 一 | 58 | 0 | 0 | 58 | 0 | 乳液 |
| 一 | 176 | 9 | 8 | 159 | 0 | 计算机编程语言 |
| 一 | 363 | 9 | 3 | 351 | 19 | 可扩展标记语言 |
| 一 | 12 | 0 | 0 | 12 | 0 | 吉蒂尔 |
| 1 | 36 | 9 | 5 | 22 | 0 | **总计** |
| **4388** | **395452** | **61815** | **11505** | **322132** | **18318** | 下面是获得上述输出的代码: |

Estimated Cost to Develop $11,615,312
Estimated Schedule Effort 38.958526 months
Estimated People Required 35.316937
Processed 41026462 bytes, 41.026 megabytes (SI)

scc 有许多选项，您可以在开源项目中或者通过使用–*-help*命令行选项来检查。

```
```bash
go get -u github.com/boyter/scc/
scc .
```
```

**计数码的 MB 数**

### 由于我们已经从文件层次结构中排除了所有非代码文件，我们可以通过以下代码大致了解 MBs:

上面的方法需要一个精确的排除标准，以确保除了代码文件之外什么都没有——这不是一个简单的任务，可能需要在每个存储库的基础上花费大量的精力。

```
```bash
cd www-gitlab-com
du -sh
```
```

由于这个挑战，我向 Ben Boyter 的 OSS 项目提出了一个请求，看看 scc 是否可以更新到计算 MBs，他能够将其工作到版本 2.13.0！谢谢你，本！据我所知，你现在只有几行代码计数器可以做到这一点！

根据请求，Ben 还花时间更新了 scc，以便它可以在一次计数运行后输出多种格式——因此，如果它还不够快，现在我们不必调用它两次或更多次来获得我们想要的输出格式。如果你一次分析一大堆存储库，这将使一切保持超快的速度。

scc 通过简单地将它处理的每个代码文件的文件字节相加来计算字节数，这与消除空格和注释的行计数略有不同。如果您查看上面的控制台输出捕获，您可以看到它给出了所有文件的摘要。在数据输出格式中——JSON、HTML 和 CSV——它将给出每种语言的字节数。我们下面的代码使用 w3m 将 html 文件转储到控制台，这样我们就可以获得控制台输出中的字节。

**对编译后的二进制文件进行字节计数**

### 一些漏洞工具会扫描编译好的二进制文件。下面的 shell oneliner 根据您提供的扩展名列表来计算文件大小。在示例中，*。jpg 和*。png 用于 www-gitlab-com repo 示例。删除扩展引用和括号会导致看到所有扩展的结果。在下面完成的脚本中，awk 用于格式化 CSV 和 HTML 数据格式。Find 有一个 not 运算符"！"可以在-iname 参数前使用它来创建排除列表。

**将所有这些整合在一起**

```
```bash
find . -type f \( -iname \*.jpg -o -iname \*.png \) |  egrep -o "\.[a-zA-Z0-9]+$" | sort -u | xargs -I '%' find . -type f -name "*%" -exec du -ch {} + -exec echo % \; | egrep "^\.[a-zA-Z0-9]+$|total$" | uniq | paste - -
```
```

### 下面的代码使用 Docker，这样您就可以轻松地在本地进行测试，并将其移植到基于容器的 CI 系统。

**注意:** scc 非常快(在这项任务中比 CLOC 快 3600%)，对于各种输出格式运行多次并不像看起来那么昂贵。

**最终输出**

```
```bash
docker run -it golang:1.15rc1-alpine3.12 sh #golang on a distro with a proper package manager
apk update; apk add git w3m #need at least 2.25 of git, w3m to render html in console
go get -u github.com/boyter/scc/
git clone --depth 1 --filter=blob:none --no-checkout https://gitlab.com/gitlab-com/www-gitlab-com.git
cd www-gitlab-com
git config --local core.sparsecheckout true
echo -e '*.* \n!**/*.idx \n!**/*.mp4 \n!**/*.gif \n!**/*.pdf \n!**/*.png \n!**/*.jpg \n!**/*.jpeg \n!**/*.eps \n!**/*.md \n' > .git/info/sparse-checkout
git checkout master

#html for easy viewing as a CI artifact and json for data ingestion
time scc . --not-match .*md --format-multi "html:loc.html,json:loc.json"
w3m -dump loc.html

echo "Total Bytes of jpgs and pngs (emulating counting your binary code files) in csv:"
time find . -type f \( -iname \*.jpg -o -iname \*.png \) |  egrep -o "\.[a-zA-Z0-9]+$" | sort -u | xargs -I '%' find . -type f -name "*%" -exec du -c {} + -exec echo % \; | egrep "^\.[a-zA-Z0-9]+$|total$" | uniq | paste - - | awk 'BEGIN {print "Type,Bytes"}{print $1 "," $2*1024}' > binarysize.csv

echo "Total Bytes of jpgs and pngs (emulating counting your binary code files) in HTML:"
time find . -type f \( -iname \*.jpg -o -iname \*.png \) |  egrep -o "\.[a-zA-Z0-9]+$" | sort -u | xargs -I '%' find . -type f -name "*%" -exec du -c {} + -exec echo % \; | egrep "^\.[a-zA-Z0-9]+$|total$" | uniq | paste - - | awk 'BEGIN {print "<html lang=\"en\"><head><meta charset=\"utf-8\" /><title>binary bytes html output</title><style>table { border-collapse: collapse; }td, th { border: 1px solid #999; padding: 0.5rem; text-align: left;}</style></head><body><table id=\"binarybytes-table\" border=1><thead><tr><th>Language</th><th>Bytes</th></tr></thead><tbody>"}{print "<tr><th>" $1 "</th><th>" $2*1024 "</th></tr>"}END { print "</table></body></html>" }' > binarysize.html
w3m -dump binarysize.html
```
```

### 下面是上面输出的一个例子，包括代码的字节。

语言

| 文件 | 线 | 空白 | 评论 | 密码 | 复杂性 | 字节 | 挽救（saving 的简写） |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1077 | 18822 | 621 | 194 | 18007 | 3 | 19395861 | 低增生性急性髓细胞性白血病 |
| 762 | 39700 | 3635 | 204 | 35861 | 0 | 2087355 | 亚姆 |
| 723 | 116857 | 8622 | 2057 | 106178 | 0 | 5572000 | 厚颜无耻 |
| 324 | 52666 | 9089 | 3578 | 39999 | 88 | 1057903 | Ruby HTML |
| 179 | 6643 | 593 | 0 | 6050 | 625 | 391692 | 红宝石 |
| 136 | 11095 | 2097 | 627 | 8371 | 484 | 333413 | Java Script 语言 |
| 125 | 31952 | 3917 | 3739 | 24296 | 3447 | 3423974 | 超文本标记语言 |
| 12 | 1228 | 100 | 123 | 1005 | 0 | 73922 | 某视频剪辑软件 |
| 11 | 1519 | 79 | 0 | 1440 | 89 | 45610 | 纯文本 |
| 四 | 七 | 2 | 0 | 5 | 0 | 327 | 半铸钢ˌ钢性铸铁(Cast Semi-Steel) |
| 3 | 926 | 155 | 四 | 767 | 0 | 14658 | 壳 |
| 3 | 86 | 20 | 七 | 59 | 9 | 2174 | JSON |
| 2 | 278 | 0 | 0 | 278 | 0 | 7117 | 降价 |
| 2 | 65 | 15 | 0 | 50 | 0 | 4170 | 战斗支援车 |
| 一 | 58 | 0 | 0 | 58 | 0 | 15278 | 乳液 |
| 一 | 176 | 9 | 8 | 159 | 0 | 4309 | 计算机编程语言 |
| 一 | 363 | 9 | 3 | 351 | 19 | 13394 | 可扩展标记语言 |
| 一 | 12 | 0 | 0 | 12 | 0 | 391 | 吉蒂尔 |
| 1 | 36 | 9 | 5 | 22 | 0 | 538 | **总计** |
| **3368** | **282489** | **28972** | **10549** | **242968** | **4764** | **32444086** | **交叉校验结果** |

### 由于 scc 对较老但古老的 CLOC 有类似的语言支持，您可以像这样交叉检查较老的实用程序(假设您在上面的 Golang 容器上):

注意:虽然 CLOC 在计算代码方面做了一些改进，但在我对 www-gitlab-com 的测试中，花费的时间是它的 24 到 36 倍，结果也非常相似。

```
```bash
apk add cloc
time cloc .
```
```

**MissionImpossibleCode.io 现场编码改进此代码**

### 在[碟中谍现场编码](https://missionimpossiblecode.io/post/mission-impossible-live-coding/)的前一集中，我和我的同事 Jefferson Jones 能够让 scc 作为一个可重用的 GitLab CI CD 插件运行。在未来的一期中，我们将会让这变得更加灵活——通过允许一个存储库列表(而不是一次做一个)和一些代码在 GitLab 组层次结构中遍历所有项目。你可以在这里了解更多关于碟中谍现场编码事件[。](https://missionimpossiblecode.io/post/mission-impossible-live-coding/)

**最后一个“蓝色的东西”优化**

### 让我们回到你的公寓——那个有蓝色分类机器人的公寓。当你正在考虑如何完成计数任务时，其中一个机器人突然灵机一动(它可能有一些吸尘器的 DNA)，并暗示公寓垃圾桶比你的公寓更靠近包装容器。因此，简单地扔掉所有“蓝色的东西”将会节省大量的时间、精力和税款。移情和怀旧算法，有人知道吗？

**用 GitLab 做数字**

### 了解工具和流程的总成本是当前状态和未来发展的关键。GitLab 有一些工具可以帮助这个部门。 [GitLab Secure](https://about.gitlab.com/stages-devops-lifecycle/secure/) 与第三方扫描器集成，可以直接向开发人员报告漏洞，这些开发人员在他们的下一个功能分支构建时会立即引入这些漏洞(将**向左硬移**)。如果 GitLab 附带的免费扫描仪足以满足您的扫描需求，那么它们没有任何基于使用的定价。因此，当一些工具整合成为可能时，您可能会节省一些钱。点击此处，了解更多关于 GitLab Secure [的详情。](https://about.gitlab.com/stages-devops-lifecycle/secure/)

Understanding the total cost of tooling and processes is key for the current state and future growth. GitLab has some tools that can help in this department. [GitLab Secure](https://about.gitlab.com/stages-devops-lifecycle/secure/) integrates with third-party scanners and can report vulnerabilities directly to the developers who introduced them immediately upon their next feature branch build (shifting **hard left**). If the free scanners that come with GitLab are sufficient for your scanning needs, they don’t have any usage-based pricing. So when some tool consolidation is possible, you can potentially save some money. Find more details on GitLab Secure [here](https://about.gitlab.com/stages-devops-lifecycle/secure/).