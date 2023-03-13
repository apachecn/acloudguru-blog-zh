# 剖析 Travis CI 文件|云专家

> 原文：<https://acloudguru.com/blog/engineering/anatomy-of-a-travis-ci-file>

Travisfile 或. travis.yaml 文件是用于建立 Travis CI 平台的主要工具。在这篇文章中，我们将介绍 Travisfile，并对. travis.yml 文件提供的不同选项进行深入分析。

## 什么是特拉维斯 CI？

Travis CI 让我们能够自动化代码测试、集成、交付和部署的过程，让我们能够将 [DevOps](https://acloudguru.com/learning-paths/devops) 和[敏捷](https://acloudguru.com/blog/engineering/devops-vs-agile-whats-the-difference)原则引入到从推送到生产部署的代码实践中。

Travis CI 是完全托管的，只需点击几下按钮即可使用，它与您现有的版本控制系统结合在一起，使您能够以最少的前期工作自动进行构建测试和更多工作——必须提供自己的测试基础架构的日子已经一去不复返了！

* * *

## 加速您的职业发展

[从 ACG 开始](https://acloudguru.com/pricing)通过 AWS、Microsoft Azure、Google Cloud 等领域的课程和实际动手实验室改变你的职业生涯。

* * *

## 什么是 Travisfile？

Travis CI 与我们现有的版本控制相结合，因此我们可以自动测试和部署我们的代码。但是为了让 Travis 在没有我们想要的规范的情况下工作，我们需要为它提供一个文件:`.travis.yml`文件——也称为“Travisfile”。

Travisfile 包含了我们管理代码的测试和部署所需的所有指令。

我们在此文件中提供的信息将用于两个目的之一:

*   它可以是关于代码的一个事实，比如编程语言、版本或者需要的服务
*   或者实际构建**阶段**的一部分——构建、测试和部署代码的特定指令

最起码，我们需要告诉特拉维斯我们在用什么语言。事实上，下面这段代码很可能是一个成功的 Travisfile:

`language: node_js`

一旦 Travis 知道使用哪种语言，它就可以假定构建环境、语言版本、安装脚本、构建脚本和其他工作。这些是我们构建的基本“事实”。

| **参数** | `env` |
| 构建环境；这是部署代码的环境 | `language` |
| 编写代码所用的语言 | `[language_name]` |
| 将语言名称指定为键，版本是提供特定版本的值 | `services` |
| 在构建环境中启用服务，比如 Docker 或 MongoDB | `install` |
| 准备构建环境的安装步骤 | `script` |
| 构建应用程序的步骤 | `jobs.include` |
| 并行构建和阶段的附加参数 | `install`和`script`也是*阶段*，阶段是 Travis 设置、构建、测试和潜在部署应用程序的步骤。 |

有 12 个构建阶段，只有`install`和`script`是强制的——尽管这些通常是在语言级别设置的，并且通常不需要手动提供。

也就是说，如果需要，我们可以为每个阶段提供我们自己的命令:

**参数/相位**

| `apt.addons` | 添加 apt 源以安装软件包 |
| `cache.components` | 在启用缓存时，安装缓存构建所需的组件 |
| `before_install` | 命令在安装阶段之前运行 |
| `install` | 安装命令 |
| `before_script` | 在应用程序构建之前运行的命令 |
| `script` | 构建脚本 |
| `before_cache` | 缓存构建之前要运行的命令 |
| `after_success/after_failure` | 生成成功或失败时运行的命令 |
| `before_deploy` | 部署代码之前要运行的命令 |
| `deploy` | 部署代码的方法 |
| `after_deploy` | 成功部署后要运行的命令 |
| `after_script` | 完成 Travis 运行之前要运行的最后命令 |
| 例如，一个更复杂的 Travisfile 可能如下所示: | 这将设置构建环境、语言和版本、所需的服务，并在设置部署到 GitHub 版本的方法之前运行两个定制脚本(一个在安装之前，另一个替换默认的 Node.js 安装命令)。 |

它还利用了一些有用的功能来构建我们的文件，例如定义所需的分支，如果正在工作的分支是“docker ”,它还提供了一个替代工作。

```
env: focal
language: node_js
node_js: 'lts/*'
services: rabbitmq
before_install: ./init.sh
install: ./install.sh
after_success: ./package.sh
jobs:
  include:
	- stage: docker
  	after_success: docker push "$DOCKER_USERNAME"/app
  	if: branch = docker
deploy:
  provider: releases
  api_key: "$GITHUB_TOKEN"
  file: app.tar.gz
  skip_cleanup: true
  on:
	branch: main
```

Travis CI 是一个方便的平台，可以轻松地测试、集成、交付和部署我们的代码，并且对所需的`.travis.yml`文件有了很好的了解，我们可以根据需要为 Travis 设置所有的项目。

想要提升你的技术技能吗？查看 [*本月免费课程*](https://acloudguru.com/blog/news/whats-free-at-acg) *(不需要信用卡！)，包括*[*【YAML 要领】*](https://acloudguru.com/course/yaml-essentials)*[*GitHub Actions 深潜*](https://acloudguru.com/course/github-actions-deep-dive) *，以及*[*Python 开发入门*](https://acloudguru.com/course/introduction-to-python-development) *。**

*了解有关 Travis CI 的更多信息*

* * *

*想了解更多关于 Travis CI 的信息吗？查看我的新课程[与 Travis CI](https://acloudguru.com/course/Building-a-Continuous-Integration-Pipeline-with-Travis-CI) 一起构建持续集成管道。*

* * *

## *本课程通过分解`.travis.yaml`文件让您开始学习 Travis CI。通过分解这个文件，我们将使用它的结构来了解 Travis CI 在集成我们的应用程序时所采用的不同构建阶段。有了这些阶段的知识，我们就可以优化我们的 Travisfile 来执行许多工作，根据许多参数进行测试，并行和分阶段工作，并根据需要部署到尽可能多的端点。*

**通过在* [*上关注一位云大师来保持联系*](https://twitter.com/acloudguru)*[*【脸书】*](https://www.facebook.com/acloudguru)*[*在 YouTube 上订阅一位云大师*](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1) *进行每周更新，并在* [*上加入对话*](http://discord.gg/acloudguru) *。您也可以查看我们本期的* [*免费课程*](https://acloudguru.com/blog/news/whats-free-at-acg) *！****

**This course gets you started with Travis CI by breaking down the `.travis.yaml` file. By breaking down this file, we’ll use its structure to learn the different build phases Travis CI takes when integrating our application. With knowledge of these phases, we can then optimize our Travisfile to perform a number of jobs, test against a number of parameters, work in both parallel and in stages, and deploy to as many endpoints as we need.**

***Keep in touch by following A Cloud Guru on* [*Twitter*](https://twitter.com/acloudguru) *and* [*Facebook*](https://www.facebook.com/acloudguru)*,* [*subscribe to A Cloud Guru*](https://www.youtube.com/c/AcloudGuru/?sub_confirmation=1) *on YouTube for weekly updates, and join the conversation on* [*Discord*](http://discord.gg/acloudguru)*. You can also check out our current crop of* [*free courses*](https://acloudguru.com/blog/news/whats-free-at-acg)*!***