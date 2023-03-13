# 多账号，多云，黑客要你的钥匙！|云专家

> 原文：<https://acloudguru.com/blog/engineering/multi-account-multicloud-protect-your-keys>

本周，我们又得到了一条直接来自烤箱的滚烫 AWS 新闻。Transit Gateway Network Manager 变成了多帐户，AWS DataSync 变成了多云——某种程度上，这是一个及时的提醒，黑客迫切需要您的 AWS 访问密钥。让我们进入本周的 AWS 新闻。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

AWS 数据同步变为多云

嗯，AWS 甚至承认 Azure 或 GCP 这样的公司并不常见，但这就是本周发生的事情。 [AWS DataSync 现在可以将谷歌云存储和 Azure 文件存储视为潜在的端点](https://aws.amazon.com/about-aws/whats-new/2022/05/aws-data-sync-two-new-storage-locations/) —允许您使用托管服务在更多位置之间转移数据。

Well, it’s not often that AWS even acknowledges the likes of Azure or GCP, but that’s just what happened this week. [AWS DataSync can now count Google Cloud Storage and Azure Files storage as potential endpoints](https://aws.amazon.com/about-aws/whats-new/2022/05/aws-data-sync-two-new-storage-locations/) — allowing you to use the managed service to shuffle data between even more locations.

现在，在你对 AWS 最终转向多云生活方式感到兴奋之前，你应该知道这种支持并不完全是原生的。AWS DataSync 使用 GCP 的 S3 兼容 API 访问谷歌云存储，并使用现有的 SMB 协议访问 Azure 文件。

截至记者发稿时，这一切可能如何运作的细节还不是很清楚，所以我不能保证它会有多好或有多不可靠。但套用劳埃德·克里斯莫斯的话来说，AWS 似乎是在告诉我们有(多)不确定的机会。

中转网关网络管理器支持多帐户

对于那些在 AWS 上管理大型多账户网络的人来说，这是一个好消息。[AWS Transit Gateway Network Manager 现在支持使用 AWS 组织创建的组织内的多个帐户](https://aws.amazon.com/about-aws/whats-new/2022/05/multi-account-support-aws-transit-gateway-network-manager/)。这使我们现在能够拥有一个涵盖所有客户的整合网络管理器控制面板，而不必从一个客户跳到另一个客户。

## 这种统一还包括 CloudWatch 指标和事件，以监视您的全球网络帝国的任何有趣的业务。是的，您现在可以在一张全球地理地图上看到所有客户的所有网络，这张地图无疑会被投影到网络运营中心的 7 英尺屏幕上，目的无非是让人们在参观数据中心时留下深刻印象。

[**观看:保护您的 AWS 环境**](https://acloudguru.com/content/securing-aws-environment-webinar) 在[这个免费的点播网络研讨会](https://acloudguru.com/content/securing-aws-environment-webinar)中，云安全专家唐·麦咭详细介绍了如何让复杂的 AWS 环境从零到安全。

“回购劫持”窃取 AWS 密钥

* * *

[![AWS Cloud Compliance Governance Security](img/6248396917d6ad72577def2a4bf7b70e.png)](https://acloudguru.com/content/securing-aws-environment-webinar)

在本周的“我们难道没有足够的东西需要担心”一栏中，一个流行的 Python 包 ctx 和一个名为 Phpass 的 PHP 包被黑客攻击显然是为了窃取环境变量，包括 AWS 密钥，并将其泄露到攻击者控制下的 Heroku URL。

* * *

## 攻击者使用了一种称为回购劫持的方法，通过这种方法，有人可以获得对合法回购的未经授权的访问，并可以将恶意代码插入新版本。安全研究人员只花了几个小时就注意到了异常，但估计已经有两万个版本的被黑代码被下载了。这种攻击手段特别狡猾，因为每当新版本发布时，许多人都会盲目地升级一个库或包。

我们如何防御这样的事情？

一种方法是将你的库锁定在特定的版本中，这样你就可以控制它们更新的时间和方式。在可能的情况下，使用 IAM 角色而不是访问密钥，并将出站流量锁定到仅受信任的目的地，这可能会减轻这种特定的攻击。但是，至少，如果您还没有启用 CloudTrail 日志记录，现在就启用吧！不，我是认真的。停止阅读这篇文章，现在就去启用它——然后回来，当然。

你是想开始你的 AWS 职业生涯还是想让你的技能更上一层楼？我们的 AWS 学习路径提供定制的路径，让您的云计算之旅更加精彩！

最后，给那些乘坐 EC2 列车的人一点小提示，[您现在可以向您的实例](https://aws.amazon.com/about-aws/whats-new/2022/05/amazon-ec2-enables-protect-instances-unintentional-stop-actions/)添加停止保护，以防止它们从控制台、CLI 或 API 意外停止。这可能是一个方便的小特性，可以防止在云信息删除或自动成本控制措施的情况下 EC2 实例被停止或终止。我的朋友们，这就是本周 AWS 所有适合印刷的新闻。

* * *

关注所有最新的 AWS 新闻！在[脸书上喜欢我们，](https://www.facebook.com/acloudguru)在[推特](https://twitter.com/acloudguru)上关注我们，并在[不和](https://discord.com/invite/pluralsight)上加入对话。

* * *

As we wrap up, just a little tidbit for those riding the EC2 train, [you can now add Stop Protection to your instances](https://aws.amazon.com/about-aws/whats-new/2022/05/amazon-ec2-enables-protect-instances-unintentional-stop-actions/) to prevent them from unintentional stop actions from the console, CLI, or API. Might be a handy little feature to keep an EC2 instance from being stopped or terminated on you in the case of a CloudFormation delete or automated cost control measures. That, my friends, is all the AWS news fit to print this week.

Stay up to date with all the latest AWS news! Like us on [Facebook,](https://www.facebook.com/acloudguru) follow us on [Twitter](https://twitter.com/acloudguru), and join in the conversation on [Discord](https://discord.com/invite/pluralsight).