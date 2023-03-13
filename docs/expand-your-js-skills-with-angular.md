# Angular |云专家入门

> 原文：<https://acloudguru.com/blog/engineering/expand-your-js-skills-with-angular>

即使你是 web 开发领域的新手，你也可能听说过 Angular——而且理由很充分。它是当今开发人员使用的最流行、最强大的 web 框架之一。

在您学习了 HTML、CSS 和 Javascript 的基础知识之后，您可能会发现自己正在寻找一个更加结构化和更加通用的平台来开始构建更加健壮的 web 应用程序。别再看了:Angular 是来拯救我们的。

这篇文章将带你了解构建 Angular 应用程序前需要了解的几个关键步骤。在这篇文章结束时，您应该对安装、创建、构建和部署 Angular 应用程序有所了解。

## 有角和有角 JS 有什么区别？

AngularJS 最初是由谷歌在 2010 年作为开源项目发布的，大约在 2014 年，谷歌团队开始重写 AngularJS，以创建一个具有新功能和增强功能的更强大的框架。这就是 Angular 诞生的时候。

2016 年，Angular 版本 2 发布，更名为 just“Angular”。所以，我们都在同一页上。AngularJS 和 Angular 不是同一个框架！这意味着在生产中运行 AngularJS 应用程序的开发团队需要在重写他们的应用程序和承担维护一个最终不受支持的框架的责任之间做出选择。因此，在 2016 年至 2018 年(AngularJS 进入 LTS)期间，团队处于恐慌期，决定层应用的发展方向。那些选择重写应用程序的人面临着许多挑战，但最终还是很高兴。

Angular 提供了许多优于 AngularJS 的好处，例如，像 Angular CLI 这样的工具，更结构化的编程语言(也称为 Typescript)，更直观的项目结构和编程范例。我是从 AngularJS 迁移到 Angular 的团队的一员，我最终很高兴，并且从未回头。

![](img/4bd8cda72d84b22aee1a29600e8c101d.png)

Angular 项目可以用于各种各样的 web 应用程序，从简单的小型网站到拥有数百万用户的企业应用程序。无论应用程序的健壮性如何，您都需要从某个地方开始。

您需要安装正确的工具，您需要创建一个 Angular 应用程序，并且您需要实时部署它。之后，让 sprint 周期开始，挂钩您的版本控制，让聪明的人做一些 CI/CD 魔术，然后你就有了一个活生生的 Angular 应用程序，为世界带来超级重要的信息。

