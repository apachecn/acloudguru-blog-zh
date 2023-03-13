# 您需要解决的 5 大常见 AWS IAM 错误|云专家

> 原文：<https://acloudguru.com/blog/engineering/fixing-5-common-aws-iam-errors>

Amazon Web Services (AWS)身份和访问管理(IAM)是一项在云中提供安全性的基础服务。它允许您管理对 AWS 服务、资源和应用程序的访问。这是 AWS 的核心服务，但没有什么是完美的。在使用它的时候，你可能会遇到错误。但是不要担心！让我们深入探讨五种常见 AWS IAM 错误的原因和解决方法。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

1.AccessDeniedException–我无法承担角色

#### IAM 角色可用于跨您拥有的不同 AWS 帐户委派对您的 AWS 资源的访问。例如，您可以与不同帐户的用户共享一个帐户中的资源。这可以通过在信任帐户和其他 AWS 信任帐户之间建立信任关系来实现。

让我们以这样一种情况为例，您希望让开发帐户中的用户能够访问生产帐户中的资源。在这种情况下，需要将开发中的更新提升到生产中。这种访问称为跨帐户访问。如果权限设置不正确，您可能会遇到下面的错误。

**错误**
`An error occurred (AccessDenied) when calling the AssumeRole operation: User: arn:aws:iam:::user is not authorized to perform: sts:AssumeRole on resource: arn:aws:iam::user:role/role`

**原因** 这个 **AccessDenied** 错误可能有两个原因:您的开发账户中的用户没有权限调用 **sts:AssumeRole** ，或者生产账户中的信任关系配置不正确。

假设您已经在生产帐户中创建了一个角色，开发帐户中的用户可以承担该角色(以检索临时安全凭据)，请考虑下面的解决方案。

**解决方案#1** 验证附加到您的开发帐户中的用户的 IAM 策略是否授予该用户对您的生产帐户中的角色的 **sts:AssumeRole** 操作的权限。您必须使用类似如下所示的策略明确授予此权限。

**解决方案#2** 也许你的开发账号中的用户已经拥有了 **sts:AssumeRole** 动作的权限，但是错误仍然发生。下一步是验证您的开发帐户(您从中调用 **AssumeRole** 的帐户)是否在您的生产帐户中设置为用户试图承担的角色的可信实体。在您的生产帐户中，一个类似于下图所示的角色应该可以做到这一点。

```
{
 "Version": "2012-10-17",
 "Statement": [{
   "Effect": "Allow",
   "Action": ["sts:AssumeRole"],
   "Resource": "arn:aws:iam::user:role/role"
 }]
}
```

成功承担角色后， **AssumeRole** API 返回一组临时安全凭证，这些凭证可用于使用角色中指定的权限访问生产帐户。

```
{
 "Version": "2012-10-17",
 "Statement": [
   {
     "Effect": "Allow",
     "Principal": {
       "AWS": "arn:aws:iam::user:user-name"
     },
     "Action": "sts:AssumeRole",
     "Condition": {}
   }
 ]
}
```

2.AccessDeniedException–我不能调用 AWS API 操作

#### 当在 AWS 帐户中提供对资源的访问时，请考虑最低特权权限的原则。最低特权权限仅授予执行给定任务所需的最低级别的访问权限。这个原则强调了这样一个事实，即用户和服务只有在被明确授予访问权限后才能访问资源。

让我们以一个用户尝试使用命令行界面调用亚马逊 S3 存储桶上的列表存储桶操作为例。用户遇到以下错误。

**错误**
`An error occurred (AccessDenied) when calling the ListBuckets operation: Access Denied`

**原因** 发生**访问被拒绝**错误是因为试图执行此操作的用户没有被明确授权访问列表桶内容。除非您明确授权，否则用户无权执行此操作。

**解决方案** 简单的解决方案是给用户附加一个内嵌策略，类似于下面的代码片段。

为了提供额外的安全级别，可以在**资源**元素中命名对象，而不是使用通配符 ***** ，它代表所有资源。如果您不熟悉**资源**元素，它指定了策略覆盖的一个或多个对象。

```
{
   "Version": "2012-10-17",
   "Statement": [
       {
           "Sid": "VisualEditor0",
           "Effect": "Allow",
           "Action": [
               "s3:ListAllMyBuckets",
               "s3:ListBucket",
               "s3:HeadBucket"
           ],
           "Resource": "*"
       }
   ]
}
```

以下示例允许使用资源、**亚马逊资源名称(ARN)** 和通配符*访问特定亚马逊 S3 存储桶中的所有商品。

让我们开始您的 AWS 之旅

```
{
   "Version": "2012-10-17",
   "Statement": [
       {
           "Sid": "VisualEditor0",
           "Effect": "Allow",
           "Action": [
               "s3:ListAllMyBuckets",
               "s3:ListBucket",
               "s3:HeadBucket"
           ],
           "Resource": "arn:aws:s3:::bucket_name/*"
       }
   ]
}
```

* * *

### 希望获得 AWS 认证或提升您的云计算职业生涯？通过与 ACG 一起做来学习受欢迎的 AWS 技能。

3.未经授权的操作-我无权执行操作

* * *

