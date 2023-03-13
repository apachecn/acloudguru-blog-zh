# 如何在云专家 Azure |上运行无服务器 PHP

> 原文：<https://acloudguru.com/blog/engineering/how-to-run-serverless-php-on-azure>

随着 [Azure Functions 自定义处理程序](https://docs.microsoft.com/azure/azure-functions/functions-custom-handlers?WT.mc_id=data-10498-alvidela)的到来，你现在可以在 Azure 上运行 PHP 无服务器应用。在本文中，您将看到如何通过让您的 PHP 项目读取 Azure 函数来利用这一新功能。

#### 入门指南

## 无服务器应用程序的结构

Azure 无服务器应用具有以下文件夹结构:

```
├── HttpTrigger
│   ├── function.json
│   └── index.php
├── QueueTrigger
│   ├── function.json
│   └── index.php
├── deploy.sh
├── host.json
├── local.settings.json
```

每一个无服务器功能都存在于类似于`HttpTrigger`和`QueueTrigger`的文件夹中。在这些文件夹中，你将有两个文件`function.json`和`index.php`。

在`functions.json`中，您将指定函数如何被触发，它接收什么参数，以及它返回什么，而`index.php`是包含您的函数逻辑的文件。要了解更多关于 Azure Functions 无服务器应用的结构，请看本指南: [Azure Functions 开发者指南](https://docs.microsoft.com/azure/azure-functions/functions-reference?WT.mc_id=data-10498-alvidela)

对于 PHP，这是我们感兴趣的，你需要在你的函数文件夹中有一个`index.php`文件，就像上面的`HttpTrigger`例子一样。您的 PHP 代码必须遵循这些约定:

```
<?php
use Azserverless\Context\FunctionContext;

function run(FunctionContext $context) {
    $req = $context->inputs['req'];

    $context->log->info('Http trigger invoked');

    $query = $req['Query'];

    if (array_key_exists('name', $query)) {
        $name = $query['name'];
        $message = 'Hello ' . $query['name'] . '!';
    } else {
        $name = 'EMPTY';
        $message = 'Please pass a name in the query string';
    }

    $context->outputs['outputQueueItem'] = json_encode($name);
    $context->log->info(sprintf('Adding queue item: %s', $name));

    return [
        'body' => $message,
        'headers' => [
            'Content-type' => 'text/plain'
        ]
    ];
}
?>
```

您需要一个名为`run`的函数，它接受一个`FunctionContext`参数，该参数将包含您的函数接收到的输入，以及其他实用程序，如[独白记录器](https://github.com/Seldaek/monolog)。您还可以在`$context`参数中设置`outputs`，就像代码对`outputQueueItem`所做的那样，添加一个值，该值将在这种特定情况下被转发到一个队列中。

那么，这个`FunctionContext`是从哪里来的呢？它来自专门为 Azure PHP 开发的新的 [Azserverless](https://github.com/videlalvaro/azserverless) 库。

转到您的项目根文件夹，并在您的`composer.json`中添加以下依赖项:

```
"require": {
    "videlalvaro/azserverless": "*"
}
```

如果您没有安装 composer，请遵循此处的说明[。](https://getcomposer.org/doc/00-intro.md)

然后在命令行上运行`composer.phar install`，这将获得所有需要的依赖项。

## 为 PHP 配置 Azure 函数

现在是时候告诉 Azure 函数如何运行你的 PHP 项目了。打开`host.json`。在该文件中，您应该添加一个顶级条目，指定该项目使用自定义处理程序运行:

```
 "customHandler": {
      "description": {
      "defaultExecutablePath": "php",
      "arguments": [
        "-S",
        "0.0.0.0:%FUNCTIONS_CUSTOMHANDLER_PORT%",
        "vendor/videlalvaro/azserverless/bin/serverless.php"
      ]
    },
    "enableForwardingHttpRequest": false
  },
```

我们告诉 Azure 函数如何执行 PHP，提供将请求转发给函数处理程序的`vendor/videlalvaro/azserverless/bin/serverless.php`文件的路径。

最后，我们需要告诉 azure 我们的应用程序将在`PHP 7.4`上运行。打开命令行，使用以下参数调用 [Azure CLI](https://acloudguru.com/course/azure-cli-essentials) :

```
az webapp config set --name your_app_name --resource-group your_resource_group --php-version 7.4
```

## 最后润色

在部署之前，确保配置您的`local.settings.json`文件，包括`"FUNCTIONS_WORKER_RUNTIME": "custom"`配置键/值和您的`AzureWebJobsStorage`连接字符串:

```
{
  "IsEncrypted": false,
  "Values": {
    "FUNCTIONS_WORKER_RUNTIME": "custom",
    "AzureWebJobsStorage": "DefaultEndpointsProtocol=https;AccountName=<accountname>;AccountKey=<accountkey>;EndpointSuffix=<endpointsuffix>"
  }
}
```

最后，确保添加指南[为 Azure 应用服务](https://docs.microsoft.com/azure/app-service/configure-language-php?pivots=platform-windows&WT.mc_id=data-10498-alvidela#run-composer)配置 PHP 应用中指定的 Kudu 脚本，以便`composer`在每次部署应用时运行，保持您的依赖关系最新。

就是这样！您应该准备好通过使用新的自定义处理程序特性将您的 PHP 应用程序部署到 Azure 功能中。

## 了解更多信息

如果您想了解更多关于本文所涉及的主题，请务必访问以下网站:

黑客快乐！

##### 关于作者

阿尔瓦罗·维德拉是微软的一名开发者拥护者，他组织了 DuraznoConf。他是 RabbitMQ in Action 的合著者，并为计算机器协会撰写文章。你可以在推特上找到他的名字是 [@old_sound](https://twitter.com/old_sound?opt_id=oeu1596472260634r0.19676524222612213) 。