要开始构建您的 Angular 应用程序，您需要首先安装 [Angular CLI](https://angular.io/cli) 。

Angular CLI 是构建 Angular 应用程序的开发人员的必备工具。您可以创建新项目、打开文档、为应用程序生成各种元素、服务、构建、测试、调试、lint、部署等等。这是一个必要的工具，你需要开始你的角度之旅。但是在安装 Angular CLI 之前，请耐心等待，您需要安装 Node.js 和 npm。幸运的是，Node.js 网站使它非常容易下载和安装，npm 包含在 Node.js 的安装中。

您可以通过运行以下命令来验证 Node.js 是否已安装。

`node --version`

`npm --version`

![](img/1a6d288b9df948922267b2d4da0d1f50.png)

之后，您就可以安装 Angular CLI 了。这可以通过运行以下命令来完成。

`npm install -g @angular/cli`

这将全局安装 Angular CLI，以便您能够开始构建 Angular 应用程序。您可以通过运行以下命令来验证安装是否成功。

`ng --version`

![](img/7e2dfb1b68512897e7a125c40697ddb5.png)

## **第二步:** **创建一个角度应用**

一旦安装了 Angular CLI，乐趣就开始了！我们可以使用我们新安装的 Angular CLI 为我们生成一个新的 Angular skeleton 项目。我们可以通过运行以下命令来做到这一点。

`ng new <app-name>`

只需将“`<app-name>`”替换为您的优秀项目的名称，Angular CLI 将开始构建您的项目。

系统会提示您是否要在项目中包含角度布线以及要使用何种 CSS 格式。您也可以在``ng new`'命令中将这些作为参数传递，但是为了简单起见，上面的命令就是您所需要的。

![](img/d3ca2bed434b0dee132c91b140eff10f.png)![](img/51e0a5df0ec2d58fc4d0f95157aeab08.png)

一旦 Angular CLI 完成，您将有一个全新的准备开始开发搭建出来的 Angular 应用程序。恭喜你，你是一个有棱角的开发者！

## **第三步:** **为你的角 App 服务**

一旦您准备好开发 Angular 应用程序，您将需要在本地提供它，这样您就可以在 Angular 项目中实际看到您所做的更改。

您可以使用下面的命令在本地运行您的 Angular 应用程序，以便开始开发和调试。首先，您需要在项目目录中导航

`cd <app-name>`

然后运行以下命令

`ng serve`

这将编译您的所有 Typescript 代码，并允许您打开 web 浏览器并查看您的应用程序。默认情况下，Angular 在端口 4200 上启动应用程序，因此您应该能够从“http://localhost:4200”上查看应用程序。

在这里，您可以直接对 Angular 项目进行更改，并在 web 浏览器中看到它们自动刷新。这是使用 Angular CLI 和自动刷新功能的另一大优势。

![](img/003380f6e7fb702ea627ddb513f57e63.png)![](img/78b6512287a60f6fe332a3b96a286f7e.png)

从这里开始，天空就是极限。您可以开始构建其他组件、服务，并实现路由，使您的 Angular 应用程序更加健壮。

当然，这只是对创建和构建 Angular 应用程序的简单介绍。你决定的实现和特性的丰富性将从这里开始闪耀。

## **第四步:部署你的 Angular 应用**

一旦你有了一个令人敬畏的 Angular 应用程序，并准备好向全世界展示，你就需要构建你的项目，以便它可以用于生产，或者一些外部公共可访问的地方。

有许多不同的方法来托管 web 应用程序。这可以在任何云平台(AWS、GCP、Azure)或其他部署平台上完成，如 [GitHub Pages](https://pages.github.com/) 、 [Netlify](https://www.netlify.com/) 、 [Firebase Hosting](https://firebase.google.com/docs/hosting) 等等。您甚至可以启动一个简单的 Apache 或 Nginx 服务器，并在那里托管文件。

无论您选择什么，您都很可能需要运行以下命令来编译并打包成一个单页面应用程序。这个命令的作用是将你的应用程序打包成一个 HTML 文件、几个 javascript 和 CSS 文件，以及你可能拥有的任何其他资产，比如图像或视频。这几个文件可以上传到您的部署平台，并准备好提供给您的最终用户。要编译、构建和打包 Angular 应用程序，请使用以下命令:

`ng build --prod`

这将在您的项目目录中创建几个文件(在一个名为``dist/`的文件夹中)。

![](img/ad38e039b701dccf4f4edba790b6866f.png)

为了让事情变得更简单，有一些流行的工具可以让您使用``ng deploy`'命令让您的部署更进一步。您不必手动上传这些文件，您可以简单地配置部署工具，运行``ng deploy``命令，应用程序将编译、构建、打包和部署您的 Angular 应用程序。很可爱，是吧？

以下是一些已经创建并准备好使用的部署工具的链接:[https://angular . io/guide/deployment # automatic-deployment-with-the-CLI](https://angular.io/guide/deployment#automatic-deployment-with-the-cli)

## **了解更多关于 Angular 的信息**

无论是构建简单的 web 应用程序还是健壮的企业应用程序，在决定使用框架时，Angular 都应该是首选。在某些情况下，其他框架可能更适合您团队的需求，但是由于健壮性、结构、强大的设计模式、健壮的支持和工具生态系统，它是迄今为止我最喜欢的用于行业和个人项目的 web 框架。

这篇文章只是对 Angular 提供的能力的一瞥，但是嘿，你必须从某个地方开始！如果不了解如何安装、创建、构建和部署 Angular 应用程序，那么您将无法学习更多内容。

如果您想了解更多关于 Angular 应用程序的原理和元素，甚至是简单的实现，那么请查看课程[使用 Angular](https://acloud.guru/learn/expanding-your-js-skills-with-angular) 扩展您的 JS 技能(由您真正创建)。

[![](img/f90a61f5da0648ec2049f161c1686281.png)](https://acloud.guru/learn/expanding-your-js-skills-with-angular)

## 其他资源和链接