#### 尝试执行某项操作时，您可能会看到一条错误消息，指出您无权执行该操作。让我们以使用 **describe-instances** 动作列出帐户中的 EC2 实例为例。

**错误** `An error occurred (UnauthorizedOperation) when calling the DescribeInstances operation: You are not authorized to perform this operation.`

**原因** 发生**未授权操作**错误是因为试图执行操作的用户或角色没有权限描述(或列出)EC2 实例。

**解决方案** 简单的解决方案是附加一个内嵌策略，类似于下面的代码片段，为用户提供访问权限。

需要强调的是，不能用资源元素中的 ARN 来定义 **DescribeInstances** 动作。有些服务不允许您为单个资源指定动作，而是要求您在**资源**元素中使用通配符 ***** 。虽然您可以为 EC2 API 的[子集定义资源级别权限，但是**描述实例**操作目前不支持资源级别权限。在这种情况下，如果您向**资源**元素添加一个 **ARN** 号，您将继续看到**未授权操作**错误。](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonec2.html)

```
{
   "Version": "2012-10-17",
   "Statement": [
       {
           "Sid": "VisualEditor0",
           "Effect": "Allow",
           "Action": [
               "ec2:DescribeInstances"
           ],
           "Resource": "*"
       }
   ]
}
```

*想要阻止删除亚马逊 S3 桶？* *使用 [AWS 策略生成器](https://acloudguru.com/hands-on-labs/preventing-deletion-of-an-amazon-s3-bucket-using-a-resource-based-policy)工具创建策略，控制对 AWS 产品和资源的访问！*

* * *

4.一个服务无权对另一个服务执行操作

* * *

#### 在管理 AWS 资源时，您通常需要授权一个 AWS 服务访问另一个服务来完成任务。让我们来看看这样的情况，您需要从 Lambda 函数中查询 DynamoDB 表。下面的 Lambda 代码片段查询 **USERS** 表，导致如下所示的错误。

**错误** `arn:aws:sts::user:assumed-role/role/function is not authorized to perform: dynamodb:Query on resource: arn:aws:dynamodb:region:account:table/USERS`

```
table = boto3.resource('dynamodb').Table('USERS')

response = table.query(KeyConditionExpression=Key('USER_ID').eq(userid))

```

**原因** 这个错误是因为 Lambda 的执行角色没有权限查询 **USERS** DynamoDB 表。

**解决方案** 简单的解决方案是通过附加如下所示的内联策略来修改 Lambda 的执行角色:

可以遵循相同的方法来允许 Lambda 访问亚马逊 S3。如果 Lambda 函数和 S3 桶在同一个 AWS 帐户中，上述方法将起作用。但是，如果他们在不同的帐户中，您需要授予 Amazon S3 Lambda 执行角色和 bucket 策略的权限。

```
{
   "Version": "2012-10-17",
   "Statement": [
       {
           "Sid": "VisualEditor0",
           "Effect": "Allow",
           "Action": "dynamodb:Query",
           "Resource": "arn:aws:dynamodb:region:account:table/USERS"
       }
   ]
}
```

5.策略必须包含有效的版本字符串

#### 创建或修改策略时，您可能会遇到一个错误，指出策略必须包含有效的**版本**字符串。此**版本**策略元素不同于用于托管策略的[多版本支持](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-versioning.html)。**版本**策略元素指定了应该用于处理策略的语言语法规则。对于那些 IAM 新手来说，这可能是一个困惑点，因为他们经常试图将当前日期用于**版本**策略元素；然而，**版本**仅限于几个选择值。例如，将当前日期用于**版本**字符串，类似于下面所示，将导致错误。

**错误** `This policy contains the following error: The policy must contain a valid version string`

```
{
   "Version": "2020-07-30",
   "Statement": [
       {
           "Sid": "VisualEditor0",
           "Effect": "Allow",
           "Action": [
               "ec2:DescribeInstances"
           ],
           "Resource": "*"
       }
   ]
}
```

**原因** 发生错误是因为**版本**被限制为几个选择值。

**解决方案** 解决方案是使用其中一个[有效的](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_version.html) **版本**元素值。目前，IAM 支持以下**版本**元素值:

**2012-10-17**——这是当前版本的政策语言。

*   **2008-10-17**——这是一个旧版本的策略语言，不支持新功能。
*   如果不包括**版本**元素，则该值默认为 **2008-10-17。**

了解更多关于 IAM 的信息

* * *

## 好了，现在你知道了！我们回顾了使用 IAM 时可能遇到的一些常见错误和解决方法。

寻找更多详细信息和提示来帮助您解决 IAM 的其他错误？查看我关于 IAM 的新入门课程，[身份和访问管理(IAM)概念](https://acloud.guru/learn/identity-and-access-management-concepts)。

如果你想更多地了解 Azure 中的 IAM，请查看 10 月份的免费课程 [IAM for Azure](https://acloud.guru/learn/17e4d37f-5a2a-4840-81a7-c2884425c576?) 。这是云专家免费提供的 24 个[免费云课程](https://acloudguru.com/blog/news/whats-free-at-a-cloud-guru-october-2020)之一。

从那来的还有更多！**云专家**提供学习路径、测验、认证准备等。

* * *

There’s more where that came from! **A Cloud Guru** offers learning paths, quizzes, certification prep, and more.