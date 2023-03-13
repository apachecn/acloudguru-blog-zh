# Docker Compose 入门

> 原文：<https://acloudguru.com/blog/engineering/getting-started-with-docker-compose>

弥合 Docker 和 Kubernetes 之间的差距可能会令人生畏——根据您的用例，它可能实际上对您没有必要。如果您希望能够有一个创建和编排少量容器的可重复过程，那么 Docker Compose 可能非常适合您。在跟进之前，请确保[安装 Docker Compose](https://docs.docker.com/compose/install/) 。

#### 定义 Docker 合成服务

当我们开始使用越来越多的`docker run`功能运行容器时，命令会变得非常冗长，很难记住。幸运的是，Docker Compose 允许我们使用特定的键将这些写在 [YAML](https://wpengine.linuxacademy.com/devops/learn-the-yaml-basics/?utm_source) 中，这些键映射到我们可以传递给各种 Docker 命令的选项。让我们用一个足够复杂的`docker run`命令来启动一个使用环境变量配置的 MySQL 容器，并将它转换成一个`docker-compose.yml`中的 YAML。下面是我们开始使用的命令:

```
$ docker run -d   --name mysql:5.7   -p 3306:3306   -e MYSQL_ROOT_PASSWORD=secret_password   -e MYSQL_DATABASE=linuxacademy   mysql
```

在设置了一些样板文件后，我们可以在一个`docker-compose.yml`文件中创建这个容器作为“服务”。这里是我们的开始: *docker-compose.yml*

```
version: "3"services:  mysql:    image: "mysql"    environment:      MYSQL_ROOT_PASSWORD: "secret_password"      MYSQL_DATABASE: "linuxacademy"    ports:      - "3306:3306"
```

用于`docker-compose.yml`文件的语法有几个不同的版本，但是我们应该总是使用最新的，在撰写本文时是 3.x。从那里，我们声明我们想要定义“服务”,这里的任何项目都将是 Docker Compose 为我们创建和运行的容器。在我们的`mysql`服务定义中，我们有一些键，可以将映射设置为非常接近手动使用`docker run`时使用的选项。值得注意的是，如果一个选项接受一个列表，并且值不包含等号(`=`，那么我们将使用 YAML 列表(以`-`开始)，否则我们将使用 YAML 键/值对，就像我们在`environment`部分所做的那样。从我们创建`docker-compose.yml`文件的目录中，我们可以使用带有`-d`标志的`docker-compose up`在后台创建并运行我们的容器，以对容器进行后台管理:

```
$ docker-compose up -dCreating network "docker-compose-example_default" with the default driverCreating docker-compose-example_mysql_1 ... done
```

我的目录名为`docker-compose-example`，Docker Compose 将根据目录名和服务名创建一个惟一的容器名。在我的例子中，我得到了`docker-compose-example_mysql_1`。尾随的`_1`处理我们想要运行容器的多个副本的事件。

#### 删除硬编码的环境变量

我们可以对我们的`mysql`服务做的一个改进就是不要硬编码环境变量。理想情况下，我们希望将我们的`docker-compose.yml`文件添加到源代码控制中，我们绝对不希望将我们的凭证提交到 git 中。幸运的是，Docker Compose 为我们传递现有的环境变量值提供了一个很好的方法。我们需要做的第一件事是从我们的`docker-compose.yml`文件中删除值，同时保留键: *docker-compose.yml*

```
version: "3"services:  mysql:  image: "mysql:5.7"    environment:      MYSQL_ROOT_PASSWORD:      MYSQL_DATABASE:    ports:      - "3306:3306"
```

为了测试这一点，我们想要删除使用`docker-compose down`创建的容器 Docker Compose:

```
$ docker-compose downStopping docker-compose-example_mysql_1 ... doneRemoving docker-compose-example_mysql_1 ... doneRemoving network docker-compose-example_default
```

接下来，我们将在运行`docker-compose up`时定义环境变量:

```
$ MYSQL_ROOT_PASSWORD=secret_password MYSQL_DATABASE=linuxacademy docker-compose up -dCreating network "docker-compose-example_default" with the default driverCreating docker-compose-example_mysql_1 ... done
```

我们不再在文件中设置这些值，但是如果我们检查容器和 grep 中的`MYSQL_`环境变量，我们可以看到这些值设置正确。*注意:*你可以使用`docker-compose ps`找到你的容器的名字。这是我所看到的:

```
$ docker inspect docker-compose-example_mysql_1 | grep MYSQL_                "MYSQL_ROOT_PASSWORD=secret_password",                "MYSQL_DATABASE=linuxacademy",                "MYSQL_MAJOR=5.7",                "MYSQL_VERSION=5.7.25-1debian9"
```

#### 编排容器

知道如何使用 Docker Compose 创建一个容器让我们非常接近能够编排多个容器。我们将遵循相同的步骤，在与我们的`mysql`键相同的层创建另一个对象。在这个例子中，让我们创建一个 [Ghost blog](https://hub.docker.com/_/ghost/) 容器，它将需要并连接到我们的`mysql`服务: *docker-compose.yml*

```
version: "3"services:  mysql:    image: "mysql:5.7"    environment:      MYSQL_ROOT_PASSWORD:      MYSQL_DATABASE:    ports:      - "3306:3306"  blog:    image: "ghost:2-alpine"    ports:      - "8080:2368"    environment:      DATABASE__CLIENT: mysql      DATABASE__CONNECTION__HOST: mysql      DATABASE__CONNECTION__USER: root      DATABASE__CONNECTION__DATABASE:      DATABASE__CONNECTION__PASSWORD:    depends_on:      - mysql
```

这里需要注意的是我们在`blog`服务中的`depends_on`键。通过指定这一点，我们告诉 Docker Compose`mysql`服务需要在`blog`服务之前启动，因为`blog`服务需要它来运行。此外，当我们为博客配置数据库连接时，我们将数据库的“主机”指定为`mysql`。这看起来很奇怪，但是在 Docker Compose 为我们的容器创建的内部网络上，其他容器(即我们的`blog`容器)可以使用`mysql`的完全限定域名(FQDN)访问`mysql`容器。我们已经运行了`mysql`容器，但是我们仍然可以运行`docker-compose up`，它将运行我们的附加容器:

```
$ MYSQL_ROOT_PASSWORD=secret_password MYSQL_DATABASE=linuxacademy DATABASE__CONNECTION__PASSWORD=secret_password DATABASE__CONNECTION__DATABASE=linuxacademy docker-compose up -dPulling blog (ghost:2-alpine)...2-alpine: Pulling from library/ghost169185f82c45: Pull complete62154f231947: Pull completeacf10a8404b6: Pull complete111312b8db58: Pull complete5a8b3dd4622e: Pull complete77aff150715c: Pull complete46a1198e6d9b: Pull completed94cdfbec967: Pull complete0007942647d7: Pull completeRecreating docker-compose-example_mysql_1 ... doneCreating docker-compose-example_blog_1    ... done
```

现在，我们可以通过连接到端口`8080`上的 Docker 主机的 IP 地址来访问我们的博客。

#### 创建卷

我们要看的最后一件事是如何通过为我们的数据库装载一个卷来改进我们为我们的博客存储数据的方式。这一改变将允许我们保留我们的数据，即使我们移除了`mysql`容器。Docker Compose 使这变得容易，因为它将卷和网络视为顶级对象，就像“服务”一样让我们创建一个名为`db-data`的卷，并将其装入我们的`mysql`容器: *docker-compose.yml*

```
version: "3"volumes:  db-data:    external: falseservices:  mysql:    image: "mysql:5.7"    environment:      MYSQL_ROOT_PASSWORD:      MYSQL_DATABASE:    ports:      - "3306:3306"    volumes:      - "db-data:/var/lib/mysql"  blog:    image: "ghost:2-alpine"    ports:      - "8080:2368"    environment:      DATABASE__CLIENT: mysql      DATABASE__CONNECTION__HOST: mysql      DATABASE__CONNECTION__USER: root      DATABASE__CONNECTION__DATABASE:      DATABASE__CONNECTION__PASSWORD:    depends_on:      - mysql
```

这对我们来说非常有用，它会为我们创造销量。`external: false`设置告诉 Docker Compose 我们没有在 Docker Compose 的“外部”创建卷。为了让我们的`mysql`服务使用它，我们需要创建一个新的容器。一个简单的方法是运行`docker-compose down`:

```
$ docker-compose downStopping docker-compose-example_blog_1  ... doneStopping docker-compose-example_mysql_1 ... doneRemoving docker-compose-example_blog_1  ... doneRemoving docker-compose-example_mysql_1 ... doneRemoving network docker-compose-example_default
```

现在，我们可以重新创建我们的容器，以便将数据写入卷中。

```
$ MYSQL_ROOT_PASSWORD=secret_password MYSQL_DATABASE=linuxacademy DATABASE__CONNECTION__PASSWORD=secret_password DATABASE__CONNECTION__DATABASE=linuxacademy docker-compose up -dCreating network "docker-compose-example_default" with the default driverCreating docker-compose-example_mysql_1 ... doneCreating docker-compose-example_blog_1  ... done
```

#### 从总体上深入挖掘 Docker

Docker Compose 非常棒，尤其是作为开始使用 Docker 和使用更复杂的系统如 [Docker Swarm](https://acloudguru.com/hands-on-labs/using-storage-volumes-with-docker-swarm) 或 Kubernetes 之间的权宜之计。如果你认为你已经准备好迈出下一步，或者你只是想了解更多，我会鼓励你去看看这些课程:**附加资源:**