# 使用 Lambda、Python 和 Boto3 安排 Amazon DynamoDB 备份

> 原文：<https://acloudguru.com/blog/engineering/scheduling-amazon-dynamodb-backups-with-lambda-python-and-boto3>

假设您想每天备份一个 DynamoDB 表。我们还希望将备份保留一段指定的时间。实现这一点的一个简单方法是使用 Amazon CloudWatch 事件规则每天触发一个 AWS Lambda 函数。在这个 AWS 动手实验中，您将使用 Boto3 库用 Python 编写一个 Lambda 函数。设置它需要配置一个 IAM 角色，设置一个 CloudWatch 规则，并创建一个 Lambda 函数。

## 创建 DynamoDB 表

在本练习中，您当然可以使用您帐户中的任何 DynamoDB 表，但是如果您想使用 AWS CLI 创建一个表，您可以使用以下命令:

```
aws dynamodb create-table --table-name Person  --attribute-definitions AttributeName=id,AttributeType=N  --key-schema AttributeName=id,KeyType=HASH  --billing-mode=PAY_PER_REQUEST
```

这将创建一个名为 **Person** 的 DynamoDB 表，主键为 **id** 。

## 创建 IAM 执行角色

所有 Lambda 函数都需要一个 IAM 角色来定义授予它的权限。这被称为 Lambda 函数的**执行角色。**首先，我们将浏览为 Lambda 函数创作 IAM 角色和创建 Lambda 函数本身的过程。我们将使用 AWS 管理控制台来完成这项任务:

1.  导航至 **IAM** 。
2.  导航到**策略**。
3.  点击**创建策略。**
4.  选择 **JSON** 选项卡。
5.  用以下 JSON 语句替换默认内容:

```
{   "Version":"2012-10-17",   "Statement":[      {         "Effect":"Allow",         "Action":[            "logs:CreateLogGroup",            "logs:CreateLogStream",            "logs:PutLogEvents"         ],         "Resource":"arn:aws:logs:*:*:*"      },      {         "Action":[            "dynamodb:CreateBackup",            "dynamodb:DeleteBackup",            "dynamodb:ListBackups"         ],         "Effect":"Allow",         "Resource":"*"      }   ]}
```

该语句授予两组权限。首先，它授予了记录到 CloudWatch 日志的能力。有了这个权限，任何 Python `print()`语句都会显示在 CloudWatch 日志中。其次，我们授予 Lambda 函数在所有表上创建、列出和删除 DynamoDB 备份的权限。

1.  点击**审核政策。**
2.  将这个策略命名为**LambdaBackupDynamoDBPolicy**。
3.  点击**创建策略。**

既然已经创建了策略，您必须创建一个附加了该策略的角色。

1.  在 IAM 中，导航到**角色**。
2.  点击**创建角色**。
3.  选择可信实体的类型: **AWS 服务**。
4.  选择将使用此角色的服务: **Lambda** 。
5.  点击**下一步:权限**。
6.  在搜索框中，找到上一步中创建的**LambdaBackupDynamoDBPolicy**。
7.  选中策略名称旁边的复选框。
8.  点击**下一步:标签**。
9.  点击**下一步:复习**。
10.  角色名称: **LambdaBackupDynamoDBRole** 。
11.  点击**创建角色**。

## 创建 Lambda 函数

让我们创建我们的 Lambda 函数！

1.  导航至**λ**。
2.  点击**创建功能**。
3.  从头开始选择**作者。**
4.  函数名: **BackupDynamoDB** 。
5.  运行时: **Python 3.7** 。
6.  在*权限*下，选择**选择或创建一个执行角色**。
7.  在*执行角色*下，选择**使用现有角色**。
8.  在*现有角色*下，选择上一步创建的 **LambdaBackupDynamoDBRole** 。
9.  点击**创建功能**。

将下面的源代码粘贴到 Lambda 函数的代码编辑器中:点击屏幕右上角的**保存**。

## 创建云观察器规则

接下来，我们将创建一个 CloudWatch 规则来安排 Lambda 函数定期运行。这将执行 DynamoDB 表的备份，并删除过时的备份。

1.  导航到**云观察**。
2.  导航到**事件** > **规则**。
3.  点击**创建规则**。
4.  安排事件以所需的时间间隔运行(例如，每 1 天一次)。
5.  点击**添加目标**。
6.  在*λ函数*下，选择 **BackupDynamoDB** 。
7.  在*配置下输入* **，**选择**常量(JSON 文本)**。
8.  将值设置为 JSON 语句:

    ```
    {"TableName": "Person"}
    ```

9.  点击**配置详细信息**。
10.  名称: **BackupDynamoDBDaily** (或者你喜欢的任何名字)。
11.  点击**创建规则**。
12.  等待 CloudWatch 规则触发您计划的下一个备份作业。如果你和我一样没有耐心，你可以把调度间隔设置为 **1 分钟**，你会看到它运行得更快。
13.  使用 CloudWatch 日志验证计划的备份作业是否已运行。日志组将被命名为`/aws/lambda/BackupDynamoDB`，每次调用都有一个流。
14.  验证备份文件是否存在于 DynamoDB 备份列表中。

## 想了解更多？

我希望你会发现这种技术对你自己的工作有用。如果你想学习更多有用的 AWS 自动化技术，可以看看我的新课程 [**用 Lambda、Python 和 Boto3 实现 AWS 自动化。**](https://linuxacademy.com/amazon-web-services/training/course/name/automating-aws-with-lambda-python-and-boto-3/)