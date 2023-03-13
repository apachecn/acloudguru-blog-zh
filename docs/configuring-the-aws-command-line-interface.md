# 配置 AWS 命令行界面(CLI) |云专家

> 原文：<https://acloudguru.com/blog/engineering/configuring-the-aws-command-line-interface>

配置 AWS 命令行界面并不复杂。在你知道之前，你就可以开始工作了！AWS CLI 根据您的需求提供了许多定制选项。举几个例子，您可以支持多个概要文件，通过向概要文件分配用户角色来限制访问，甚至使用 HTTP 代理。我们开始吧！

## AWS CLI 的简单配置

AWS CLI 在本地将用户配置和表示为名为*的实体，命名为配置文件*，或简称为*配置文件*。如果没有使用–配置文件选项指定配置文件，将使用默认配置文件，该文件方便地命名为默认。

## **默认配置文件配置**

1.  打开一个终端窗口，输入以下命令:`aws configure`在 Windows 上，您首选的终端应用程序可能是 PowerShell 或 Windows 命令提示符(CMD)。在 Linux、Mac 或 Unix 上，可以是任意数量的使用 bash、zsh 或 tsch shells 的终端应用程序。
2.  输入 AWS 访问键、默认区域名称和默认输出格式:`AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLEAWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY Defaultregion name [None]: us-west-2Default output format [None]: json`

### 什么是 Aws 访问密钥，我为什么需要它们？

AWS 访问密钥，特别是 AWS 访问密钥 ID 和 AWS 秘密访问密钥，用于在发出请求时唯一且安全地识别您的身份。这些可以在 AWS 管理控制台中找到或创建。关于创建 AWS 访问键的更多信息可以在[这里](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html)找到。

**注意:** Amazon 建议您为有限的 IAM 角色使用访问密钥，而不是 AWS root 帐户访问密钥。原因是，[根据 AWS 文档](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html)，IAM *可以让您安全地控制对 AWS 服务和 AWS 帐户资源的访问。*

### **默认的地区名称是什么？**

默认的地区名称是一个非可选的字段，通常是离你最近的地区名称。这是将用于对服务进行调用的默认区域。有关服务和可用区域的列表，请参见[区域和端点](https://docs.aws.amazon.com/general/latest/gr/rande.html)。

### **默认输出格式是什么？**

默认的输出格式是一个*可选的*字段，指定来自 Amazon Web 服务的响应格式。如果不指定格式类型，将使用 JSON。

可用的格式类型有:

## **多个配置文件**

因此，您已经为默认用户安装并配置了 AWS CLI。很简单，对吧？但是如果你想支持多个用户呢？幸运的是，AWS CLI 通过使用*命名概要文件*支持多用户。命名配置文件的配置几乎与默认配置文件完全一样。然而，有一点小小的不同。您必须将–配置文件选项与 aws 配置命令一起使用，并指定一个配置文件名称:`aws configure --profile my_profile_name`关于配置文件的更多信息可在[这里找到](https://docs.aws.amazon.com/cli/latest/userguide/cli-multiple-profiles.html)。

### **如何更新我的配置设置？**

您可以通过使用 AWS CLI 或手动更改凭证和配置文件中的值来更新您的配置设置。

1.  **使用 AWS CLI**–在您的终端中运行 aws 配置命令，并输入更新的信息。有关更多详细信息，请参考上面的配置部分。

2.**手动更改数值**–导航至。aws 目录，并更新凭证和配置文件中的键值对。

* * *

***还有什么 CLI？***

*查看我们的 [AWS CLI 和 S3 备忘单](https://acloudguru.com/blog/engineering/aws-s3-cheat-sheet)。或者，尝试我们的动手实验，在 CLI 中获得创建和定制 [Lambda 函数的真实体验。](https://acloudguru.com/hands-on-labs/using-the-aws-cli-to-create-an-aws-lambda-function)*

* * *

### 我的凭据存储在哪里？

AWS CLI 将凭证存储在名为 c redentials 的本地文件中，该文件位于名为的文件夹中。aws 在您的主目录中。

### 我的默认区域名称和输出格式存储在哪里？

AWS CLI 将默认区域名称和输出格式存储在名为的文件夹中名为 config 的本地文件中。aws 在您的主目录中。您可以通过将 AWS_CONFIG_FILE 环境变量设置为另一个路径来更改配置文件的位置。关于设置环境变量的更多信息可以在[这里](https://docs.aws.amazon.com/cli/latest/userguide/cli-environment.html)找到。

### **我可以手动添加已命名的个人资料吗？**

您可以通过将所需信息添加到凭证和配置文件来手动配置配置文件。凭证和配置文件中的字段由键-值对表示，这些键-值对的名称以括号中的概要文件名开头。默认配置文件也位于这两个文件中。

1.  导航到。您主目录中的 aws 文件夹。
2.  打开凭证文件，添加概要文件名，后跟键值对:`[my_profile_name]aws_access_key_id=AKIAI44QH8DHBEXAMPLEaws_secret_access_key=je7MtGbClwBF/2Zp9Utk/h3yCo8nvbEXAMPLEKEY`
3.  打开 config 文件，添加配置文件名，前缀为 > profile ，后跟键值对。例如`[profile my_profile_name]region=us-east-1output=text`

**注意:**对于命名配置文件，AWS 凭证文件使用与 CLI 配置文件不同的命名格式。在 AWS 凭证文件中配置命名概要文件时，*不要*包含“概要文件”前缀。更多信息参见 [AWS 文档](https://docs.aws.amazon.com/cli/latest/userguide/cli-multiple-profiles.html)。

### 我可以为多个命令指定一个默认配置文件吗？

当然啦！您可以通过设置 AWS_DEFAULT_PROFILE 环境变量来实现。关于设置环境变量的更多信息可以在[这里](https://docs.aws.amazon.com/cli/latest/userguide/cli-environment.html)找到。

**注意:**设置环境变量会改变缺省配置文件，直到您的 shell 会话结束，或者直到您将该变量设置为不同的值。

### 我在哪里可以找到更多信息？

有关 AWS CLI 配置的更多信息，请参见用户指南中的配置部分[此处](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html)。

## 成功！

就是这样！现在您已经配置了 CLI，您已经准备好使用它与 AWS 服务进行交互，并开始从终端管理您的基础设施。下一次，我们将解释如何进行 API 调用来启动服务器、创建安全组，以及只需几个按键就能完成的更多事情。

* * *

## 获得更好职业所需的技能。

掌握现代技术技能，获得认证，提升您的职业生涯。无论您是新手还是经验丰富的专业人士，您都可以通过实践来学习，并在 ACG 的帮助下推进您的云计算职业生涯。

* * *

更多 AWS CLI 资源