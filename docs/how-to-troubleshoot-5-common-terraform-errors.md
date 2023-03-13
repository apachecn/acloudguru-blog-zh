# Terraform 故障排除:5 个常见错误

> 原文：<https://acloudguru.com/blog/engineering/how-to-troubleshoot-5-common-terraform-errors>

关于 Terraform 有很多值得爱的地方——terra form 是我们去年在[搜索最多的话题](https://acloudguru.com/blog/engineering/the-cloud-top-ten-the-most-searched-cloud-topics-at-acg)——但没有什么是完美的。出现错误，需要排除故障。我们可以帮忙。

在本帖中，我们将详细介绍您在使用 Terraform 管理基础设施时可能遇到的一些常见 Terraform 错误，并提供故障排除技巧。我们走吧！

* * *

**通往更好职业的钥匙**

[立即开始 ACG](https://acloudguru.com/pricing) 通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室来改变你的职业生涯。

* * *

## Terraform 故障排除

在对有缺陷的 Terraform 配置进行故障排除时，您很可能会遇到以下四类错误之一:

1.  语言错误 —你遇到的大多数错误很可能属于这一类。这些是您的配置中的语法错误，Terraform 会打印出行号和错误的简要说明。
2.  **状态错误** —这也是在使用 Terraform 时很可能遇到的常见错误。这些错误大多来自于您的状态被锁定或不同步。如果您的状态不同步，Terraform 可能会破坏或改变现有资源。当您遇到这些错误时，您的配置总是第一个要查看的地方。在您修复了任何配置错误之后，查看一下您的状态，并确保那里的一切都考虑到了。如果您的配置或状态中缺少任何东西，您会希望通过刷新、导入或替换资源来确保一切都是同步的。
3.  **核心错误** —这些级别的错误通常意味着你已经发现了一个 bug，甚至可能会产生一个编写 Terraform 的 [Go 语言](https://acloudguru.com/blog/engineering/what-is-go-an-intro-to-googles-go-programming-language-aka-golang)的恐慌错误。这些错误通常意味着当您与 Terraform 核心开发团队在 GitHub 上提交问题时，您将把日志转储到一个文件中，并将其附加到一个模板化的错误报告中。
4.  **提供者错误** —提供者错误也是如此。这些错误围绕着提供者插件和不同版本插件的可能问题。通常这会导致在 GitHub 中向该提供者插件的开发团队提交一个问题。

我们将重点关注您在使用 Terraform 管理基础设施时可能遇到的五个常见错误。这些错误属于我们的前两类。我们将看看如何修复每一个错误，并检查寻找什么，希望在未来避免它们。让我们来看看我们的第一个错误。

* * *

**[获取 Terraform 备忘单](https://acloudguru.com/blog/engineering/the-ultimate-terraform-cheatsheet)**
**查看排名前十的 Terraform 命令，并在我们的 [Terraform 备忘单](https://acloudguru.com/blog/engineering/the-ultimate-terraform-cheatsheet)中获得您需要的所有基本命令的完整摘要，以充分利用这一直观的 IaC 工具。**

* * *

## 1.地形变量插值误差

当试图在不使用正确的插值语法的情况下向输入变量追加内容时，会出现 Terraform 变量插值错误。使用`terraform fmt`命令可以捕捉到这个错误。这将产生一个类似于下面示例的错误:

```
$ terraform fmt
Error: Invalid character

  on main.tf line 46, in resource "aws_instance" "web_app":
 46:     Name = $var.name-web_app

This character is not used within the language.

Error: Invalid expression

  on main.tf line 46, in resource "aws_instance" "web_app":
  46:     Name = $var.name-web_app

Expected the start of an expression, but found an invalid expression token.
```

这里你可以看到我们得到了两个错误。一个通知您无效的字符，另一个通知您无效的表达式。两者在同一条线上。

修复？

改变这一点:

```
 tags = {
      Name = $var.name-web_app
   }
 }
```

对此:

```
 tags = {
      Name = "${var.name}-web_app"
   }
 }
```

只要您在编写 Terraform 配置代码时记住使用必要的插值语法，此错误是常见的，并且很容易修复和避免。

## 2.地形循环误差

在你的地形配置中，循环错误被认为是循环逻辑的一个实例。当一个资源依赖于另一个首先被创建的资源，但是那个资源依赖于另一个被创建的资源时，它在 Terraform 中导致一个失败创建的循环。让我们看一个使用 AWS 安全组的例子。

当您运行一个`terraform validate`命令时，错误如下:

```
$ terraform validate

Error: Cycle: aws_security_group.sg_ping, aws_security_group.sg_8080
```

除了导致问题的资源之外，在这个错误中没有什么可说的。如果我们看一下下面的配置，并寻找 AWS 安全组，我们可以看到问题是什么。您可以看到，我们要创建的两个安全组正在寻找要首先创建的另一个安全组。它们相互依赖，由于这种依赖关系，Terraform 不能创建任何一种资源。

```
 resource "aws_security_group" "sg_ping" {
   name = "Allow Ping"

   ingress {
     from_port       = -1
     to_port         = -1
     protocol        = "icmp"
     security_groups = [aws_security_group.sg_8080.id]
   }
 }

 resource "aws_security_group" "sg_8080" {
   name = "Allow 8080"

   ingress {
     from_port       = 8080
     to_port         = 8080
     protocol        = "tcp"
     security_groups = [aws_security_group.sg_ping.id]
   }
 }
```

要解决这个问题，我们可以简单地将我们的安全组资源和安全组规则分离到单独的资源中。这样，我们的安全组就在需要使用依赖关系的规则创建之前创建，而安全组是在创建之后创建的，如下例所示。

```
resource "aws_security_group" "sg_ping" {
   name = "Allow Ping"
}

resource "aws_security_group" "sg_8080" {
   name = "Allow 8080"
}

resource "aws_security_group_rule" "allow_ping" {
    type = "ingress"
    from_port = -1
    to_port = -1
    protocol = "icmp"
    security_group_id = aws_security_group.sg_ping.id
    source_security_group_id = aws_security_group.sg_8080.id
}

resource "aws_security_group_rule" "allow_8080" {
    type = "ingress"
    from_port = 80
    to_port = 80
    protocol = "tcp"
    security_group_id = aws_security_group.sg_8080.id
    source_security_group_id = aws_security_group.sg_ping.id
}
```

## 3.每个错误的平台

Terraform for_each 属性允许您根据您定义的标准创建一组相似的资源。

在下面的例子中，我们创建了一组相似的实例，每个实例被分配给不同的安全组。Terraform 无法解析 aws_security_group。*.id，因为 splat 表达式只插入列表类型，而 for_each 属性是为映射类型保留的。因此，我们需要替换`*`并添加一个本地值来实现这一点。

```
$ terraform validate
Error: Invalid reference

  on main.tf line 44, in resource "aws_instance" "web_app":
  44:   for_each               = aws_security_group.*.id

A reference to a resource type must be followed by at least one attribute
access, specifying the resource name.

Error: Invalid "each" attribute

  on main.tf line 47, in resource "aws_instance" "web_app":
  47:   vpc_security_group_ids = [each.id]

The "each" object does not have an attribute named "id". The supported
attributes are each.key and each.value, the current key and value pair of the
"for_each" attribute set.
```

首先，我们将更改下面的资源块:

```
 resource "aws_instance" "web_app" {
   for_each               = aws_security_group.*.id
   ami                    = data.aws_ami.ubuntu.id
   instance_type          = "t2.micro"
   vpc_security_group_ids = [each.id]
   user_data              = <<-EOF
               #!/bin/bash
               echo "Hello, World" > index.html
               nohup busybox httpd -f -p 8080 &
               EOF
   tags = {
     Name = "${var.name}-learn"
   }
 }
```

对此:

```
resource "aws_instance" "web_app" {
   for_each               = local.security_groups
   ami                    = data.aws_ami.ubuntu.id
   instance_type          = "t2.micro"
   vpc_security_group_ids = [each.value]
   user_data              = <<-EOF
               #!/bin/bash
               echo "Hello, World" > index.html
               nohup busybox httpd -f -p 8080 &
               EOF
   tags = {
     Name = "${var.name}-learn-${each.key}"
   }
 }
}
```

请注意，我们已经将 for_each 值从`*`更改为`local.security_groups`，并将 vpc_security_groups_ids 从`[each.id]`更改为`[each.value]`。我们还需要对我们的标签做一个快速的更改，这样它也可以显示通过将`”${var.name}-learn”`更改为`”${var.name}-learn-${each.key}”`而创建的每个 web 应用程序，这将把虚拟机的编号附加到标签名称的末尾。

接下来，我们将创建一个本地块，它将把安全组列表转换成一个映射类型，如下例所示:

```
locals {
  security_groups = {
    sg_ping   = aws_security_group.sg_ping.id,
    sg_8080   = aws_security_group.sg_8080.id,
  }
}
```

现在，当您运行`terraform validate`时，for_each 错误应该会得到解决。

## 4.Terraform 输出错误

Terraform 输出错误可能有几种不同的原因，但最常见的原因是没有捕获您尝试捕获的所有资源。以下面的错误为例。

在这个例子中，因为在我们的主配置文件中使用了 for 表达式，所以我们的输出变量需要更新，这样我们的输出就可以获取我们试图显示的所有资源。让我们来看看。

```
$ terraform validate

 Error: Missing resource instance key

   on outputs.tf line 3, in output "instance_id":
    3:   value       = aws_instance.web_app.id

 Because aws_instance.web_app has "for_each" set, its attributes must be
 accessed on specific instances.

 For example, to correlate with indices of a referring resource, use:
     aws_instance.web_app[each.key]

 Error: Missing resource instance key

   on outputs.tf line 8, in output "instance_public_ip":
    8:   value       = aws_instance.web_app.public_ip

 Because aws_instance.web_app has "for_each" set, its attributes must be
 accessed on specific instances.

 For example, to correlate with indices of a referring resource, use:
     aws_instance.web_app[each.key]

 Error: Missing resource instance key

   on outputs.tf line 13, in output "instance_name":
   13:   value       = aws_instance.web_app.tags

 Because aws_instance.web_app has "for_each" set, its attributes must be
 accessed on specific instances.

 For example, to correlate with indices of a referring resource, use:
     aws_instance.web_app[each.key]
```

在上面的错误中，我们试图输出应用 id、公共 ip 和实例的标签。由于我们有多个这样的变量，Terraform 抛出了一个错误，因为我们的变量只需要一个，而 Terraform 不知道应该从输出中获取哪一个。下面是我们的 outputs.tf 文件的样子:

```
 output "instance_id" {
   description = "ID of the EC2 instance"
    value       = aws_instance.web_app.id
 }

 output "instance_public_ip" {
   description = "Public IP address of the EC2 instance"
    value       = aws_instance.web_app.public_ip
 }

output "instance_name" {
   description = "Tags of the EC2 instance"
   value        = aws_instance.web_app.tags
}
```

在这里，您可以看到我们的输出变量只是为了获取单个 id、单个公共 ip 和单个标签而编写的。

下面是我们用来修复此错误的代码示例:

```
 output "instance_id" {
   description = "ID of the EC2 instance"
    value       = [for instance in aws_instance.web_app: instance.id]
 }

 output "instance_public_ip" {
   description = "Public IP address of the EC2 instance"
    value       = [for instance in aws_instance.web_app: instance.public_ip]
 }

output "instance_name" {
   description = "Tags of the EC2 instance"
   value        = [for instance in aws_instance.web_app: instance.tags.Name]
}
```

在上面的例子中，我们将通过使用`for`表达式来捕获所有实例 id、公共提示和每个实例的标签，从而修复错误。

## 5.地形状态误差

您的 Terraform 状态文件存储了有关已配置资源的信息。它会将资源映射到您的配置，然后跟踪所有相关的元数据。如果状态不同步，Terraform 可能会改变你现有的资源。排除任何配置错误后，最好检查一下您的状态。通过刷新、导入或替换资源，确保您的配置同步。

使用 Terraform 状态时，您可能会收到的一个错误是 Terraform 正在获取状态锁。下面是一个错误示例:

```
Acquiring state lock. This may take a few moments…

  Error: Error acquiring the state lock

  Error message: ConditionalCheckFailedException: The conditional request failed
  Lock Info:
    ID:        c2024f2b-b615-05bf-e516-e49ed2852087
    Path:      <…>
    Operation: OperationTypePlan
    Who:       <…>
    Version:   1.0.2
    Created:   2021-07-28 14:54:32.498842 +0000 UTC
    Info:      

  Terraform acquires a state lock to protect the state from being written
  by multiple users at the same time. Please resolve the issue above and try
  again. For most commands, you can disable locking with the “-lock=false”
  flag, but this is not recommended.
```

这种情况偶尔会发生，通常意味着另一个团队成员正在对基础设施进行更新。有时候锁会卡住。为了解决这个问题，我们可以尝试一些事情。

首先，我们可以运行带有`-lock=false`标志的`apply`命令，就像错误告诉我们的那样。以下是该命令的一个示例:

```
terraform force-unlock <ID>
```

有时候这个命令不起作用。你可以通过一个`-force`标志到命令上来尝试，如果第一个命令不工作就强制解锁如下:

```
terraform force-unlock -force <ID>
```

您可以在错误消息中找到这些命令的 ID。

如果两个命令都不能解锁状态，您可以等待几分钟左右，然后再试一次。最后，尽量杀死悬挂 terraform 进程。如果你在 Windows 机器上运行 Terraform，在任务管理器中找到进程，杀死它。如果您在 Linux 或 Mac 上运行 Terraform，请运行以下命令:

```
ps aux | grep terraform
kill -9 <process_id>
```

如果其他方法都失败了，这应该可以解决锁的问题。

* * *

[**读作:云状，地形，还是 CDK？AWS 上的 IAC 指南**](https://acloudguru.com/blog/engineering/cloudformation-terraform-or-cdk-guide-to-iac-on-aws) *概述 AWS 中可用的 IaC 工具，以及如何在它们之间进行选择。*

* * *

## 动手排除 Terraform 故障

这就是了，大师们！这些只是您在使用 Terraform 时可能会遇到的一些常见错误。每个错误通常很容易修复，你只需要知道你在看什么。

Terraform 很好地解释了错误，并直接指出了配置中的问题。我发现对 Terraform 进行故障诊断比我用过的其他工具更容易。错误消息的详细程度给我留下了深刻的印象，我非常喜欢它告诉您哪个配置文件有问题，以及在文件的哪里可以找到问题。

希望这篇文章能帮助你容易地识别和修复你在使用 Terraform 时遇到的一些常见错误。保持威严，大师们——让我们继续地球化！

想了解更多有关如何排除 Terraform 故障的信息？查看我的使用 Terraform 课程的[动手故障排除。](https://acloudguru.com/course/hands-on-troubleshooting-with-terraform)

您还可以浏览我们的 [Terraform 培训](https://acloudguru.com/training-library/terraform-training)、[顶尖开发技能和技术](https://acloudguru.com/blog/engineering/to-succeed-in-devops-careers-level-up-these-skills)以及[本月在 ACG](https://acloudguru.com/blog/news/whats-free-at-acg) 有什么免费的。

通过在推特上关注 ACG、关注 T2、关注脸书、关注 YouTube 上的云专家，或者加入我们令人敬畏的不和谐社区。