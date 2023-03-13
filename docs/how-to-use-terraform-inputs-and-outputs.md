# 使用和声明 Terraform 输出-输入指南

> 原文：<https://acloudguru.com/blog/engineering/how-to-use-terraform-inputs-and-outputs>

Terraform 是一个非常强大和高效的工具，用于在您的环境中部署和管理基础架构。有了这么多的提供者和模块，没有什么是 Terraform 做不到的。

Terraform 的最大吸引力在于，您可以使用相同的配置在多个环境中创建资源，或者随着基础架构的增长和变得更加复杂，使用变量的需求也会增长。实现这一点的方法是使用输入和输出变量。

在这篇文章中，我们将探讨什么是变量，以及如何在你的地形配置中使用它们。

## 什么是 Terraform **输出变量**？

将输出变量视为 Terraform 模块的返回值。输出变量有几种用途。以下是一些例子:

*   我们可以使用输出向父模块公开子模块资源属性的子集。
*   在运行`terraform apply`之后，我们可以在 CLI 输出中使用输出来打印根模块的值。
*   如果使用远程状态，其他配置可以通过`terraform_remote_state`数据源访问根模块的输出

这些只是我们为什么要使用输出变量的几个例子。要声明输出值，必须在输出块中声明它们，如下例所示。

```
 output "instance_ip_addr" {
  value = aws_instance.server.private_ip
} 
```

声明输出变量时，有三个可选参数可供使用。

*   **描述**–您可以使用此参数描述每个值的用途。

```
 output "instance_ip_addr" {
  value       = aws_instance.server.private_ip
  description = "The private IP address of the main server instance."
} 
```

*   **敏感**–使用该选项时，Terraform 将隐藏`terraform plan`和`terraform apply`命令输出中标记为敏感的值。

```
 output "db_password" {
  value       = aws_db_instance.db.password
  description = "The password for logging in to the database."
  sensitive   = true
} 
```

*   **Depends _ on**–当父模块访问其子模块之一导出的输出值时，该选项非常有用。该输出值的依赖性允许 Terraform 正确地确定在其他模块中定义的资源之间的依赖性。

```
 output "instance_ip_addr" {
  value       = aws_instance.server.private_ip
  description = "The private IP address of the main server instance."

  depends_on = [
    # Security group rule must be created before this IP address could
    # actually be used, otherwise the services will be unreachable.
    aws_security_group_rule.local_access,
  ]
} 
```

在构建配置时，输出变量非常有用。尤其是当任何部署基础设施或基础设施中的资源的人需要特殊的指令或登录信息时。让我们来总结一下使用变量的第三种方式。

## **如何使用局部变量**

局部变量为表达式指定一个名称，这样它就可以在一个模块中多次使用而不会重复。如果您熟悉大多数编程语言，局部变量就像函数的临时局部变量。下面是一个如何声明局部变量的例子。

```
 locals {
  # Common tags to be assigned to all resources
  common_tags = {
    Service = local.service_name
    Owner   = local.owner
  }
} 
```

然后，您可以通过在配置的资源块中引用类似于 so : `tags = local.common_tags`的表达式来调用局部变量。局部值只能在声明它的模块内的表达式中访问。

你可能会问，我什么时候使用局部变量！局部变量有助于避免在一个配置中多次重复相同的值或表达式。但是，如果它们被过度使用，它们还会隐藏实际使用的值，使配置很难被未来的配置参与者阅读。建议适量使用。

## **什么是 Terraform 输入变量？**

我们已经谈了很多输出变量，但现在让我们谈谈输入变量及其用途。

输入变量是将参数应用于 Terraform 配置的主要方式。它允许在不改变 Terraform 模块自己的源代码的情况下定制配置的各个方面，并允许在不同的配置之间共享模块。

您可以在配置的根模块中声明变量。您可以使用 CLI 选项和环境变量来设置它们。如果您熟悉大多数编程语言，Terraform 模块可以与函数定义相媲美:

*   输入变量类似于函数参数。
*   输出值类似于函数返回值。
*   局部值类似于函数的临时局部变量。

* * *

![Terraform Cheatsheet](img/079f543cc60333160171f62053f9585d.png)

