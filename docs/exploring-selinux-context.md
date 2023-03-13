# 探索 SELinux:环境

> 原文：<https://acloudguru.com/blog/engineering/exploring-selinux-context>

SELinux 的一个关键部分是理解和使用 SELinux *上下文*。系统中的一切都包含一个上下文，这些上下文用于确定哪些用户、应用程序和服务可以访问哪些文件、目录和应用程序。即使不了解详细的策略创建，大多数 SELinux 用户也可以通过使用和改变上下文来管理他们的系统。SELinux 中有三种类型的上下文，通过查看 SELinux 对文件的权限可以很好地解释这三种上下文。要查看一个目录的 SELinux 上下文，请使用带有`-Z`标志的`ls`命令。这是为`/var/www/`准备的目录:

```
[vagrant@centos www]$ ls -Zdrwxr-xr-x. root root system_u:object_r:httpd_sys_script_exec_t:s0 cgi-bindrwxr-xr-x. root root system_u:object_r:httpd_sys_content_t:s0 html
```

我们想从权限输出中看到的是类似于`system_u:object_r:httpd_sys_script_exec_t`的部分。这是文件的三个上下文。让我们深入了解一下:

### [![SELinux contexts](img/e80bd79574f0135452c53fdc0ce32f67.png)](https://blog.linuxacademy.com/blog/wp-content/uploads/2016/11/selinuxcontext.png) 用户上下文

第一个蓝色部分是*用户上下文*。这有三个可用值:`user_u`、`system_u`和`root`。其中每一个都表示哪种类型的用户可以访问该文件，而不是具体哪个用户。在用户上下文为`user_u`的情况下，普通登录用户可以访问文件(关于普通文件权限)；值`system_u`表示系统用户——如上例所示；最后，`root`表示只有系统的 root 用户才能访问该文件。

### 角色上下文

角色上下文，在上面的例子中是洋红色的，主要用于流程和域。普通 SELinux 用户可能不需要担心这个上下文。对于文件和目录，这总是`object_u`。

### 类型上下文

紫色的类型上下文可以说是在设置 SELinux 权限和解决 SELinux 问题时最重要的上下文。类型上下文提供了与 SELinux 相关的细粒度控制。您的系统，即使只启用了缺省的 SELinux 并且没有做任何更改，也有许多类型上下文。使用`semanage fcontext -l`命令查看所有可用类型。当查看特定文件或服务的上下文时，您可能希望通过管道连接到`grep`。输出使用正则表达式来表示给定的上下文是否是递归的。例如，以下是 CentOS 7 安装中类型上下文为`httpd_sys_content_t`的所有目录:

```
[vagrant@centos ~]$ sudo semanage fcontext -l | grep "httpd_sys_content"/srv/([^/]*/)?www(/.*)?                            all files          system_u:object_r:httpd_sys_content_t:s0/var/www(/.*)?                                     all files          system_u:object_r:httpd_sys_content_t:s0/etc/htdig(/.*)?                                   all files          system_u:object_r:httpd_sys_content_t:s0/srv/gallery2(/.*)?                                all files          system_u:object_r:httpd_sys_content_t:s0/var/lib/trac(/.*)?                                all files          system_u:object_r:httpd_sys_content_t:s0/var/lib/htdig(/.*)?                               all files          system_u:object_r:httpd_sys_content_t:s0/var/www/icons(/.*)?                               all files          system_u:object_r:httpd_sys_content_t:s0/usr/share/glpi(/.*)?                              all files          system_u:object_r:httpd_sys_content_t:s0/usr/share/htdig(/.*)?                             all files          system_u:object_r:httpd_sys_content_t:s0/usr/share/drupal.*                                all files          system_u:object_r:httpd_sys_content_t:s0/usr/share/z-push(/.*)?                            all files          system_u:object_r:httpd_sys_content_t:s0/var/www/svn/conf(/.*)?                            all files          system_u:object_r:httpd_sys_content_t:s0/usr/share/icecast(/.*)?                           all files          system_u:object_r:httpd_sys_content_t:s0/var/lib/cacti/rra(/.*)?                           all files          system_u:object_r:httpd_sys_content_t:s0/usr/share/ntop/html(/.*)?                         all files          system_u:object_r:httpd_sys_content_t:s0/usr/share/doc/ghc/html(/.*)?                      all files          system_u:object_r:httpd_sys_content_t:s0/usr/share/openca/htdocs(/.*)?                     all files          system_u:object_r:httpd_sys_content_t:s0/usr/share/selinux-policy[^/]*/html(/.*)?          all files          system_u:object_r:httpd_sys_content_t:s0
```

## 改变上下文

如果我们愿意，我们可以改变某些目录的上下文。这可能是因为我们需要更改权限，或者因为我们在不同位置之间移动了一个文件——虽然在一个文件夹内创建的所有文件*都继承了上下文，但移动的文件保留了它们的原始上下文。假设我们将新的*index.html*文件移动到我们的`/var/www/html`目录中:*

```
[vagrant@centos ~]$ sudo mv index.html /var/www/html/[vagrant@centos ~]$ cd /var/www/html/[vagrant@centos html]$ ls -Z-rw-rw-r--. vagrant vagrant unconfined_u:object_r:user_home_t:s0 index.html
```

这个例子特别合适，因为我们可以在实践中看到 SELinux 的效果。如果我们试图通过网络浏览器查看我们的*index.html*文件，我们会收到一个*禁止*错误。这是因为，如上所示，它保留了它原来的`user_home_t`类型，而不是它需要的`httpd_sys_content_t`上下文。这可以用`restorecon`命令改变:

```
[vagrant@centos html]$ restorecon index.html[vagrant@centos html]$ ls -Z-rw-rw-r--. vagrant vagrant unconfined_u:object_r:httpd_sys_content_t:s0 index.html
```

使用 SELinux 的默认上下文来确保所有文件都是适当的类型。在这种情况下，它看到 index.html 的*是`/var/www(/.*)?`目录的一部分，并确保它继承了适当的上下文。或者，假设我们移动了整个`html/`目录，并需要改变 SELinux 上下文。假设，不管出于什么原因，我们的服务器没有 Apache 必需的缺省 SELinux 策略。为此，我们可以使用`semanage`来改变类型上下文:*

```
semanage fcontext -a -t httpd_sys_content_t '/var/www/html(/.*)?'
```

`-t`标志表示类型。另外，注意包含了`(/.*)?`——这告诉 SELinux 在`/var/www/html`目录下的文件和目录也继承了这种风格。如果需要，我们还可以删除目录的上下文:

```
semanage fcontext -d "/var/www/html(/.*)?"
```

即使通过管理 SELinux 上下文和权限，我们也只是触及了这个深入工具的表面。回来看看博客，了解更多关于 SELinux 的内容，或者去 LinuxAcademy.com 的 T2 了解更多关于 SELinux 和其他系统管理和安全主题的课程。