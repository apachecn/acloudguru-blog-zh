# 用 AWS Amplify 和 Flask 创建一个无服务器的 Python API

> 原文：<https://acloudguru.com/blog/engineering/create-a-serverless-python-api-with-aws-amplify-and-flask>

Flask 是我最喜欢的创建快速 API 的工具之一。Python 仍然是我最喜欢的编程语言，尽管过去几年主要使用 JavaScript 语法对我来说简单而优雅，像 Pandas 这样的 Python 库的能力令人难以置信。

部署 Python 应用程序并不总是最有趣的活动，所以我们还将使用 AWS Lambda 来使我们的应用程序[无服务器](https://aws.amazon.com/serverless/)。另外，我们将使用 AWS Amplify 的命令行界面来创建和管理我们的资源。

我们还需要一个数据库来存储我们的数据，在这种情况下，我们将为布兰妮的歌曲构建一个 API，并使用 [DynamoDB](https://aws.amazon.com/dynamodb/) 来存储我们的数据。

本教程对于已经掌握了关于 AWS Amplify、API 如何工作以及 Python 的基础知识的人来说是最有帮助的。

让我们深入研究代码！

项目设置

首先，我们将初始化一个 Amplify 项目。你需要安装和配置[Amplify CLI](https://docs.amplify.aws/cli/start/install)和[节点](https://nodejs.org/en/download/)。我将从 React 应用程序开始，但我们将专注于教程的后端，所以如果你不是 React 开发人员，你应该没问题！

## 在您的终端中运行下面的命令来创建一个 React 样板文件，更改为它，然后初始化 Amplify。

初始化 Amplify 会提示你一些问题。对于所有这些，您只需按 enter 键就可以选择默认值！

添加数据库

```
$ npx create-react-app britney-spears-api
$ cd britney-spears-api
$ amplify init
```

接下来，我们需要向我们的项目添加一个 DynamoDB 数据库。在您的 CLI 中运行`amplify add storage`。这会问你一些关于你的数据的问题。

```
? Enter a name for the project britneyspearsapi
? Enter a name for the environment dev
? choose your default editor: Visual Studio Code
? Choose the type of app that you\'re building javascript
? What javascript framework are you using react
? Source Directory Path: src
? Distribution Directory Path build
? Build Command: npm run-script build
? Start Command: npm run-script start
? Do you want to use an AWS profile? yes
? Please choose the profile you want to use `your-profile`
```

## 现在，运行`amplify push -y`在 AWS 上部署您的数据库！

创建 API

```
? Please select from one of the below mentioned services: NoSQL Database
? Please provide a friendly name for your resource that will be used to label this category in the project: britneySongStorage
? Please provide table name: britneySongs

? What would you like to name this column: id
? Please choose the data type: string
? Would you like to add another column: Yes
? What would you like to name this column: name
? Please choose the data type: string
? Would you like to add another column: Yes
? What would you like to name this column: year
? Please choose the data type: number
? Would you like to add another column: Yes
? What would you like to name this column: link
? Please choose the data type: string
? Would you like to add another column: No

? Please choose partition key for the table: id
? Do you want to add a sort key to your table? N

? Do you want to add global secondary indexes to your table? No
? Do you want to add a Lambda Trigger for your Table? No
```

现在，让我们添加一个 API！我们将为所有 CRUD 操作创建路径，并允许数据库交互。

## 我们将使用 Amplify CLI 添加一个 API:`amplify add api`。

系统会提示您回答一些问题。首先，命名您的 API，然后为您的路由提供一个基本路径。

然后，系统会提示我们创建一个新的 AWS Lambda 函数，并将其命名为。我们将使用 Python 语言。

我们还需要配置一些高级设置，以便访问我们的数据库。使用空格键选择存储和所有 CRUD 操作。

```
? Please select from one of the below mentioned services: REST
? Provide a friendly name for your resource to be used as a label for this category in the project: britneySongApi
? Provide a path (e.g., /book/{isbn}): /song
```

然后，您可以对接下来的几个问题回答“否”，尽管我会选择“是”来编辑您的本地 Lambda 函数。它会打开你的文本编辑器找到你想要的文件！

```
? Choose a Lambda source Create a new Lambda function
? Provide an AWS Lambda function name: britneyspearsapi
? Choose the runtime that you want to use: Python
```

创建一个 API 将启用 [Amazon API 网关](https://aws.amazon.com/api-gateway/)，它将处理 HTTP 请求到我们 Lambda 函数的路由。

```
? Do you want to configure advanced settings? Yes
? Do you want to access other resources in this project from your Lambda function? Yes
? Select the categories you want this function to have access to. storage
? Select the operations you want to permit on britneySongStorage create, read, update, delete
```

最后，运行 amplify push 将您的服务部署到云中。`-y`标志将跳过确认步骤。

```
? Do you want to invoke this function on a recurring schedule? No
? Do you want to configure Lambda layers for this function? No
? Do you want to edit the local lambda function now? Yes
? Restrict API access No
? Do you want to add another path? No
```

**注意:每当您想要部署对 API 的更改时，您都需要重新运行这个 push 命令。**

Python 函数

```
$ amplify push -y
```

首先，转到您的函数的目录:

## 您需要为 Python 打包安装 [pipenv](https://pypi.org/project/pipenv/) 。然后，我们将安装必要的软件包。

`aws-wsgi`将允许我们使用烧瓶路由

```
cd amplify/backend/function/britneyspearsapi 
```

在 Python 中支持与 AWS 服务的交互，我们将在 DynamoDB 中使用它

*   是我们的网络框架
*   将为我们的 flask 应用程序处理 CORS
*   然后，打开你的 Lambda 函数的代码——它是在`amplify add api`步骤中为你打开的，但是如果你关闭了它，在你的函数文件夹中打开`src/index.py`。
*   在你的文件中会有一个生成的“Hello World”Lambda 函数，你可以删除它。

```
$ pipenv install aws-wsgi boto3 flask flask-cors
```

首先，我们需要初始化 Flask 应用程序。我们还将使用`flask-cors`来处理 CORS。

在这段代码下面，添加一个 Lambda 处理程序—这个函数将处理我们的请求事件。API Gateway 专门寻找一个名为`handler`的函数，所以一定要这样称呼它！

我们还将使用 [`awsgi`](https://github.com/slank/awsgi) 来使用带有 API 网关的 WSGI 中间件。

```
from flask_cors import CORS
from flask import Flask, jsonify, request

app = Flask(__name__)
CORS(app)
```

导入`awsgi`:

然后添加`handler`功能:

在`handler`上面，我们来添加我们的第一条路线！在上面的`amplify add api`步骤中，我们已经为我们的 API 创建了一个基本路径。我将把这个路由保存到一个变量中，这样我就可以用它作为我所有 URL 的前缀。然后，我将为我的 Flask 应用程序添加一个路由，处理那个`/songs/` url 并接受 GET 请求。现在，我将发送一个“hello world”消息。

```
+ import awsgi
from flask_cors import CORS
from flask import Flask, jsonify, request
```

运行`amplify push -y`以部署您的更改。

```
def handler(event, context):
    return awsgi.response(app, event, context)
```

要在前端使用这个路径，首先我要安装`aws-amplify`。在你的前端的根目录而不是你的 Python 函数的根目录中这样做。

```
# Constant variable with path prefix
BASE_ROUTE = "/song"

@app.route(BASE_ROUTE, methods=['GET'])
def list_songs():
    return jsonify(message="hello world")
```

然后，配置放大器。如果你在一个`create-react-app`生成的项目中，把它放在`index.js`文件中。

然后，添加 API 调用。我们将使用`aws-amplify`的`API.get`向我们的 API 发出 GET 请求。第一个参数是我们创建的 API 的名称，第二个参数是我们想要请求的路由。

```
$ npm i aws-amplify
```

添加创建路线

```
import { Amplify } from 'aws-amplify'
import config from './aws-exports'

Amplify.configure(config)
```

现在，让我们制作一条将在我们的数据库中创建一首新歌的路线。我将导入`boto3`、`uuid`和`os`，然后创建一个到数据库的新连接。我们还将从 Amplify 为我们创建的环境变量中获得 DynamoDB 表的名称。这些在`amplify add api`步骤的输出中列出。

```
import { API } from 'aws-amplify'

const getData = async () => {
  const data = await API.get('britneySongApi', '/song')
  console.log(data)
}
```

## 现在，我们将创建我们的路线。这个仍然位于`/song` url，但是这次它将处理一个 POST 请求。我们将获取请求对象，将其转换为 json，然后创建项目。我们将提供表的名称和该项目的数据。我们将使用 Python 的`uuid4`函数随机生成`id`。然后，我们将返回一条消息，表明该项已被创建。

现在，在前端，我们将发出创建新歌的 POST 请求！

```
import awsgi
+ import boto3
+ import os

from flask_cors import CORS
from flask import Flask, jsonify, request
+ from uuid import uuid4

+ client = boto3.client("dynamodb")
+ TABLE = os.environ.get("STORAGE_BRITNEYSONGSTORAGE_NAME")
BASE_ROUTE = "/song"
```

添加列表路由

```
 @app.route(BASE_ROUTE, methods=['POST'])
def create_song():
    request_json = request.get_json()
    client.put_item(TableName=TABLE, Item={
        'id': { 'S': str(uuid4()) },
        'name': {'S': request_json.get("name")},
        'year': {'S': request_json.get("year")},
        'link': {'S': request_json.get("link")},
    })
    return jsonify(message="item created")
```

让我们更新我们的 list route 来返回数据库中所有歌曲的列表。将`list_items`功能的返回改为表格扫描。

```
const data = await API.post('britneySongApi', '/song', { 
  body: { 
    name: 'Toxic', 
    year: '2003', 
    link: 'https://www.youtube.com/watch?v=LOZuxwVk7TU' 
  } 
})
console.log(data)
```

## 然后在前端，你可以提出这个请求来查看所有的歌曲！

添加获取路线

```
@app.route(BASE_ROUTE, methods=['GET'])
def list_songs():
+    return jsonify(data=client.scan(TableName=TABLE))
```

现在，我们将添加一个函数，它根据歌曲的`id`获取一首歌曲。我们将创建一个路由来处理对`/song/<song_id>`的 GET 请求。然后，我们将在数据库中查询具有该 id 的歌曲！

```
const data = await API.get('britneySongApi', '/song')
console.log(data)
```

## 添加编辑路线

现在，我们需要添加一个路由来编辑一个项目。这将处理对`/song/<song_id>`的`PUT`请求。这个`Key`将是我们想要更新的歌曲的`id`。 [`UpdateExpression`](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Expressions.UpdateExpressions.html) 将允许我们修改歌曲的所有属性。然后，`ExpressionAttributeNames`提供键名，`ExpressionAttributeValues`提供值。

```
@app.route(BASE_ROUTE + '/<song_id>', methods=['GET'])
def get_song(song_id):
    item = client.get_item(TableName=TABLE, Key={
        'id': {
            'S': song_id
        }
    })
    return jsonify(data=item)
```

## 添加删除路线

最后，我们将添加一个删除歌曲的路由。

```
@app.route(BASE_ROUTE + '/<song_id>', methods=['PUT'])
def update_song(song_id):
    client.update_item(
        TableName=TABLE,
        Key={'id': {'S': song_id}},
        UpdateExpression='SET #name = :name, #year = :year, #link = :link',
        ExpressionAttributeNames={
            '#name': 'name',
            '#year': 'year',
            '#link': 'link'
        },
        ExpressionAttributeValues={
            ':name': {'S': request.json['name']},
            ':year': {'S': request.json['year']},
            ':link': {'S': request.json['link']},
        }
    )
    return jsonify(message="item updated")
```

## 运行`amplify push -y`以部署您的更改！

排除故障

```
@app.route(BASE_ROUTE + '/<song_id>', methods=['DELETE'])
def delete_song(song_id):
    client.delete_item(
        TableName=TABLE,
        Key={'id': {'S': song_id}}
    )
    return jsonify(message="song deleted")
```

为了调试 API 的问题，您可以用一个`event.json`文件更新 run `amplify mock`来匹配您请求的事件对象。例如，要测试`/song`路径，您可以使用如下事件:

## `event.json`

然后运行:

在本地测试您的功能。

```
{ "path": "/song", "httpMethod": "GET", "queryStringParameters": ""}
```

后续步骤

```
$ amplify mock function britneyspearsapi
```

本教程演示了如何使用 AWS SDK 和 AWS Amplify 生成的 Lambda 函数来构建完整的 CRUD API。你可以继续使用其他的放大资源，比如存储歌曲文件的存储器，或者限制 API 使用的认证。您还可以构建一个完整的前端来提取数据。

## Next Steps

This tutorial demonstrates how to use the AWS SDK with an AWS Amplify-generated Lambda function to build a full CRUD API. You could continue to use other Amplify resources like storage to store the song files, or authentication to restrict the API usage. You could also build out a full frontend to pull the data.