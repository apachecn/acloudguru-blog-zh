# Azure 事件中心和流分析:穿越流

> 原文：<https://acloudguru.com/blog/engineering/crossing-the-streams-with-azure-event-hubs-and-stream-analytics>

由 Abhishek Gupta
[博客](https://medium.com/@abhishek1987) | [LinkedIn](https://in.linkedin.com/in/abhirockzz) | [推特](https://twitter.com/abhi_tweeter)

这篇博客提供了一个如何使用 [Azure Stream Analytics](https://docs.microsoft.com/azure/stream-analytics/stream-analytics-introduction?WT.mc_id=acloudguru-blog-abhishgu) 处理来自 [Azure Event Hubs](https://docs.microsoft.com/azure/event-hubs/event-hubs-about?WT.mc_id=acloudguru-blog-abhishgu) 的流数据的实际例子。您应该能够使用 Azure 门户(或 Azure CLI)完成本教程，而无需编写任何代码。在这篇博文的最后，还有其他资源可以用来探索使用 Azure Stream Analytics 进行流处理。

**包括哪些内容？**

*   用例、解决方案及其组成部分的快速概述
*   如何设置所需的 Azure 服务:事件中心、流分析和 Blob 存储
*   如何使用示例数据配置和测试 Azure 流分析作业
*   如何运行 Azure 流分析作业并使用实时数据进行测试

*想了解更多关于 Azure 认证的信息吗？*
*查看我们的 [Azure 认证和学习路径。](https://acloudguru.com/azure-cloud-training)*

## **概述**

Azure Stream Analytics 是一个实时分析和复杂事件处理引擎，旨在同时分析和处理来自多个来源的大量快速流数据。它支持一个`Job`的概念，每个由一个`input`、`query`和一个`output`组成。Azure Stream Analytics 可以从 Azure Event Hub(包括 Apache Kafka 的 Azure Event Hub)、Azure IoT Hub 或 Azure Blob 存储中`ingest`数据。`query`基于 SQL 查询语言，可用于轻松过滤、排序、聚合和连接一段时间内的流数据。

假设您有一个应用程序，它接受来自客户的已处理订单，并将它们发送到 Azure Event Hubs。该要求是处理“原始”订单数据，并用额外的客户信息(如姓名、电子邮件、位置等)丰富它。要做到这一点，您可以构建一个下游服务，该服务将从事件中心消费这些订单并处理它们。在这个例子中，这个服务恰好是一个 Azure 流分析作业(当然，我们将在后面探讨它！)

* * *

作为基础设施的一部分，您可以使用 Kafka 来处理消息传递。想了解更多关于使用简单 HTTP 请求生成和使用消息的知识吗？尝试我们的动手实验，获得使用 REST 代理消费 [Kafka 数据所需的请求经验。](https://acloudguru.com/hands-on-labs/consuming-kafka-messages-with-confluent-rest-proxy)

* * *

为了构建这个应用程序，我们需要从外部系统(例如，一个数据库)获取这个客户数据，对于订单信息中的每个客户 ID，我们将查询这个客户的详细信息。这将满足低速数据系统或不需要考虑端到端处理延迟的系统。但这将对高速流数据的实时处理提出挑战。

当然，这不是一个新奇的问题！这篇博文的目的是展示如何使用 Azure Stream Analytics 实现一个解决方案。以下是各个组件:

### 输入数据源

Azure 流分析作业连接到[一个或多个数据输入](https://docs.microsoft.com/azure/stream-analytics/stream-analytics-add-inputs?WT.mc_id=acloudguru-blog-abhishgu)。每个输入定义了一个到现有数据源的连接——在本例中是[，它的 Azure Event Hubs](https://docs.microsoft.com/azure/stream-analytics/stream-analytics-define-inputs?WT.mc_id=acloudguru-blog-abhishgu#stream-data-from-event-hubs) 。

单个订单是一个 JSON 有效负载，如下所示:

```
{
    "id": "42",
    "custid": "4",
    "amount": "100"
}
```

### 参考数据

客户信息作为[参考数据](https://docs.microsoft.com/azure/stream-analytics/stream-analytics-use-reference-data?WT.mc_id=acloudguru-blog-abhishgu)提供。虽然，客户信息可能会改变(例如，如果客户改变了她的电话号码)，但出于本例的目的，我们将把它视为存储在 [Azure Blob 存储容器](https://docs.microsoft.com/azure/stream-analytics/stream-analytics-use-reference-data?WT.mc_id=acloudguru-blog-abhishgu#azure-blob-storage)中的 [`static`引用数据](https://docs.microsoft.com/azure/stream-analytics/stream-analytics-use-reference-data?WT.mc_id=acloudguru-blog-abhishgu#static-reference-data)。

### 询问

这是我们解决方案的核心！它基于匹配的客户 ID(在`customers`数据集中是`id`,在`orders`流中是`id`)将来自 Azure Event Hubs 的订单数据(连续流)与静态参考客户数据连接起来

### 输出接收器

简而言之，[输出](https://docs.microsoft.com/azure/stream-analytics/stream-analytics-define-outputs?WT.mc_id=acloudguru-blog-abhishgu)让您存储和保存流分析作业的结果。在这个例子中，为了简单起见，我们[继续使用 Azure Event Hubs(一个不同的主题)](https://docs.microsoft.com/azure/stream-analytics/stream-analytics-define-outputs?WT.mc_id=acloudguru-blog-abhishgu#event-hubs)作为输出。

现在您已经有了一个概念性的概述，是时候深入了解了。你只需要一个 Azure 账户。如果你还没有，就免费拿一个。

## 初始设置

在本节中，您将:

*   创建 Azure 事件中心命名空间和主题
*   创建 Azure Blob 存储帐户和容器
*   创建 Azure Stream Analytics 作业，并为该作业配置事件中枢和 Blob 存储输入

### Azure 活动中心

您需要创建一个[事件中心名称空间](https://docs.microsoft.com/azure/event-hubs/event-hubs-features?WT.mc_id=acloudguru-blog-abhishgu#namespace)和中心(主题)。有很多选项，包括 [Azure Portal](https://docs.microsoft.com/azure/event-hubs/event-hubs-create?WT.mc_id=acloudguru-blog-abhishgu) 、 [Azure CLI](https://docs.microsoft.com/azure/event-hubs/event-hubs-quickstart-cli?WT.mc_id=acloudguru-blog-abhishgu) 、 [ARM 模板](https://docs.microsoft.com/azure/event-hubs/event-hubs-resource-manager-namespace-event-hub?WT.mc_id=acloudguru-blog-abhishgu)或 [Azure PowerShell](https://docs.microsoft.com/azure/event-hubs/event-hubs-quickstart-powershell?WT.mc_id=acloudguru-blog-abhishgu)

* * *

Azure 资源管理器(ARM)模板提供了一种使用文本文件定义 Azure 资源和配置的强大方法。使用我们的动手实验室来了解如何定位和利用微软的公共 [Azure quickstart 模板。](https://acloudguru.com/hands-on-labs/deploy-a-github-quickstart-arm-template-using-the-azure-portal)

* * *

请注意，您需要创建**两个**主题:

*   **输入**(你可以把它命名为`orders` ): Azure Stream Analytics 将把它作为订单数据的(流)“源”
*   **输出**(你可以将它命名为`customer-orders` ): Azure Stream Analytics 将使用它作为一个“接收器”来存储查询处理的丰富数据

### Azure Blob 存储

你需要创建一个 Azure 存储帐户。[这个快速入门](https://docs.microsoft.com/azure/storage/common/storage-account-create?tabs=azure-portal&WT.mc_id=acloudguru-blog-abhishgu)带你完成这个过程，并为 Azure 门户、Azure CLI 等提供指导。一旦完成，继续前进，[使用 Azure 门户或](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-portal?WT.mc_id=acloudguru-blog-abhishgu#create-a-container) [Azure CLI](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-cli?WT.mc_id=acloudguru-blog-abhishgu#create-a-container) 创建一个容器。

将下面的 JSON 保存到一个文件中，并上传到您刚刚创建的存储容器中。

```
[
    {
        "id": "1",
        "name": "Willis Collins",
        "location": "Dallas"
    },
    {
        "id": "2",
        "name": "Casey Brady",
        "location": "Chicago"
    },
    {
        "id": "3",
        "name": "Walker Wong",
        "location": "San Jose"
    },
    {
        "id": "4",
        "name": "Randall Weeks",
        "location": "San Diego"
    },
    {
        "id": "5",
        "name": "Gerardo Dorsey",
        "location": "New Jersey"
    }
]
```

### Azure 流分析

首先创建一个 Azure 流分析作业。如果你想使用 Azure 门户，只需遵循本节概述的[步骤](https://docs.microsoft.com/azure/stream-analytics/stream-analytics-quick-create-portal?WT.mc_id=acloudguru-blog-abhishgu#create-a-stream-analytics-job)或者如果你不喜欢点击 UI，使用 [Azure CLI 代替](https://docs.microsoft.com/azure/stream-analytics/quick-create-azure-cli?WT.mc_id=acloudguru-blog-abhishgu#create-a-stream-analytics-job)。

**配置 Azure 事件中心输入**

打开您刚刚创建的 Azure Stream Analytics 作业，并将 Azure Event Hubs 配置为一个**输入**。以下是一些屏幕截图，应该可以指导您完成这些步骤:

从左侧菜单中选择**输入**

选择 **+添加流输入>事件中心**

输入事件中心详细信息-门户为您提供了从现有事件中心命名空间和订阅中的相应事件中心中进行选择的便利，因此您只需选择正确的名称即可。

**配置 Azure Blob 存储输入:**

从左侧菜单中选择**输入**

选择**添加参考输入>斑点存储**

输入/选择 Blob 存储详细信息

一旦完成，您应该会看到以下**输入**:

## 使用示例数据配置查询和测试

Azure Stream Analytics 允许你用样本数据测试你的流查询。在本节中，我们将分别为事件中心和 Blob 存储输入上传订单和客户信息的样本数据。

### **上传样本数据为** `**orders:**`

**打开 Azure Stream Analytics 作业，选择**查询**并上传示例订单数据以供事件中心输入**

**将下面的 JSON 保存到一个文件并上传。**

```
[
    {
        "id": "42",
        "custid": "1",
        "amount": "100"
    },
    {
        "id": "43",
        "custid": "2",
        "amount": "200"
    },
    {
        "id": "44",
        "custid": "3",
        "amount": "300"
    },
    {
        "id": "45",
        "custid": "3",
        "amount": "150"
    },
    {
        "id": "46",
        "custid": "4",
        "amount": "170"
    },
    {
        "id": "47",
        "custid": "5",
        "amount": "150"
    },
    {
        "id": "48",
        "custid": "5",
        "amount": "200"
    }

]
```

### ****上传客户样本数据****

**打开 Azure Stream Analytics 作业，选择**查询**并为 Blob 存储输入上传样本订单数据**

**您可以上传之前上传到 Blob 存储的 JSON 文件。**

**现在，配置并运行以下查询:**

```
SELECT o.id as order_id, o.amount as purchase, o.custid as customer_id, c.name customer_name, c.location as customer_location
FROM orders o
JOIN customers c  
ON o.custid = c.id 
```

**打开 Azure Stream Analytics 作业，选择**查询**,然后按照下面截图中描述的步骤操作:**

**选择**查询>进入查询>测试查询**别忘了选择**保存查询****

**查询`JOINs`根据匹配的客户 ID(在`customers`数据集中是`id`,在`orders`流中是`id`)用静态引用`customers`数据(来自 Blob 存储)对来自事件中心的数据进行排序。)**

***探究* [*引用数据* *加入* *操作*](https://docs.microsoft.com/stream-analytics-query/reference-data-join-azure-stream-analytics?WT.mc_id=acloudguru-blog-abhishgu) *或者挖掘到* [*流分析查询引用*](https://docs.microsoft.com/stream-analytics-query/stream-analytics-query-language-reference?WT.mc_id=acloudguru-blog-abhishgu)**

## **使用流数据测试作业**

**很高兴能够使用样本数据来测试我们的流解决方案。让我们继续尝试将实际数据(订单)端到端地流入活动中心。**

**运行`Job`需要一个`Output`。为了配置输出，选择**输出> +添加>事件中枢****

**输入事件中心详细信息:门户为您提供了从现有事件中心名称空间和订阅中的相应事件中心中进行选择的便利，因此您只需选择正确的名称空间即可。**

### **开始工作**

**在 Azure Stream Analytics 界面，选择**概览**，点击**开始**并确认**

**等待作业开始，您应该看到`Status`变为**运行****

### ****测试端到端流量****

****为了简单起见，我们可以使用`kafkacat` CLI 来生成订单和消费丰富的事件(而不是程序)。只需[安装它](https://github.com/edenhill/kafkacat#install)，你就可以开始了。****

*****注意:虽然我使用了`kafkacat`，但是您可以自由选择任何其他机制(CLI 或编程)。这个* [*文档提供了大量的例子*](https://docs.microsoft.com/azure/event-hubs/apache-kafka-developer-guide?WT.mc_id=%20acloudguru-blog-abhishgu)****

****创建一个包含事件中心信息的`kafkacat.conf`文件:****

```
**metadata.broker.list=<namespace><namespace>.servicebus.windows.net:9093
security.protocol=SASL_SSL
sasl.mechanisms=PLAIN
sasl.username=$ConnectionString
sasl.password=Endpoint=sb://<enter namespace=""><namespace>.servicebus.windows.net/;SharedAccessKeyName=RootManageSharedAccessKey;SharedAccessKey=</enter></namespace>**
```

******启动消费者收听来自事件中心的输出主题******

****让我们首先启动将连接到输出主题(`customer-orders`)的消费者流程，该输出主题将从 Azure Stream Analytics 获取丰富的订单信息****

****在终端中:****

```
**export KAFKACAT_CONFIG=kafkacat.conf
kafkacat -b <enter namespace=""><namespace>.servicebus.windows.net:9093 -t customer-orders

//output
% Reading configuration from file kafkacat.conf
% Auto-selecting Consumer mode (use -P or -C to override)</enter>**
```

****这将阻塞，等待来自`customer-orders`的记录。****

******在另一个终端，开始向`orders`主题**发送订单信息****

```
**kafkacat -P -b <enter namespace=""><namespace>.servicebus.windows.net:9093 -t orders</enter>**
```

****您可以通过`stdout`发送订单数据。只需一次粘贴一个，并观察另一个终端的输出:****

```
**{"id": "22","custid": "1","amount": "100"}
{"id": "23","custid": "2","amount": "200"}
{"id": "24","custid": "3","amount": "300"}
{"id": "25","custid": "4","amount": "400"}
{"id": "26","custid": "15","amount": "500"}**
```

****您在消费者终端上看到的输出应该类似于以下内容:****

```
**...
% Reached end of topic customer-orders [0] at offset 0
{"order_id":"22","purchase":"100","customer_id":"11","customer_name":"Willis Collins","customer_location":"Dallas"}

% Reached end of topic customer-orders [0] at offset 1
{"order_id":"23","purchase":"200","customer_id":"2","customer_name":"Casey Brady","customer_location":"Chicago"
...**
```

****请注意订单信息现在是如何被客户数据(本例中是姓名、位置)丰富的。您可以随意使用本主题中的信息。例如，您可以将这个丰富的物化视图持久化到 [Azure Cosmos DB](https://docs.microsoft.com/azure/stream-analytics/stream-analytics-define-outputs?WT.mc_id=devto-blog-abhishgu#azure-cosmos-db) ，触发一个 [Azure 函数](https://docs.microsoft.com/azure/stream-analytics/stream-analytics-define-outputs?WT.mc_id=devto-blog-abhishgu#azure-functions)等等。****

****不出所料，您不会看到与客户(其 ID 不在参考客户数据(在 Blob 存储中)中)下的订单相对应的丰富事件，因为 *JOIN* 标准是基于客户 ID 的。****

****这就把我们带到了本教程的结尾！我希望它能帮助你开始使用 Azure Stream Analytics，并在进入更复杂的用例之前进行测试。****

## ****接下来去哪里？****

****除此之外，还有大量的材料供你挖掘。****

## ****结论****

****高速实时数据带来了使用传统架构难以应对的挑战，其中一个问题就是*连接*这些数据流。根据不同的用例，定制的解决方案可能会更好地为您服务，但是这需要花费大量的时间和精力来做好。如果可能的话，您可能想要考虑提取您的数据处理架构的一部分，并将繁重的工作交给为这类问题定制的服务。****

****在这篇博文中，我们探索了一种可能的解决方案，通过结合使用 Azure Event Hubs 获取数据和 Azure Stream Analytics 使用 SQL 处理数据来实现流连接。这些都是功能强大的现成服务，您可以配置和使用它们，而无需设置任何基础架构，而且由于有了云，这些解决方案中涉及的分布式系统的底层复杂性完全从我们这里抽象出来。****

*****想了解更多关于 Azure 认证的信息吗？*
*查看我们的 [Azure 认证和学习路径。](https://acloudguru.com/azure-cloud-training)*****