# 构建无服务器的 Kafka 数据管道

> 原文：<https://acloudguru.com/blog/engineering/building-a-serverless-kafka-data-pipeline>

无服务器服务允许我们构建应用程序，而不必担心底层基础设施。就 Apache Kafka 而言，这允许开发人员避免配置、扩展和管理其集群的资源利用。在这篇文章中，我将使用亚马逊 MSK 无服务器集群创建一个无服务器 Kafka 集群，并展示如何创建无服务器生产者和消费者。

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## 如何启动**无服务器 Kafka 集群**

Apache Kafka 是一个分布式事件存储和流处理平台。因为它具有高度的可伸缩性和弹性，所以它提供了一种将数据处理与源和目标分离的机制。

Kafka 可以根据您的工作负载进行定制，这会带来运营开销。使用无服务器 Kafka，代价是您失去了配置集群容量的灵活性，但您获得了通过单一界面使用 Kafka 的能力，该界面只为客户端提供一个端点。

要开始使用 AWS，您可以从亚马逊 MSK 控制台页面创建一个集群。

![image.png](img/a36e4454aee0b39159d21ba0283a0285.png)

有了无服务器，就不用担心配置了。您只需继续操作，几分钟内就可以设置好集群。

![image.png](img/361f18dbe21c8289a25b195c15790ff5.png)

