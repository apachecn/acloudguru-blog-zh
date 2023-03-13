# 如何使用 GitHub 操作来自动化 Terraform 

> 原文：<https://acloudguru.com/blog/engineering/how-to-use-github-actions-to-automate-terraform>

在这篇博文中，我们将看一个使用 GitHub Actions 来自动化 Terraform 的例子，并为您提供一个快速简单的 CI/CD 解决方案。

我相信大多数管理员都会同意， [Terraform](https://acloudguru.com/blog/engineering/the-ultimate-terraform-cheatsheet) 是在您的环境中部署和管理基础架构的非常强大和高效的工具。但是你知道你可以用 GitHub 动作让它变得更好并自动化吗？

GitHub Actions 将持续集成添加到 GitHub 库，以自动化您的软件构建、测试和部署。

当使用 CI/CD 自动化 Terraform 时，它将实施配置最佳实践，促进协作，并自动化 Terraform 工作流。在这篇博客中，我将带领你使用 Terraform 和 GitHub 操作创建一个 AWS S3 网站。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

### 先决条件

因此，在能够使用 GitHub 操作来自动化 Terraform 之前，首先需要设置和配置这三样东西:

1.  Terraform CLI 已下载并安装。
2.  您将需要一个 AWS 帐户，有一个 AWS 访问密钥和秘密密钥，以及授予用户的 **AmazonS3FullAccess** IAM 权限。您还需要创建一个 S3 存储桶来远程存储 Terraform 状态。
3.  最后，您需要建立一个具有以下结构的 GitHub 存储库:

*   一个名为 **src** 的目录，你将在其中存储你的网站代码。
*   答。 **github** 目录，然后您将在其中创建一个**工作流**目录并存储您的 github 动作配置文件。
*   一个 **terraform** 目录，您将在其中存储您的 terraform 配置文件。

想从 Terraform 中获得最大收益的所有基本命令列表吗？查看我们的 [Terraform 备忘单](https://acloudguru.com/blog/engineering/the-ultimate-terraform-cheatsheet)。

## **配置您的 AWS 提供商和远程状态**

假设您已经配置了所有的先决条件，接下来您必须做的就是配置 Terraform 来引用您的 AWS 帐户。

您需要在 GitHub repo 中的 terraform 目录下创建一个名为 **main.tf** 的文件，配置如下:

```
terraform {
  required_providers {
    aws = {
      source = "hashicorp/aws"
      Version = "~>3.27"
    }
  }

  required_version = ">=0.14.9"

}

provider "aws" {
  version = "~>3.0"
  region  = "east-us-1"
}
```

该代码块将告诉 Terraform 我们想要提供 AWS 资源，并且我们将资源创建默认为 AWS 内的 **east-us-1** 区域。(您可以将其更改为适合您的任何地区。)

接下来，您需要将远程状态添加到我们的配置中。您需要将下面的代码块添加到 main.tf 文件中，就在下面的 **required_version** 值之后，并用您的 bucket 名称和 bucket 键替换占位符值:

```
required_version = ">=0.14.9" 

   backend "s3" {
       bucket = "[Remote_State_S3_Bucket_Name]"
       key    = "[Remote_State_S3_Bucket_Key]"
       region = "east-us-1"
   }
}
```

状态是 Terraform 用来比较基础设施的当前状态和期望状态的。默认情况下，Terraform 在本地存储状态。

这对于测试和诸如此类的事情来说很好，但是对于大多数生产级别或大型基础设施来说，出于安全和协作的目的，您真的应该考虑远程存储状态。

此外，由于我们使用 GitHub 操作，状态将需要远程创建。如果没有远程状态，Terraform 会生成一个本地文件，但不会提交给 GitHub，因此我们会丢失状态数据。这可能会导致自动化的各种问题，因为 Terraform 非常依赖状态数据。

## **完成你的地形配置**

现在，您已经将远程后端添加到了您的配置中，我们现在可以添加资源块，它将定义您希望 Terraform 将哪些资源部署到您的基础架构中。您需要添加以下代码块来创建网站所需的 S3 资源:

```
resource "aws_s3_bucket" "s3Bucket" {
     bucket = "[BUCKET_NAME_HERE]"
     acl       = "public-read"

     policy  = <<EOF
{
     "id" : "MakePublic",
   "version" : "2012-10-17",
   "statement" : [
      {
         "action" : [
             "s3:GetObject"
          ],
         "effect" : "Allow",
         "resource" : "arn:aws:s3:::[BUCKET_NAME_HERE]/*",
         "principal" : "*"
      }
    ]
  }
EOF

   website {
       index_document = "index.html"
   }
}
```

## **设置 GitHub 动作**

既然我们已经解决了这个问题，现在我们可以继续设置我们的 GitHub 操作了。

现在你可能会问，“为什么我要把我们的 Terraform 配置添加到 GitHub 动作或其他 CI/CD 管道中？”以下是一些原因:

*   管道创造更多**可见性**。在团队中使用 Terraform 管理基础设施时，您可以轻松查看正在运行的内容以及运行时间。在本地运行时，只有您拥有这种可见性。
*   管道创造**可追溯性**。当在管道中运行 Terraform 时，它们通常存储日志。这允许您在方便的时候回顾旧的构建及其输出。
*   流水线创造**重复性**。当您配置管道时，它应该每次都执行相同的操作。这将使调试和故障排除更加容易。
*   最后，他们创造了简单性。管道本质上可以取代本地实例。这样你就不用设置本地的依赖关系什么的了。

在 GitHub 动作可以运行之前，您需要做的第一件事是将您的 AWS 凭证添加到存储库中。为此，您需要遵循以下步骤:

1.  导航到您的存储库并选择**设置**选项卡。
2.  一旦你看到左边有一个**秘密**部分，从列表底部数第三个，点击它。
3.  点击**新建储存库密码**按钮。
4.  添加您的 **AWS_SECRET_ACCESS_KEY** 并点击**添加秘密**按钮。
5.  重复步骤 3，添加您的 **AWS_ACCESS_KEY_ID** ，并点击**添加秘密**按钮。

接下来，在**中创建 **actions.yaml** 文件。github/workflows** 目录下有如下代码:

```
name: Deploy Infrastructure

on:
  push:
    branches:
      - master

jobs:
  tf_fmt:
    name: Deploy Site
    runs-on: ubuntu-latest
    steps:

    - name: Checkout Repo
      uses: actions/checkout@v1

    - name: Terraform Init
      uses: hashicorp/terraform-github-actions/init@v0.4.0
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        TF_ACTION_WORKING_DIR: 'terraform'
        AWS_ACCESS_KEY_ID:  ${{ secrets.AWS_ACCESS_KEY_ID }}
        AWS_SECRET_ACCESS_KEY:  ${{ secrets.AWS_SECRET_ACCESS_KEY }}

    - name: Terraform Validate
      uses: hashicorp/terraform-github-actions/validate@v0.3.7

    - name: Terraform Apply
      uses: hashicorp/terraform-github-actions/apply@v0.4.0
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        TF_ACTION_WORKING_DIR: 'terraform'
        AWS_ACCESS_KEY_ID:  ${{ secrets.AWS_ACCESS_KEY_ID }}
        AWS_SECRET_ACCESS_KEY:  ${{ secrets.AWS_SECRET_ACCESS_KEY }}

    - name: Sync S3
      uses: jakejarvis/s3-sync-action@master
      env:
        SOURCE_DIR: './src'
        AWS_REGION: 'us-east-1'
        AWS_S3_BUCKET: '[BUCKET_NAME_HERE]'
        AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
        AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
```

我们在这里声明，任何时候有推送到 **src** 目录的时候，都会启动一个动作，让 Terraform 部署对你的网站所做的更改。您需要确保使用您的 bucket 名称更新 yaml 文件。你还需要确保你已经创建了 **src** 目录，并在其中添加了一个**index.html**文件。

### 成功！

就是这样！您已经使用 Terraform 和 GitHub 操作成功创建了一个 CI/CD 管道。想想这种可能性，以及这样的过程能为您节省多少时间，尤其是当您的站点或基础设施增长时。使用 Terraform 和 GitHub 操作确实可以帮助创建一个简化的、易于管理的、可重复的流程，从而节省时间并减少麻烦。下次见，大师们！

## 了解有关使用 Terraform 管理应用程序和基础设施的更多信息

请查看我的新课程[使用 Terraform 管理应用程序和基础设施](https://acloudguru.com/course/using-terraform-to-manage-applications-and-infrastructure)，体验 Terraform 的奇妙世界！

我们将探讨管理员如何使用 Terraform 轻松地向各种提供商部署基础设施。无论是单一的简单配置，还是包含多个提供商的更复杂配置，本课程都将展示从一个位置管理基础架构是多么简单。

* * *

[**获得痛苦的云词典**](https://get.acloudguru.com/cloud-dictionary-of-pain)
说云不一定要努力。我们分析了数以百万计的回复，找出了最容易让人犯错的概念。抓住这个[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)获取一些最痛苦的云术语的简洁定义。