# 红帽考试:几个小技巧

> 原文：<https://acloudguru.com/blog/engineering/red-hat-exams-a-few-tips>

Alright, so you’ve dipped your toes in the Red Hat ecosystem and you’ve been studying (at least, I hope you have!) You’ve probably learned a lot of great ways to do things and are possibly gearing up to take the [RHCSA](https://acloudguru.com/course/red-hat-certified-system-administrator-ex200-exam-prep). Let’s discuss a few things that may help when the test comes around. Please keep in mind, the NDA for Red Hat exams are no joke, so I will be adhering to that throughout this article.

## 你将不得不与什么一起工作

在你登录并获准进入测试室后，你会看到一个终端。这不是普通的终端，这个终端集成了摄像头和麦克风，可以记录你的每一个动作和呼吸。当你参加考试时，请记住这一点，尽量不要发表任何与考试有关的 【咸】 评论！该终端将安装 RHEL 7，并安装 GUI。您将获得一个虚拟机进行访问。这个虚拟机是您执行大部分任务的地方，这些任务也显示在终端上。**确保在开始之前阅读所有任务！**这一点非常重要！您遇到的一些任务可能与其他任务相关，如果您按顺序执行它们，可能会发生冲突并导致问题。

好了，现在我们已经讨论了您的环境 (所有 都已由 Red Hat 在各种公开帖子中详述)，让我们稍微谈谈目标和一些可能有助于实现目标的提示。

## 目标

*   **了解并使用必备工具**
*   **操作运行系统**
*   **配置本地存储**
*   **创建和配置文件系统**
*   **部署、配置和维护系统**
*   **管理用户和群组**
*   **管理安全**

我将一个接一个地讨论这些问题，并提供一些见解或提示，可能有助于你在考试中可能遇到的排列。

I’m going to go through these one-by-one and just provide a little insight or tips that may help with possible permutations you may encounter on the exam. 

了解并使用基本工具

## Understand and use essential tools

如上面链接的官方目标页面所示，理解和使用基本工具包括 grep、将输出重定向到文件、压缩这些文件、修改权限等等。到目前为止，这些应该已经是第二天性了，但是请记住，考试是非常无情的。如果你做错了，你的意图不会被考虑。如果您不小心打错了一些东西，比如一个许可，或者 grep 一个额外的字符，您将错过这个目标。 由于任务数量相对较少，错过整个任务会对你的分数非常不利。你也会有很大的压力，因为 RHCSA 不是一个便宜的考试！

As shown on the official objectives page linked above, understanding and using essential tools can include grep, redirecting output to files, compressing these files, modifying permissions, and so on. A lot of these should be second nature by now, but keep in mind that the exam is very unforgiving. If you do something incorrectly, your intention is not taken into consideration. If you accidentally mistype something, such as a permission, or grep an extra character, you will miss that objective. With the relatively small number of tasks, missing an entire task can be very detrimental to your score. You will also be under a lot of pressure as the RHCSA is not a cheap exam!

我建议你**在开始考试的时候安装** **【服务器** **【带 GUI】组套**，这样可以更容易的检查错误！这确实需要一段时间，但是如果你在阅读任务的时候首先这么做，你就不会浪费太多时间，而且会让一些任务变得容易很多！尤其是简单的任务！

What I recommend is that you **install the** **‘Server** **with GUI’ group install when you start your exam** in order to make double checking for mistakes much easier! This does take a while, but if you do it first thing while reading your tasks, you won’t waste much time and it will make some of the tasks a lot easier! Especially the simple tasks!

操作运行系统

## Operate running systems

“操作 运行系统”目标是一个包含一些潜在任务的目标，这些任务 决定你的考试成败！如果您的环境无法引导，RHCSA 将自动使您失败。是的，你没看错，如果你的系统不能为考试评分员正确启动，你将得到一个“0/300”的分数。 即使你做对了其他所有的事情，你仍然会得到一个【0】。

The “operate running systems” objective is one that contains some potential tasks that make or break your exam! The RHCSA will fail you automatically if your environment is unable to boot. Yes, you read that right, if your system does not boot correctly for the exam grader, you will receive a score of “0/300”. It doesn’t matter if you did everything else right, you will still receive a “0”.

鉴于这一事实，当您执行任何类型的系统目标操作或其他涉及 grub 的工作时，请确保重新启动系统并进行测试！ 如果您的系统无法正常重启，您可以要求监考人员将您的虚拟机重置为初始状态。请注意，这将覆盖您已经完成的所有工作，因此我建议您首先执行重新启动后可能会失败的任何操作。这样，如果出现问题或输入错误，您不会丢失大量的工作！

Due to this fact, when you are performing any type of system target manipulation or other work that involves grub, ensure you reboot your system and test! If your system does not reboot properly, you can ask the exam proctor to reset your VM to its initial state. Do be aware that this will overwrite any work you have already completed, so I recommend you perform any actions that could potentially fail after reboot first. This way, if something goes wrong or you mistype something, you don’t lose a significant amount of work!

Another point to remember is that Red Hat can throw in some pretty hefty surprises. When you access your VM, there may be issues that have to be resolved before you can even continue into the environment. Keep this in mind and study the objectives very carefully! **The Linux Academy [hands-on labs](https://linuxacademy.com/features/labs_exercises) are crucial in preparing you for these potential surprises. **

创建和配置文件系统/配置本地存储

## Create and Configure Filesystems/Configure Local Storage

我将这两个目标结合在一起，因为它们非常相似，并且相互依赖。这些任务可能涉及 LVM、交换、fstab、不同的文件系统、调整文件系统的大小以及其他潜在的任务。非常仔细地练习这些！我还建议首先执行这些任务，因为它们会导致系统无法启动。如果您最后执行它们并出现错误，您就有可能丢失在它们之前执行的所有工作！

I have combined these two objectives since they are fairly similar and rely on each other. These tasks can involve LVM, Swap, fstab, different filesystems, resizing filesystems, and other potential tasks. Practice these very carefully! I also recommend doing these tasks first as they can cause your system not to boot. If you perform them last and have an error, you risk losing all of your work performed before them!

在配置本地存储目标中，另一件需要注意的事情是任务的顺序。在 RHCSA 上执行大多数任务有多种方式，如果您以某种方式执行一个本地存储任务，您可能会发现由于空间问题，后面的任务无法执行。在开始执行任务之前，请确保您已经阅读了所有任务。同样，阅读所有任务的最佳时间是安装 GUI 的时候。

Another thing to look out for in the configuring local storage objective is the order of the tasks. There are many ways to perform most tasks on the RHCSA, and if you perform one local storage task a certain way, you might find that a task that comes after it cannot be performed due to space concerns. Ensure you have read all the tasks before you start performing them. Again, a great time to read all tasks is when installing the GUI.

最后，我知道我 之前说过，但我再说一遍:重启！在执行可能损坏文件系统或导致根文件系统无法启动的任务后，请务必重新启动！ 这些目标的另一个潜在方面是配置 ACL。这很简单，但是**一定要仔细阅读 Linux 学院实验室**以确保你非常了解它们。这是安装 GUI 非常有用的另一个例子。

Finally, I know I said it before, but I’ll say it again: REBOOT! Always reboot after performing tasks that could damage the filesystem or cause the root filesystem not to boot!Another aspect of these objectives that could potentially show up is configuring ACLs. This is pretty straightforward, but **do go through the Linux Academy labs** to ensure you know them very well. This is another instance where having the GUI installed can be very helpful.

部署、配置和维护系统

## Deploy Configure and Maintain Systems

This objective has a significant number of potential tasks you may see. One thing that is very critical to focus on is the “Install and update software packages from Red Hat Network, a remote repository, or from the local file system” section. Although tasks can and very well may show up that contain other aspects of this objective, not being able to access a remote repository can lead to a potential instant fail! Multiple tasks could depend on this single tasks, so make sure you are very skilled at accessing remote repositories, [adding new repositories to yum](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/deployment_guide/sec-managing_yum_repositories), and other tasks that relate to these operations.

同样，在任何涉及 grub、内核修改或文件系统的事情之后，都要重新启动！

And also, once again, reboot after anything that involves grub, kernel modifications, or the filesystem! 

管理用户和群组

## Manage Users and Groups

我不打算深入探讨这个目标，因为由此产生的任务是不言自明的。确保您非常仔细地阅读，理解 sticky-bits 以及如何设置和读取权限，主组与补充组，并使用 GUI 来检查您的工作！

I’m not going to go too deep into this objective as the tasks that could stem from it are pretty self-explanatory. Ensure you read very carefully, understand sticky-bits and how to set and read permissions, primary groups vs. supplemental groups, and use the GUI to your advantage to check your work! 

管理安全

## Manage Security

啊，安全，大家最喜欢的话题！首先，是的，你应该知道 SELinux。我确实有一个有趣的小技巧，它让我的事情变得简单多了，也可能对你有所帮助！是*-e*旗。 *"-e"* 、 或*"–equal "*、 可以使将上下文镜像到新文件夹变得容易得多。

Ah, security, everyone’s favorite topic! First things first, yes, you should know SELinux. I do have a fun little tip that made things a lot easier for me and it may help you as well! It’s the “*-e*” flag. The *“-e”*, or *“–equal”*, can make mirroring context to a new folder much easier.

假设你想把默认的 Apache 目录移动到*"/var/web "*而不是 *"/var/www/html"* 。 通常，您需要找到 "/var/www/" 的正确上下文，并将其添加到 "/var/web" 文件夹中。尽管这并不难，但确实需要一些时间。

Let’s say you want to move the default Apache directory to *“/var/web”* instead of *“/var/www/html”*. Typically, you would need to find the proper context for “/var/www/” and add it to the “/var/web” folder. Although this isn’t difficult, it does take some time.

有了 *"-e"* 标志，只需一行就可以将上下文从*"/var/www/html "*复制到*"/var/web "*！ 这不是很棒吗？！

With the *“-e”* flag, you can simply copy the context from *“/var/www/html”* to *“/var/web”* with one line! Isn’t that great?!

要做到这一点，完整的命令是:*semanage f context-a-e/var/www//var/web*

To do this, the full command is:*semanage fcontext -a -e /var/www/ /var/web *

还有，别忘了执行*restorecon**-Rv/var/web*使其生效！

Also, don’t forget to perform*restorecon* *-Rv /var/web* to make it effective!

在 SELinux 之上，您可能会遇到一些防火墙任务以及 SSH 任务。既然是考试，记住速度很重要。当然，您可以使用日志来诊断防火墙/SELinux 问题，但通常更容易:

禁用 SELinux/防火墙

1.  检查问题是否解决
2.  重新启用
3.  修复
4.  通过使用这种方法，您可以验证问题并快速修复，而无需翻遍日志。这肯定不是你在生产中会做的事情，但在考试中，如果对你有用，利用更快的工作流程。再次强调，利用 GUI 为您带来优势！GUI 有一些非常简单的防火墙工具，让您的生活更加轻松。

By using this method, you can verify the problem and fix it quickly without rummaging through logs. This is certainly not something you would do in production, but on an exam, take advantage of the faster workflow if it works for you. And, again, use the GUI to your advantage! The GUI has some very simple firewall tools to make your life easier. 

结论

## Conclusion

RHCSA 考试当然不容易！这是一场令人望而生畏的考试，可以击垮在这个行业呆久了的人的精神。不要因此而气馁！祝你好运！不要忘记在测试结束时重新启动！

The RHCSA exam is certainly not easy! It is a daunting exam that can break the spirits of people who have been in the industry for a long time. **Don’t let this discourage you!** Good luck! And don’t forget to reboot at the end of your test!

ACG 为你成为红帽认证建筑师(RHCA)的旅程提供了一条学习之路。通过五门实践课程和全面的实践考试，你将完全准备好接受梦寐以求的 RHCA。

ACG offers a learning path for your journey to become a Red Hat Certified Architect (RHCA). Through five hands-on Courses and comprehensive practice exams, you’ll be completely prepared to receive the coveted RHCA.