当您不知道需要处理多少数据时，入口的默认选项 200 Mib/s 和 400 Mib/s 非常适合 Kafka 工作负载的初学者。如果您的工作负载增加，并且无服务器集群无法满足默认的写/读吞吐量，您可以探索使用[托管的 AWS Kafka 集群](https://aws.amazon.com/msk/)，它提供了针对您的工作负载调整集群的灵活性。

集群启动后，您可以在控制台的 properties 选项卡中查看客户机所需的 API 端点。

![image.png](img/68e6c7969cb7981e79f4711591724021.png)

有关设置集群的更多信息，请查看官方[文档](https://docs.aws.amazon.com/msk/latest/developerguide/serverless-getting-started.html)。

## **创建无服务器 Kafka 客户端**

一旦集群启动，我们就可以创建 Kafka 客户端，将数据发送到集群，并从集群中进行消费。在本节中，我将解释如何:

*   为 Lambda 函数设置所需的 IAM 权限
*   为 Lambda 函数构建一个 Docker 映像
*   配置 Lambda 函数以与无服务器 Kafka 集群通信

### **设置权限**

目前，与集群通信需要基于 IAM 的身份验证。以下是可用于客户端的示例策略。确保用您的值替换`REGION`、`Account-ID`和`CLUSTER_NAME`。

```
{
   "Version": "2012-10-17",
   "Statement": [
       {
           "Effect": "Allow",
           "Action": [
               "kafka-cluster:Connect",
               "kafka-cluster:AlterCluster",
               "kafka-cluster:DescribeCluster"
           ],
           "Resource": [
               "arn:aws:kafka:REGION:Account-ID:cluster/CLUSTER_NAME/*"
           ]
       },
       {
           "Effect": "Allow",
           "Action": [
               "kafka-cluster:*Topic*",
               "kafka-cluster:WriteData",
               "kafka-cluster:ReadData"
           ],
 "Resource": [
               "arn:aws:kafka:REGION:Account-ID:topic/CLUSTER_NAME/*"
           ]
       },
       {
           "Effect": "Allow",
           "Action": [
               "kafka-cluster:AlterGroup",
               "kafka-cluster:DescribeGroup"
           ],
           "Resource": [
               "arn:aws:kafka:REGION:Account-ID:group/CLUSTER_NAME/*"
           ]
       }
   ]
}
```

接下来，我们可以为 Lambda 函数创建一个新角色，并将上面的策略附加到该角色。

![image.png](img/78ad00336a8a502da47eba0ecf2a8882.png)

此外，该角色将需要 AWSLambdaVPCAccessExecutionRole 策略，因为该功能需要部署在与无服务器集群相同的 VPC 中。

![image.png](img/ebaee5315b250ed5130af52385796ada.png)

#### **构建 Docker 图像**

对于我们的 Lambda 函数，我们将使用一个定制容器，它具有连接到 Kafka 集群所需的所有先决条件。下面是一个可以用来构建 Kafka 客户端 Lambda 函数的 Dockerfile 示例。查看底部的参考资料部分，获取`handler.py`和`client.properties`文件。

```
# Lambda base image
FROM public.ecr.aws/lambda/python:3.8
# Install Kafka prereqs
RUN yum -y install java-11 wget tar
RUN wget https://archive.apache.org/dist/kafka/2.8.1/kafka_2.12-2.8.1.tgz
RUN tar -xzf kafka_2.12-2.8.1.tgz
RUN wget https://github.com/aws/aws-msk-iam-auth/releases/download/v1.1.1/aws-msk-iam-auth-1.1.1-all.jar
RUN mv aws-msk-iam-auth-1.1.1-all.jar ${LAMBDA_TASK_ROOT}/kafka_2.12-2.8.1/libs
COPY ./client.properties ${LAMBDA_TASK_ROOT}
# Remove tgz
RUN rm kafka_2.12-2.8.1.tgz
# Lambda code
COPY handler.py ${LAMBDA_TASK_ROOT}
# Run handler
CMD ["handler.action"]
```

按照这里的指示将你的图片推送到[亚马逊弹性容器注册处](https://aws.amazon.com/ecr/) (ECR)。一旦你的图像在 ECR 中，你可以使用容器图像创建一个 [Lambda 函数。创建函数后，我们需要更新一些设置。](https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-images.html)

### **配置 Lambda 功能**

最后，我们需要配置 Lambda 函数，以便它可以与集群交互。对于基本设置，我们需要将内存增加到 1024 MB，超时时间增加到 1 分钟，并使用我们上面创建的 IAM 角色。

![image.png](img/e50ecc0b2cdf57ac21c7e8efd32dcf70.png)

接下来，我们需要确保 Lambda 函数与 MSK 集群具有相同的 VPC、子网和安全组。

![image.png](img/5fc953e740cecde630162620f2439f7a.png)

最后，我们需要从“查看客户端信息”按钮添加设置为 MSK 集群端点的`KAFKA_ENDPOINT`环境变量。

![image.png](img/b3c1b64718ccd8c6e3988019f7103a7d.png)

这样，我们就可以开始生产和消费数据了。

## **生产和消费数据**

使用 Lambda，我们可以通过控制台中的“test”选项卡发送测试事件，以验证我们的容器映像正在工作。为了测试 produce 函数，我们可以将这个简单的有效载荷发送到`my_topic`。

```
{
 "action": "produce",
 "topic": "my_topic",
}
```

生产者代码只是使用样本数据，通过传入的参数调用生产者脚本。

```
./kafka_2.12-2.8.1/bin/kafka-console-producer.sh 
--topic {topic}
--bootstrap-server {KAFKA_ENDPOINT}
--producer.config client.properties < /tmp/test.json
```

一旦代码运行了来自 MSK 集群的指标，将需要几分钟来更新和指示数据已收到。可以从集群主页上的指标选项卡中查看指标。

![image.png](img/e741d148a7140c17cdfc1de4efb0f013.png)

然后，我们还可以通过更新有效负载来测试消费者代码。

```
{
 "action": "consume",
 "topic": "my_topic",
}
```

类似地，消费者代码使用传入的参数调用消费者脚本，并将输出写入示例文件。根据您的使用情况，可以将文件上传到 S3，或者对数据运行其他功能。超时参数用于确保脚本关闭，否则它会一直等待输入。

```
"./kafka_2.12-2.8.1/bin/kafka-console-consumer.sh
--topic {topic} --from-beginning
--bootstrap-server {KAFKA_ENDPOINT}
--consumer.config client.properties --timeout-ms 12000 > /tmp/output.json"
```

所有的代码都是可配置的，以适应您的用例，所以请随意使用它作为入门指南，并根据需要进行调整。

## 结论

在本帖中，我们讨论了如何通过以下方式成功设置开始扩展无服务器 Kafka 管道所需的基础设施:

*   启动无服务器 MSK 集群
*   创建 Kafka 客户端 Docker 映像
*   部署基于容器的 Lambda 函数
*   通过 Lambda 控制台生成和消费数据

这个解决方案可以扩展以适应不同的用例，比如使用 Eventbridge 定期从数据库中读取数据，或者将处理过的消息上传到 S3。Lambda 的灵活性与 Kafka 将数据处理从源和目标解耦的能力相结合，为无服务器数据管道提供了基础。

*在 Twitter 上关注 Banjo，点击* [*，@banjtheman*](https://twitter.com/banjtheman) *和* [*，@AWSDevelopers*](https://twitter.com/awsdevelopers) *了解更多关于云计算和 AWS 的有用提示和技巧。*

### 关于作者

Banjo 是 AWS 的一名高级开发人员，他在那里帮助开发人员对使用 AWS 感到兴奋。Banjo 热衷于将数据操作化，并围绕利用数据启动了一个播客、一个 meetup 和开源项目。当没有建造下一个大东西时，班卓喜欢通过玩视频游戏特别是 JRPGs 和探索他周围发生的事件来放松

## 资源

**客户端属性**

```
security.protocol=SASL_SSL
sasl.mechanism=AWS_MSK_IAM
sasl.jaas.config=software.amazon.msk.auth.iam.IAMLoginModule required;
sasl.client.callback.handler.class=software.amazon.msk.auth.iam.IAMClientCallbackHandler
```

**handle . py**

这段代码为 Lambda 提供了一个模板，用于与无服务器 Kafka 集群进行交互。由于基于 IAM 的认证，标准的 Kafka Python 库不能与集群交互，所以我开发了一个 Java 脚本包装器来与集群交互。

```
import json
import logging
import os
import subprocess
from typing import List, Dict, Any

KAFKA_ENDPOINT = os.environ["KAFKA_ENDPOINT"]

def action(event, context) -> Dict[str, Any]:
   """
   Purpose:
       Entrypoint for action on cluster
   Args:
       event - data from lambda
       context - context data from lambda
   Returns:
       response - JSON response
   """

   body = {
       "message": "Running Action",
       "input": event,
   }

   curr_action = event["action"]
   topic = event["topic"]

   # If creating topic, can specify number of partitions
   if "num_partitions" in event:
       num_partitions = event["num_partitions"]
   else:
       num_partitions = 1

   if curr_action == "produce":
       response = produce(topic, num_partitions)
   elif curr_action == "consume":
       response = consume(topic)
   else:
       raise ValueError("Invalid action")

   return response

def consume(topic: str) -> Dict[str, Any]:
   """
   Purpose:
       Consume data in a topic
   Args:
       topic - topic to consume on
   Returns:
       response - JSON response
   """
   body = {
       "message": "Data consumed!!!",
   }

   # TODO can play with the timeout, on how long you want to collect data
   # TODO can also configure if you want to get data from the beginning or not
   cmd = f"./kafka_2.12-2.8.1/bin/kafka-console-consumer.sh --topic {topic} --from-beginning --bootstrap-server {KAFKA_ENDPOINT} --consumer.config client.properties --timeout-ms 12000 > /tmp/output.json"

   os.system(cmd)

   # TODO
   # Do what you need to do with output.json i.e upload to s3, run analytics, etc..

   response = {"statusCode": 200, "body": json.dumps(body)}
   logging.info(response)

   return response

def produce(topic: str, num_partitions: int) -> Dict[str, Any]:
   """
   Purpose:
       Produce data in a topic
   Args:
       topic - topic to create
       num_partitions - number of num_partitions to use
   Returns:
       response - JSON response
   """
   # TODO would input your process to get data to send to topic
   sample_data = '{"user":"Alice","number":105,"timestampInEpoch":1650880895}\n{"user":"Bob","number":5,"timestampInEpoch":1650880324}'

   # Write sample output to temp file
   write_to_file("/tmp/test.json", sample_data)

   body = {
       "message": "Data produced!!!",
       "input": sample_data,
   }

   # Check if topic exists, if not create it
   topics = list_topics()
   if not topic in topics:
       if not create_topic(topic, num_partitions):
           raise RuntimeError("Topic not created")

   produce_topic_command = f"./kafka_2.12-2.8.1/bin/kafka-console-producer.sh  --topic {topic} --bootstrap-server {KAFKA_ENDPOINT} --producer.config client.properties < /tmp/test.json"

   os.system(produce_topic_command)

   response = {"statusCode": 200, "body": json.dumps(body)}
   logging.info(response)

   return response

def create_topic(topic:str, num_partitions:int) -> bool:
   """
   Purpose:
       Create topic in cluster
   Args:
       topic - topic to create
       num_partitions - number of num_partitions to use
   Returns:
       bool - True if created, false if not
   """

   cmd = f"./kafka_2.12-2.8.1/bin/kafka-topics.sh --bootstrap-server {KAFKA_ENDPOINT} --command-config client.properties --create --topic {topic} --partitions {num_partitions}"

   output = subprocess.check_output(cmd, shell=True)
   output_string = output.decode("utf-8")
   outputs = output_string.split("\n")

   # Check if created
   success_string = f"Created topic {topic}."
   if success_string in outputs:
       logging.info(outputs)
       return True
   else:
       logging.error(outputs)
       return False

def list_topics() -> List[str]:
   """
   Purpose:
       List topics in cluster
   Args:
       N/A
   Returns:
       topics - list of topics
   """
   cmd = f"./kafka_2.12-2.8.1/bin/kafka-topics.sh --list --bootstrap-server {KAFKA_ENDPOINT} --command-config client.properties"

   # Run the command to get list of topics
   output = subprocess.check_output(cmd, shell=True)
   output_string = output.decode("utf-8")
   topics = output_string.split("\n")  # turn output to array

   return topics

def test_produce_consume() -> None:
   """
   Purpose:
       Test producing and consuming
   Args:
       N/A
   Returns:
       N/A
   """
   logging.info("testing produce")
   response = produce("my_topic", 1)
   logging.info(response)
   logging.info("testing consume")
   consume("my_topic")
   logging.info("Done and Done")

def write_to_file(file_path: str, file_text: str) -> bool:
   """
   Purpose:
       Write text from a file
   Args/Requests:
        file_path: file path
        file_text: Text of file
   Return:
       Status: True if written, False if failed
   """

   try:
       with open(file_path, "w") as myfile:
           myfile.write(file_text)
           return True

   except Exception as error:
       logging.error(error)
       return False

if __name__ == "__main__":
   loglevel = logging.INFO
   logging.basicConfig(format="%(levelname)s: %(message)s", level=loglevel)
   test_produce_consume()
```