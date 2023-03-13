# 免费启动您的第一个 Ansible 动手实验室|云专家

> 原文：<https://acloudguru.com/blog/engineering/launch-your-first-ansible-hands-on-lab-for-free>

什么是动手实验？

## 您的第一个可回答的动手实验

Hands-On Labs is a key feature when it comes to learning practical skills. Instead of simply watching videos, [Hands-On Labs deploy real environments](https://linuxacademy.com/blog/linux-academy/instantly-launch-hands-on-labs-with-instant-labs/) with real-world scenarios for you to complete. By completing those scenarios, you are building skills that can be used directly on the job.

剧本是 Ansible 的核心。它们提供了一种在任意数量的系统上执行大量任务的方法。这个动手实验通过让你制作和执行一个可行的剧本，让你踏上精通可行的道路。在实验结束时，您将完成第一份可行的行动手册。

Most of the Hands-On Labs in our [Learn Ansible By Doing course](https://linuxacademy.com/devops/training/course/name/learn-ansible-by-doing) are less than 15 Gems to launch, so you could launch at least 2-3 labs as part of this walkthrough we are doing, for free. You can also earn more Gems by referring members or [taking other actions](https://linuxacademy.com/blog/tips/linux-academy-gems-explained/).

## Your First Ansible Hands-On Lab

真实世界场景完成

在这个可行的动手实验中，**我们将完成以下场景** :

If you haven’t already, [go to this link](https://beta.linuxacademy.com/#/hands-on-labs/details/1681e41c-22cc-4a11-b12c-eaef01468e62) and click on “Start Hands-On Lab.” We’re ready to get started!

*您的主管要求您寻找一种方法来自动化和审核您环境中新服务器的基本系统配置。假设 Ansible 已经在您的环境中进行了基本配置，那么最简单的解决方案就是编写一个脚本来引导您的新主机。*

### **按照这些说明完成场景** :

创建一个名为/home/ansi ble/bootstrap . yml的剧本，以满足以下引导需求:

在所有提供的服务器上:

编辑 /etc/hosts 以包含以下条目: `ansible.xyzcorp.com  169.168.0.1`

安装elinks

创建用户 xyzcorp_audit

将文件`/home/ansible/motd` 和`/home/ansible/issue` 复制到`/etc/`

1.  在提供的网络服务器上:
2.  安装【nmap-ncat】
3.  创建用户 xyzcorp_network

在提供的系统管理员服务器上:

将`/home/ansible/scripts.tgz` 从控制节点复制到`/mnt/storage`

*   已经为您配置了 Ansible 控制节点，并且每个测试服务器都已经配置为使用 Ansible。默认清单已配置为包括组 network 和 sysadmin。每个组包括一个示例主机。

完成上述情景和说明后，**我们将完成以下目标** :

*   为可行清单中的所有服务器创建一个基本行动手册。

在行动手册中添加一节，介绍易变清单中的网络服务器。

在行动手册中为 Ansible 清单中的 SysAdmin 服务器添加一个部分。

执行行动手册以验证您的行动手册工作正常

为此，您将使用实验页面上的给定凭证 SSH 到 Ansible 控制节点。在这里，您将配置行动手册，该手册将完成我们的说明中的任务，并在其他 2 个节点上执行操作。

*   您的证书可能与我的不同，但这是它们在实验操作页面上的样子
*   *服务器凭证*
*   帮助你的学习工具

如果您不确定如何完成说明中列出的目标和任务，我们会提供书面指南和视频。这些旨在引导您从头到尾完成整个场景，这样，如果您在这个动手实验中遇到困难，您可以查看解决方案并继续前进。

*视频指南*

*文字指导*

### 除了书面指南和视频指南，我们还提供了架构图，以可视化的形式向您展示最终结果。如果你像我一样是视觉学习者，这真的可以帮助记忆概念和解决方案。

*建筑示意图*

**完成场景，获得新技能！**

现在，您可以访问动手实验环境和所需的培训资源，以便完成本实验、学习新技能并继续进行更多可行的实验！

以下是其他一些可行的动手实验，例如:

### **Complete the scenario and earn a new skill!**

You now have access to the Hands-On Lab environment and the training resources you need in order to complete this lab, learn a new skill, and move on to more Ansible labs!

Here are some other Ansible Hands-On Labs, for example:

If you are [part of a business account](https://linuxacademy.com/team), **your manager can see exactly which skills you’ve gained** as a result of your training on Linux Academy, and that can go a very long way!