*需要更多地形技巧？查看我们的[终极地形命令备忘单](https://acloudguru.com/blog/engineering/the-ultimate-terraform-cheatsheet)。*

* * *

## 我们如何声明一个输入变量？

需要在地形配置中使用`variable block`声明输入变量。下面的例子是一个`variable block`的样子:

```
 variable "image" {
  type = string
}

variable "availability_zone_names" {
  type = list(string)
  default = ["us-east-1]
} 
```

在这个例子中，我们声明了两个变量。变量名称后的标签是该变量的名称。这需要在声明的所有其他变量中是唯一的。

如果你想添加另一个图像变量，你需要做类似于`image_0`和`image_1` 这样的事情。

接下来，您将定义类型，在第一个例子中是`string`类型约束。下一个变量是定义可用性区域。你可以在这里看到`list(string`中的类型，如果没有定义`us-east-1`则有一个默认值。这样做的目的是，如果变量没有提供值，那么它将使用默认值。

以下是可以使用的可选参数和类型约束的列表:

**自变量:**

*   `default`–默认值，使变量可选。
*   `type`–指定变量可接受的值类型。
*   `description`–指定输入变量的文档。
*   `validation`–定义验证规则，通常除了类型约束之外。
*   `sensitive`–当变量在配置中使用时，这将限制 Terraform UI 输出。

**类型约束**

**可用于类型约束的类型构造函数**

*   `list(<TYPE>)`
*   `set(<TYPE>)`
*   `map(<TYPE>)`
*   `object({<ATTR_NAME> = <TYPE>, … })`
*   `tuple([<TYPE>, …])`

在变量块中，type 参数允许您限制作为变量值接受的值。如果不设置约束，则类型参数将接受任何值。类型约束是可选的，但鼓励使用。类型约束允许 Terraform 在解决问题时返回有用的错误消息。

*[云状、地形或 CDK？查看我们在 AWS 上的 IaC 指南。](https://acloudguru.com/blog/engineering/cloudformation-terraform-or-cdk-guide-to-iac-on-aws)*

### **使用变量**

可通过使用`var.<variable_name>`从 terraform 模块块内访问变量值。下面我们有一个例子来证明这一点。

```
 resource "aws_instance" "example" {
  instance_type = "t2.micro"
  ami           = var.image_id
} 
```

变量值只能在声明它的模块内的表达式中访问。

## **在 Terraform 中分配变量的多种方式**

我们已经复习了一些关于输入变量的基础知识。现在让我们看几个如何声明变量的例子。

下面的例子说明了如何从命令行声明变量。

```
 $ terraform apply -var="image_id=ami-abc123"
$ terraform apply -var='image_id_list=["ami-abc123","ami-def456"]' -var="instance_type=t2.micro"
$ terraform apply -var='image_id_map={"us-east-1":"ami-abc123","us-east-2":"ami-def456"}' 
```

这里你可以看到我们通过`-var`选项向`terraform apply`命令提供变量来指定我们的变量。如果我们有多个变量，我们可以创建一个扩展名为`.tfvars`或`.tfvars.json`的变量文件，然后在命令行中指定该文件，如下例所示。

```
 $ terraform apply -var-file="testing.tfvars" 
```

变量定义文件使用与其余 Terraform 配置文件相同的语法。

我们也可以使用环境变量来设置 Terraform 中的变量。你可以像下面的例子一样简单的导出你的变量。

```
 $ export TF_VAR_image_id=ami-abc123 
```

### **事情是有顺序的！**

在声明变量时，您需要知道变量定义的优先级。Terraform 以特定的顺序加载变量。顺序如下:

*   环境变量
*   `terraform.tfvars`文件(如果存在)
*   `terraform.tfvars.json`文件(如果存在)
*   任何`*.auto.tfvars`或`*.auto.tfvars.json`文件(如果存在)
*   命令行上的任何`-var`和`-var-file`选项。

这将有助于构建一些较大的配置文件，或者尝试使用一个配置将基础架构部署到多个云环境。

这是一堂关于什么是输入、输出和局部变量以及如何在 Terraform 中使用它们的速成课。它们在构建你的地形配置时非常有用，并且会在你开始构建更复杂的，我指的是有趣的地形配置时帮助你。玩得开心点，我的 Terraform gurus，让我们继续一次在 Terraform block 上建造未来吧！

* * *

[![Taylor Dolezal](img/622e5ae10860dc793cb426955ac8abc6.png)](https://get.acloudguru.com/kubernetes-azure-hashicorp-way-webinar)

[**WATCH: Kubernetes + Azure，哈希公司之道**](https://get.acloudguru.com/kubernetes-azure-hashicorp-way-webinar) 有没有想过创建一种标准化的方法来部署您的应用程序，以及如何安全地这样做？在 Azure 上使用 HashiCorp 堆栈是一个很好的起点！观看此[免费点播网络研讨会](https://get.acloudguru.com/kubernetes-azure-hashicorp-way-webinar)，HashiCorp 的 Taylor Dolezal 将介绍使用地形、拱顶和航路点的潜力。

* * *

想要提升你的地形技能吗？查看我们的 [HashiCorp 认证 Terraform 助理课程](https://acloudguru.com/course/hashicorp-certified-terraform-associate)。

* * *

**What are Terraform **Output Variables**?**

将输出变量视为 Terraform 模块的返回值。输出变量有几种用途。[在这里看例子！](https://acloudguru.com/blog/engineering/how-to-use-terraform-inputs-and-outputs)

**How to use local variables in terraform?**

局部变量为表达式指定一个名称，这样它就可以在一个模块中多次使用而不会重复。如果您熟悉大多数编程语言，局部变量就像函数的临时局部变量。

****What are Terraform Input Variables?****

输入变量是将参数应用于 Terraform 配置的主要方式。它允许在不改变 Terraform 模块自己的源代码的情况下定制配置的各个方面，并允许在不同的配置之间共享模块。

**How to declare variables in Terraform?**

您可以通过-var 选项来指定我们的变量，从而为 terraform apply 命令提供变量。如果我们有多个变量，我们可以用。tfvars 或. tfvars.json 文件扩展名，然后在命令行上指定该文件。

## 获得更好职业所需的技能。

掌握现代技术技能，获得认证，提升您的职业生涯。查看我们当前的[免费课程](https://acloudguru.com/blog/news/whats-free-at-acg-may-2021)或[获得 7 天免费试用](https://acloudguru.com/pricing)。无论您是新手还是经验丰富的专业人士，您都可以在 ACG 的帮助下推进您的云计算职业生涯。