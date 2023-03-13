# 使用瞭望塔让您的容器保持最新

> 原文：<https://acloudguru.com/blog/engineering/using-watchtower-to-keep-your-containers-up-to-date>

了望塔是一个应用程序，监视你的

[running containers](https://wpengine.linuxacademy.com/linuxacademy-com/history-of-container-technology/)

对于图像的改变。当您向 Docker 注册表推送更新时，Watchtower 会检测到更改，并下载映像的新副本。然后，它将使用新的映像和与原始映像相同的启动选项重新启动容器。

例如，假设您有一个名为`my-app`的容器化应用程序，它使用端口映射`8090:3000`运行。您的团队使用 CI/CD 推出应用程序的每日更新。迭代完成后，您可以标记图像并将其上传到注册表。瞭望塔被配置为每 60 秒检查一次注册表。一旦 60 秒的迭代完成，它会检测到`my-app`图像的变化并将其拉下。然后，Watchtower 优雅地关闭`my-app`容器，然后使用端口映射为`8090:3000`的新映像重新启动它。

为了让所有这些工作，瞭望塔需要能够访问 Docker API。当创建瞭望塔容器时，你需要挂载`/var/run/docker.sock`作为一个卷。

## **使用瞭望塔**

现在，让我们去启动了望塔。如果您已经安装了 Docker，或者您的一个云服务器使用 Docker 认证发行版作为镜像，那么您可以使用您的本地系统。在下面的示例中，我们将创建一个使用以下启动选项的瞭望塔容器。容器将总是被重新启动。它会上升

`/var/run/docker.sock`

到

`/var/run/docker.sock`

在集装箱上。默认情况下，瞭望塔将每 5 分钟检查一次图像注册表。我们希望它每 30 秒检查一次，所以使用

`-i`

轮询间隔设置为的标志

`30`

。关于瞭望塔选项的完整列表，请访问 GitHub

[readme](https://github.com/v2tec/watchtower)

.

```
docker run -d --name watchtower   --restart always   -v /var/run/docker.sock:/var/run/docker.sock   v2tec/watchtower   -i 30
```

现在，瞭望塔容器正在运行，让我们为它创建一个要监视的容器。在您的系统上，创建一个`index.html`文件。例如:

```
<html>  <header>    <title>My We Page</title>  </header>  <body>    This is my web page.  </body></html>
```

现在创建一个 Dockerfile，它使用 nginx 作为基本图像。将`index.html`文件复制到容器上的`/usr/share/nginx/html/index.html`。将`/usr/share/nginx/html`设置为工作目录。

Dockerfile:

一旦 docker 文件准备好了，就建立你的形象。您可能希望在您的私人注册表上用您的 Docker Hub 用户名或该图像的完整 URL 来标记该图像。在下面的例子中，我将使用我的 Docker Hub 用户名。

## 登录并推送图像:

```
FROM nginxCOPY index.html /usr/share/nginx/html/index.htmlWORKDIR /usr/share/nginx/html
```

使用您推送到注册表的映像创建一个容器:

```
docker build -t rivethead42/nginx -f Dockerfile .
```

执行`docker ps`来确保你的容器正在运行。验证容器正在运行后，您可以等待几分钟，然后再进行任何更改。我们将检查容器的状态，以确认瞭望塔已经更新了它。

```
docker logindocker push rivethead42/nginx
```

Create a container using the image you pushed to the registry:

```
docker run -d —name my-web-page -p 80:80 —restart always rivethead42/nginx
```

Execute `docker ps` to make sure your container is running. After verifying that the container is running, you can wait a few minutes before making any changes. We’ll be checking the status of the container to verify that Watchtower has updated it.

既然`my-web-page`容器已经运行了几分钟，让我们对`index.html`文件做一个更改。

```
docker ps
```

执行`docker ps`并通过检查状态来记录容器已经运行了多长时间。重建映像并将其推送到 Docker Hub:

```
<html>  <header>    <title>My We Page</title>  </header>  <body>    This is my web page, how do you like it?  </body></html>
```

现在我们等待了望塔来检测变化。定期运行`docker ps`检查容器状态。当它低于初始状态时，我们知道瞭望塔发挥了它的魔力。

```
docker psdocker build -t rivethead42/nginx -f Dockerfile .docker push rivethead42/nginx
```

如你所见，通过使用瞭望塔，保持容器最新是非常容易的。如果你想了解你能用 Docker 做的其他事情，看看我最新的课程

Now we wait for Watchtower to detect the changes. Periodically run `docker ps` to check the container status. When it is less than the original status, we know that Watchtower has worked its magic.

```
docker ps
```

As you can see, it’s pretty easy to keep containers up to date by using Watchtower. If you want to learn about other things you can do with Docker, check out my latest course

** [Learn Docker By Doing](https://linuxacademy.com/containers/training/course/name/docker-and-container-orchestration-hands-orchestration-hands-on).**