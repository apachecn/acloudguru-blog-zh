# AWS Secrets Manager vs 参数存储

> 原文：<https://acloudguru.com/blog/engineering/an-inside-look-at-aws-secrets-manager-vs-parameter-store>

在本文中，我们将探讨 AWS Secrets Manager 和 AWS Systems Manager 参数存储之间的相似之处和不同之处。让我们开始吧！

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

什么是 AWS Secrets Manager？

## 亚马逊网络服务在 2018 年推出了 [AWS Secrets Manager](https://aws.amazon.com/secrets-manager/) 。这是一项帮助您保护对应用程序、服务和 It 资源的访问的服务。该服务使您能够在数据库凭证、API 密钥和其他机密的整个生命周期中轻松地轮换、管理和检索它们。使用 Secrets Manager，您可以保护、审核和管理用于访问 AWS 云中、第三方服务上和内部资源的机密。

**AWS Secrets Manager 有哪些功能？**

## 好吧，让我们回到过去，就在政治家发明互联网之后；-).也许我们在用老派的 ASP 或其他语言开发 web 应用程序。如果我们有一个想要连接的数据库呢？没问题，让我们打开 Netscape，搜索数据库的连接字符串。啊，在那儿，真酷。我们可以将这个连接字符串直接插入我们的 ASP 代码，内联硬编码我们的数据库凭证，访问我们的数据库，执行查询，返回一个记录集并开始处理它！但是当然总有坏人潜伏在周围等着好人做傻事。愚蠢的是将数据库凭证硬编码在代码中。

黑客大概在黑客训练营的第一周就学会了如何抓取这些信息。所以好人从他们的错误中吸取教训，在因为严重的安全漏洞而被解雇后得到一份新工作，并学会从他们的代码中删除数据库凭证。他们创建配置文件，并从代码中引用配置文件中的秘密。这无疑是比硬编码凭证更好的解决方案。AWS 出现了，其他选项也变得可用。

在 AWS 中，开发者可以将他们的秘密存储在 S3，甚至可以加密静态和传输中的数据。众所周知，AWS 中的事物发展变化很快。首先是 [AWS 系统管理器参数存储](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter-store.html)。参数存储是一个安全的托管键/值存储，非常适合存储参数、机密和配置信息。然后在 2018 年 4 月，AWS 宣布了提供类似功能的 Secrets Manager。那么它们有什么不同，又有什么相似之处呢？

**AWS 秘密管理器** **vs AWS 系统参数库:相似之处**

## 先说相似点。而且有很多这样的服务，这就引出了一个问题，拥有这两种服务有什么意义？这可能是最好的保留判断，因为这是一个很好的赌注，AWS 将继续发展秘密管理器。但是现在，我们来谈谈相似之处。

加密

### 首先是加密。AWS Secrets Manager 和 AWS Systems Manager 参数存储都使用 AWS KMS 来加密值。KMS 是一项托管服务，使您能够轻松加密您的数据。AWS KMS 为您提供高度可用的密钥存储、管理和审计解决方案，以便在您自己的应用程序中加密数据，并控制 AWS 服务中存储数据的加密。

借助 KMS 和 IAM，您可以使用策略来控制 IAM 用户和角色解密值的权限。因此，轻松加密您的秘密的能力对于参数存储和秘密管理器来说都是一个巨大的特性。只有我一个人，你可以控制你的秘密。加密仅仅是为你的秘密增加了一层安全保障吗？嗯，可能是这样，但是如果加密您的机密是合规性要求呢？无论是参数存储还是机密管理器，它都是开箱即用的。

那么，如果你想加密秘密，你该如何选择呢？在这种情况下，参数存储提供了更多的功能。它可以选择存储未加密的数据，或者用 KMS 密钥加密数据。使用 Secrets Manager，机密以加密方式存储，并且没有存储未加密数据的选项。这是参数存储的一个用例。

托管密钥/值存储服务

### 另一个重要的相似之处是托管密钥/价值存储服务。这两种服务都允许您在名称或键下存储值。它们还可以存储最多 4096 个字符的值，并且您的键可以有前缀。我要提到的最后一个相似之处是，这两个服务都可以与 [AWS CloudFormation](https://aws.amazon.com/cloudformation/) 交互。让我们记住，CloudFormation 是作为代码的基础设施，因此在 CloudFormation 模板中存储秘密正是我们希望通过使用参数存储或秘密管理器来摆脱的那种不好的做法。

参数存储或机密管理器中的 CloudFormation 模板中的值都是可引用的，因此您不必对您的机密进行硬编码！没有理由在 CloudFormation 模板中硬编码诸如数据库密码之类的东西。您的模板是代码，应该像处理应用程序代码一样小心处理，注意安全性。您可以将您的用户名和密码存储在一个秘密中，您的 CloudFormation 模板可以引用该秘密，因此您在模板中只有一个指向该值的指针。

****AWS 秘密管理器** **vs AWS 系统参数存储:差异****

## 好了，现在我们需要讨论秘密管理器和参数之间的区别。让我们直接跳到底线，成本。

费用

### 参数存储不收取额外费用。您可以存储的参数数量是有限制的，目前的限制是 10，000 个。AWS Secrets Manager 需要额外的费用，目前每个存储的秘密需要 0.40 美元。此外，每 10，000 次 API 调用会产生 0.05 美元的额外费用。我们这里说的是几分钱，听起来并不多，但正如您所料，这些钱加起来可以用于一个大型组织，如果您存储大量机密，应该考虑这些钱。

AWS Secrets Manager 开始胜出的地方是自动轮换机密的能力。AWS Secrets Manager 提供了与 Amazon RDS 的完整密钥轮换集成。这对你意味着什么？嗯，Secrets Manager 可以轮换密钥，并在 RDS 中为您实际应用新的密钥/密码。我们都知道应该轮换密钥，但我们真的这么做了吗？Secrets Manager 使这一过程的自动化变得非常简单。

RDS 以外的服务的密钥轮换怎么样？我们可以使用工具箱中另一个有价值的工具:AWS Lambda！您可以使用 Lambda 编写一个函数来旋转您的密钥，这直接集成在 Secrets Manager 控制台中。

生成随机秘密的能力

### 另一个巨大的不同，也是 Secrets Manager 的一个胜利，是生成随机秘密的能力。您可以在 CloudFormation 中随机生成密码，并将密码存储在 Secrets Manager 中。这不仅仅是云形成的功能。SDK 可用于在您的应用程序代码中实现这一点。最后一个区别，也是 Secrets Manager 的另一个成功之处，是秘密可以跨帐户共享。

获得更好职业所需的技能。

* * *

## 掌握现代技术技能，获得认证，提升您的职业生涯。无论您是新手还是经验丰富的专业人士，您都可以通过实践来学习，并在 ACG 的帮助下推进您的云计算职业生涯。

Master modern tech skills, get certified, and level up your career. Whether you’re starting out or a seasoned pro, you can learn by doing and advance your career in cloud with ACG.

* * *