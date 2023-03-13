# 如何使用 Amazon event bridge API Destinations 将您的工作负载与 Slack 相集成

> 原文：<https://acloudguru.com/blog/engineering/how-to-integrate-your-workload-with-slack-using-amazon-eventbridge-api-destinations>

API 使您的应用程序能够发出请求、传递数据和使用第三方服务的功能。随着在 [Amazon EventBridge](https://aws.amazon.com/eventbridge/) 中 API 目的地的推出，您现在可以直接从 AWS 中的事件调用外部 API。这使得将您的应用程序与软件即服务(SaaS)提供商(如 [Zendesk](https://www.zendesk.com/) 或 [PagerDuty](https://www.pagerduty.com/) )集成更加容易，或者将数据发送到任何公开 REST API 端点的服务。

当系统状态发生变化或您的工作负载发生变化时，就会发生事件。它可能是存储在 [S3](https://acloudguru.com/course/s3-masterclass) 中的新对象，来自控制台的新登录，或者是在您的电子商务应用程序中处理的支付。事件是一个 JSON 结构，它包含了所发生事件的细节，并且有许多事件是由 AWS 服务自动生成的。

对于[无服务器](https://acloudguru.com/course/serverless-concepts)开发人员来说，API Destinations 使得构建微服务变得更加简单，这些微服务可以响应工作负载内部或 AWS 服务生成的事件。这种集成取代了定制代码，有助于管理机密和 API 密钥，并自动处理下游请求的排队和节流。

通过将 AWS 事件与外部服务相连接，您可以:

*   当审批工作流在 [AWS 步骤功能](https://aws.amazon.com/step-functions/)中完成时，通过 Stripe 发放信用卡退款。
*   自动打开 GitHub 问题以响应 [AWS CodeStar](https://aws.amazon.com/codestar/) 中的构建失败。
*   当 Amazon DynamoDB 表中的数据发生变化时，在 Contentful 中创建新的产品页面。

在这篇博文中，我将展示如何与 Slack 进行集成。这会导致基于您的 AWS 帐户中的事件的消息发布到 Slack 通道。

这个示例使用 [AWS 无服务器应用程序模型](https://aws.amazon.com/serverless/sam/) (AWS SAM)将解决方案部署到您的 AWS 帐户。您可以使用这里介绍的代码来构建与服务的类似集成，如 [GitHub](https://github.com/) 、 [Str](https://stripe.com/) [i](https://stripe.com/) [pe](https://stripe.com/) 和 [Contentful](https://www.contentful.com/) 。

## 概观

在示例应用程序中，您为 Slack 配置 API 目的地，并配置 EventBridge 规则来路由特定事件。架构看起来是这样的:

1.  AWS 服务和自定义应用程序生成事件。这些都用 JSON 表示。
2.  一个 [Amazon EventBridge](https://aws.amazon.com/eventbridge/) 事件总线接收事件。
3.  规则评估事件是否匹配指定的模式。这些模式也用 JSON 表示，可以匹配传入事件的属性。匹配 *Slack* 规则的事件被转发到 API Destinations 目标。
4.  [API 目的地](https://docs.aws.amazon.com/eventbridge/latest/APIReference/API_ApiDestination.html)配置使用一个包含授权秘密的[连接](https://docs.aws.amazon.com/eventbridge/latest/APIReference/API_Connection.html)和一个 API。API 包含目标 URL、http 方法和其他配置信息。
5.  外部 API 接收事件。这个例子使用 Slack，但是目标 URL 可以是任何 REST API 或 webhook。

要开始，你需要安装 [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) 和 [AWS SAM](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install.html) 。你还需要[一个备用账户](https://slack.com/get-started)，但这里显示的一切都可以使用免费账户完成。

## API 目的地功能如何工作

EventBridge 规则将匹配的消息路由到目标，API 目的地是一种目标。它由包含认证信息的*连接*和 *API* 配置组成。连接中提供的凭证安全地存储在 [AWS 秘密管理器](https://aws.amazon.com/secrets-manager/)中。一个连接代表一个目标服务，一个连接可以被多个 API 和规则使用。

虽然您可以使用 Lambda 函数调用外部 REST API，但是 API Destinations 提供了额外的管理和配置选项，否则您将使用自定义代码编写这些选项。您可以配置一个每秒*调用速率*，这可以保护 API 免受突发流量高峰的影响，并有助于减少繁忙系统中的调用数量。

在内部，EventBridge 使用一个队列来保存超过此速率的请求。它可以缓冲这些消息长达 24 小时。API 目标的最大超时是 5 秒，服务将重试任何超过此超时的调用。

* * *

[**自动化 AWS 成本优化**](https://go.acloudguru.com/AWS-Cost-Optimization-Webinar)
AWS 为您的企业提供了前所未有的价值，但经济高效地使用它可能是一项挑战。在这个[免费点播的网络研讨会](https://go.acloudguru.com/AWS-Cost-Optimization-Webinar)中，您将了解 AWS 成本优化工具和策略的概况。

* * *

## 测试 API 目的地功能

Webhook.site 是一个有用的调试工具，可以回应任何传入的请求，帮助查看 API 调用中发送了什么。在创建 Slack 集成之前，首先部署一个 EventBridge 规则，该规则带有一个路由到 Webhook.site 的 API 目的地。

要部署此解决方案:

1.  导航到[https://webhook.site/](https://webhook.site/)并复制唯一的 webhook URL。

2.  克隆代码回购:
    `git clone https://github.com/aws-samples/serverless-patterns`

3.  更改目录:
    `cd ./eventbridge-api-destinations/1-webhook-site`

4.  部署 AWS SAM 模板:
    `sam deploy --guided`

5.  当提示输入 *MyWebhookURL* 时，输入步骤 1 中的 URL。

要测试应用程序:

1.  将目录改为主代码库:
    `cd ..`

2.  向 EventBridge 发送测试事件:
    `aws events put-events --entries file://testEvent.json`

3.  API 调用到达 Webhook.site，在这里您可以看到有效负载和头:

这个示例应用程序将整个事件负载传递给 API 端点。testEvent.json 中的测试事件出现在 Webhook.site 的*原始内容*字段中。

## 了解 AWS SAM 模板

该模板部署多个 AWS 资源。首先，它创建了一个新的事件总线:

```
 MyEventBus:
    Type: AWS::Events::EventBus
    Properties:
      Name: "MyEventBus" 
```

API 目的地由一个连接和一个 API 组成。由于这是一个开放的 API，所以授权被定义为 API_KEY，并由 Webhook.site 注销:

```
 MyConnection:
    Type: AWS::Events::Connection
    Properties:
      AuthorizationType: API_KEY
      Description: 'My connection with an API key'
      AuthParameters:
        ApiKeyAuthParameters:
          ApiKeyName: MyWebhook
          ApiKeyValue: MyAPIkey 
```

API 将调用端点设置为在部署期间作为参数提供的 URL。它将 HTTP 方法配置为 *POST* ，并将消息限制为每秒 10 条:

```
MyApiDestination:
    Type: AWS::Events::ApiDestination
    Properties:
      Name: 'MyWebhookTest'
      ConnectionArn: !GetAtt MyConnection.Arn
      InvocationEndpoint: !Ref MyWebhookURL
      HttpMethod: POST
      InvocationRateLimitPerSecond: 10 
```

最后，模板定义了一个规则，该规则确定一个事件模式，然后将目标设置为新的 API 目的地:

```
 EventRule: 
    Type: AWS::Events::Rule
    Properties: 
      Description: "EventRule"
      State: "ENABLED"
      EventBusName: !Ref MyEventBus
      EventPattern: 
        source:
          - "MyTestApp"
        detail-type:
          - "MyTestMessage"       
      Targets: 
        - Arn: !GetAtt MyApiDestination.Arn
          RoleArn: !GetAtt EventBridgeTargetRole.Arn
          Id: "MyAPIdestination" 
```

EventBridge 服务也需要调用 API 目的地的权限，因此 [IAM 角色](https://github.com/aws-samples/serverless-patterns/blob/main/eventbridge-api-destinations/1-webhook-site/template.yaml)授予了这种访问权限。

* * *

[**获得痛苦的云词典**](https://get.acloudguru.com/cloud-dictionary-of-pain)
说云不一定要努力。我们分析了数以百万计的回复，找出了最容易让人犯错的概念。抓住这个[云指南](https://get.acloudguru.com/cloud-dictionary-of-pain)获取一些最痛苦的云术语的简洁定义。

* * *

## 将 Slack 设置为 API 目标

首先，您必须配置对 Slack 帐户的 bot 访问。为此，请按照 [*中的说明为您的工作区*](https://slack.com/help/articles/115005265703-Create-a-bot-for-your-workspace) 创建一个 bot，并记下 bot 的令牌(该代码以 *xoxb* 开头)和通道 ID。您需要这两个值来部署此解决方案。

API 目的地支持三种不同类型的授权:基本用户名和密码、OAuth 和 API 密钥。Slack bot 使用 OAuth 方法，在 Authorization 头中作为载体令牌传递。这个令牌随每个 API 请求一起传递，使 Slack 能够验证发送者。

要部署松弛示例，请执行以下操作:

1.  从终端，改变目录:
    `cd ../2-slack`

2.  部署 AWS SAM 模板:
    `sam deploy --guided`

3.  系统会提示您输入三个参数:
    1.  MySlackToken:从 Slack 配置中输入 bot 令牌(这个从 *xoxb* 开始)。
    1.  MySlackChannel:输入 Slack 中的频道 ID。
    1.  MyEventBusName:接受默认值 *MyEventBus* ，因为该模板使用第一个示例中部署的相同事件总线。

要测试松弛集成，请执行以下操作:

1.  将目录改为主代码库:
    `cd ..`

2.  向 EventBridge 发送测试事件:
    `aws events put-events --entries file://testEvent.json`

3.  该消息出现在松弛频道中:

## 了解 AWS SAM 模板

这个模板中使用的*连接*资源配置一个在 API 请求的授权头中传递的令牌。它在松弛令牌前添加“承载”关键字:

```
 Type: AWS::Events::Connection
    Properties:
      AuthorizationType: API_KEY
      Description: 'My connection with an API key'
      AuthParameters:
        ApiKeyAuthParameters:
          ApiKeyName: 'Authorization'
          ApiKeyValue: !Sub 'Bearer ${MySlackToken}' 
```

API 配置使用 Slack 的 *Post Message* API，并将调用速率限制为每秒 10 条消息:

```
 MyApiDestination:
    Type: AWS::Events::ApiDestination
    Properties:
      Name: 'MySlackNotifier'
      ConnectionArn: !GetAtt MyConnection.Arn
      InvocationEndpoint: 'https://slack.com/api/chat.postMessage'
      HttpMethod: POST
      InvocationRateLimitPerSecond: 10 
```

该规则使用与前面定义的相同的事件模式，过滤源为 *MyTestApp* 和细节类型为 *MyTestMessage* 的所有事件:

```
 EventRule: 
    Type: AWS::Events::Rule
    Properties: 
      Description: "EventRule"
      State: "ENABLED"
      EventBusName: !Ref MyEventBusName
      EventPattern: 
        source:
          - "MyTestApp"
        detail-type:
          - "MyTestMessage"       
      Targets: 
        - Arn: !GetAtt MyApiDestination.Arn
          RoleArn: !GetAtt EventBridgeTargetRole.Arn
          Id: "MyAPIdestination"
          InputTransformer:
            InputPathsMap:
              text: $.detail.event
            InputTemplate: !Sub >
              {
                "channel": "${MySlackChannel}",
                "text": <text>
              } 
```

在第一个示例中，整个事件负载被传递给目标。然而，Slack 需要特定的 JSON 属性，所以它使用一个[输入转换器](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-transforming-target-input.html)从有效负载中提取这些属性。[输入路径映射](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-events-rule-inputtransformer.html)部分定义了有效载荷的变量，而[输入模板](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-events-rule-inputtransformer.html)嵌入了 AWS SAM 参数和输入路径变量。结果是您可以配置一个有效负载来匹配 API 的特定需求。

## 结论

使用 API 目的地，您可以使用 EventBridge 调用第三方 API，而无需编写任何业务逻辑。该服务提供可配置的节流和安全的密钥管理，同时为超过此限制的消息缓冲长达 24 小时的消息。

通过过滤由 AWS 服务或定制应用程序生成的事件，您可以使用这种集成来扩展工作负载的功能。API Destinations 构建于现有的 EventBridge 功能之上，引入了*连接*和 *API* 资源来帮助配置凭证和定义 API 端点。

在这些例子中，您将消息发送到 webhook 调试服务和 Slack。使用所示的方法，您可以修改模板和有效负载格式来过滤不同的事件，并与几乎任何外部 REST API 端点集成。

要部署这些模式和其他模式，请参阅无服务器世界中新的[无服务器模式集合](https://serverlessland.com/patterns)。想了解更多无服务器提示和技巧吗？查看我们的 [6 款最受欢迎的工具，让无服务器过渡](https://acloudguru.com/blog/engineering/6-things-i-wish-i-had-known-before-going-serverless)变得轻而易举！

* * *

## 获得更好职业所需的技能。

掌握现代技术技能，获得认证，提升您的职业生涯。无论您是新手还是经验丰富的专业人士，您都可以通过实践来学习，并在 ACG 的帮助下推进您的云计算职业生涯。