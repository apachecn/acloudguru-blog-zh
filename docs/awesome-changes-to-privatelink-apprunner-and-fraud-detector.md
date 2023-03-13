# 对 PrivateLink、AppRunner 和欺诈检测器的更改|云专家

> 原文：<https://acloudguru.com/blog/engineering/awesome-changes-to-privatelink-apprunner-and-fraud-detector>

本周 AWS 怎么了？PrivateLink party 的规模有所扩大，AppRunner 获得了一个非常受欢迎的新功能，欺诈检测器开始意识到它的周围环境。另外，我会让你知道一个你会喜欢的全新系列。让我们开始吧！

* * *

**通往更好职业的钥匙**

[立即开始 ACG](https://acloudguru.com/pricing) 通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室来改变你的职业生涯。

* * *

## PrivateLink 扩大支持

对 PrivateLink 的支持还在继续扩大……最近 AWS 宣布名单上又增加了一些服务，特别是事件管理器、[亚马逊 elastic cache](https://aws.amazon.com/about-aws/whats-new/2022/02/amazon-elasticache-aws-privatelink/)、[亚马逊 MemoryDB for Redis](https://aws.amazon.com/about-aws/whats-new/2022/02/amazon-memorydb-redis-aws-privatelink/) 和[亚马逊预测](https://aws.amazon.com/about-aws/whats-new/2022/02/aws-privatelink-support-amazon-forecast/)。

PrivateLink 是 AWS 对将某些 AWS 服务直接连接到您的 VPC 的能力的统称，避免了往返于这些服务的公共端点。大多数服务使用接口端点，而 S3 和 DynamoDB 使用网关端点。效果是一样的… PrivateLink 使您对这些服务的呼叫不通过公共互联网，而是使用 AWS 网络主干。这增加了隐私，并且在端点策略的帮助下，可以极大地提高安全性。

## AppRunner 获得 VPC 访问权限

AppRunner 是 AWS 的交钥匙集装箱服务，有点像 Fargate 的小兄弟。

AppRunner 的目标是提供一种快速、简单的方法，使用容器范式部署和扩展 web 应用程序——但是所有其他复杂的部分都在幕后处理。虽然有意设计得很简单，但奇怪的是却没有访问 VPC 中的资源的能力。

现在，随着您宣布现在可以将 AppRunner 工作负载连接到现有的 VPC，这个限制就不复存在了。因此，您的 AppRunner 托管的应用程序和 API 现在可以返回到您的 VPC 子网，以访问这些 RDS 实例、Redis 缓存或您在其中运行的任何东西，前提是您将安全组配置为允许这样做。

另外，通过这个 VPC 连接，您还可以使用我们之前讨论过的 PrivateLink 从您的 AppRunner 应用程序私下连接到其他 AWS 服务。

## 欺诈检测器获取地理位置

上周，AWS 宣布[亚马逊欺诈检测器](https://aws.amazon.com/about-aws/whats-new/2022/02/aws-geolocation-enrichment-amazon-fraud-detector-models)现在将地理定位作为服务的一部分。

亚马逊欺诈检测器是一种托管的机器学习服务，你可以训练它来识别看起来不寻常的情况，因此可能表明一些邪恶的事情正在发生。借助这种新的地理位置丰富功能，欺诈检测器可以自动计算客户端的 IP 地址和物理位置(如送货地址和账单地址)之间的距离，并将其作为输入提供给欺诈检测模型。

现在，使用地理定位的欺诈检测服务已经存在了一段时间，但欺诈检测器最酷的部分是它从你的实际交易数据中学习，并不断学习。因此，如果地理上分散的交易是你的在线业务的正常部分，随着模型的学习和改进，它们可能不会被标记为不寻常。

## 但是等等，还有呢！

就在你认为事情不可能变得更好的时候，你会喜欢我们的新系列， [Cloud Builder Live](https://www.youtube.com/watch?v=dDnSTs2J6fk) ，由我的朋友和同事 David Tucker 主演。在这个真人版系列中，您可以跟随 David 使用 AWS、Microsoft Azure 和 Google 云平台实时构建一个工作应用程序。它现在正在 YouTube 和 Twitch 上播放。

我的朋友们，这就是本周所有适合发表的 AWS 新闻。保持安全，互相照顾，并保持令人敬畏，云大师！