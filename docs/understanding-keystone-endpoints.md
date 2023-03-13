# 了解 Keystone 端点

> 原文：<https://acloudguru.com/blog/engineering/understanding-keystone-endpoints>

**(OpenStacks 身份服务)**

> OpenStack Identity (Keystone)提供了一个用户中心目录，这些用户映射到他们可以访问的 OpenStack 服务。它作为云操作系统中的通用认证系统，可以与现有的后端目录服务集成，如 [LDAP](https://en.wikipedia.org/wiki/LDAP "LDAP") 。它支持多种形式的认证，包括标准用户名和密码凭证、基于令牌的系统和 AWS 风格(即[亚马逊网络服务](https://en.wikipedia.org/wiki/Amazon_Web_Services "Amazon"))登录。此外，该目录在单个注册表中提供了部署在 OpenStack 云中的所有服务的可查询列表。用户和第三方工具可以通过编程来确定他们可以访问哪些资源。https://en . Wikipedia . org/wiki/open stack # Identity _ Service _ . 28 keystone . 29

在 OpenStack 中，在我们开始利用庞大的服务和应用生态系统之前，我们首先必须授权我们的用户。使用 OpenStack Identity (keystone)时，我们需要理解一些非常重要的术语。我想花一点时间来解决今天在 keystone 中设置端点时最大的困惑之一。首先让我们从定义什么是端点开始。keystone 中的**端点**只是一个 URL，可以用来访问 OpenStack 中的服务。一个**端点**就像是你(**用户**)使用 OpenStack **服务**的一个接触点。 *adminurl* (我们将在下面进一步展示)是为管理用户准备的，而 *internalurl* 是其他**服务**用来相互交流的。而 *publicurl* 是其他每个访问服务端点的人使用的。让我们理解以下术语:服务是任何 OpenStack 服务，比如 Nova、Swift，甚至 keystone 本身。**角色**是用户拥有的授权级别。**令牌**是一个字母数字字符串，允许我们根据其访问级别或**(参见上述角色)**访问服务。用户就是将要访问服务的人。传统上，这也可以用作服务本身使用的(服务帐户)。而最后**租户**真的只是一群用户。(第 1 部分)1)首先，我们需要实际创建两个**租户**，我们将简单地将它们命名为*管理员*(这将是管理员**租户**记住租户只是一组**用户**)另一个**租户**将被称为*服务*(这是服务组，即:我们服务的租户..在我们的例子中，我们使用 nova **服务**。

```
$ keystone tenant-create --name=admin --description="Admin Tenant"$ keystone tenant-create --name=service --description="Service Tenant"
```

2)现在我们需要使用密码 *linuxacademy123* 创建名为 *admin* 的管理用户

```
# keystone user-create --name=admin --pass=*linuxacademy123*   --email=*admin@linuxacedmy123*
```

**3)我们现在需要为 OpenStack 中名为 *admin 的管理任务创建一个新的**角色**。*这个默认的*管理*策略允许访问大多数服务。**

```
# keystone role-create --name=admin
```

**4)我们必须为**用户添加**角色**。**用户总是使用**租户**登录，并且**角色**被分配给这些**租户内的**用户**。**在这里，当使用*管理员**租户登录时，我们将把*管理员* **角色**添加到*管理员* **用户**中。*****

```
# keystone user-role-add --user=admin --tenant=admin --role=admin
```

**(第 2 部分)在下面的例子中，我们将创建一个 Nova **用户**，然后将它链接到我们的**租户**，称为*服务*，然后将它链接到我们的*管理员* **角色**。然后，我们将创建实际的计算(nova) **服务**。最后，我们将使用新创建的 nova **服务**返回的 ID 值来创建我们的**端点**。5)创建一个名为 *nova 的用户。*我们将把我们的密码定义为 *linuxacademy123。***

```
$ keystone user-create --name nova --pass *linuxacademy123*+----------+----------------------------------+| Property |              Value               |+----------+----------------------------------+|  email   |                                  || enabled  |               True               ||    id    | f1a06c73141a441da5df57c46c3b69c5 ||   name   |               nova               || username |               nova               |+----------+----------------------------------+
```

**6)现在，我们将把这个新用户 *nova* 链接到我们在第 1 部分中创建的*服务*租户，以及我们也命名为 *admin 的**角色**。***

```
$ keystone user-role-add --user nova --tenant service --role admin
```

**7)现在是时候创建我们实际的**服务**了，它将被称为 nova，其中它的**服务**的类型是 NOVA 计算服务。**

```
$ keystone service-create --name nova --type compute  --description "OpenStack Compute"+-------------+----------------------------------+|   Property  |              Value               |+-------------+----------------------------------+| description |        OpenStack Compute         ||   enabled   |               True               ||      id     | 5844875f25c54e52a0d5c7f6076bff86 ||     name    |               nova               ||     type    |             compute              |+-------------+----------------------------------+
```

**8)我们现在已经到了设置的实际部分，为 nova 计算**服务**创建实际的**端点**。但是首先，我认为提到一个我在用户创建这些端点时遵循 OpenStacks 文档时看到的常见错误是非常重要的。大多数文档使用以下内容作为示例:**

```
$ keystone endpoint-create  --service-id $(keystone service-list | awk '/ compute / {print $2}')  --publicurl https://*controller*:8774/v2/%(tenant_id)s  --internalurl https://*controller*:8774/v2/%(tenant_id)s  --adminurl https://*controller*:8774/v2/%(tenant_id)s  --region regionOne+-------------+-----------------------------------------+|   Property  |                  Value                  |+-------------+-----------------------------------------+|   adminurl  | https://controller:8774/v2/%(tenant_id)s ||      id     |    c397438bd82c41198ec1a9d85cb7cc74     || internalurl | https://controller:8774/v2/%(tenant_id)s ||  publicurl  | https://controller:8774/v2/%(tenant_id)s ||    region   |                regionOne                ||  service_id |    6c7854f52ce84db795557ebc0373f6b9     |+-------------+-----------------------------------------+
```

**让我们一行一行地过一遍。在第一行中，我们使用 endpoint-create 命令开始创建端点。在第二行中，我们使用–service-id 返回 nova 服务的服务 id，我们使用该服务创建实际的 URL 身份验证端点。然而，几乎所有较新版本的 OpenStack 文档都使用下面的搜索字符串，我们在第二行也看到了:$(keystone service-list | awk '/compute/{ print $ 2 } ')简而言之，上面的字符串在$()中打开了一个后台子 shell。在()中，我们使用一种称为 awk 的 shell 脚本语言运行实际的搜索字符串。首先，它调用 keystone 命令 *keystone service-list* ，该命令在行和列中列出了所有可用的服务，包括名称、实际服务 id、描述等。然后，我们使用搜索字符串/ compute /将它输出|,因为我们希望使用该行来提取 nova compute 的服务 id。{print $2}正在从该行中提取第二列(2 ),该列恰好是服务计算服务的 id。第一行是|字符。例如，如果我们执行以下命令:keystone service-list，那么我们将会看到:+———————————————————————————————| id | name | type | description |+—————————————————————————————+ ———————————————————————————- 9b 1737 a 7632241 CD 8 b 38 ba 6 f 141 bb FFE 是服务 ID 本身:5844875 f 25 c 54 e 52 a 0 D5 c7f 6076 BFF 86 虽然这是按顺序设置所有服务并遵循设置指南时快速完成的一个很好的方法，但如果您以不同的顺序设置服务，这有时会导致问题。 因此，我建议在使用 *keystone endpoint-create* 设置端点时，手动使用服务 id，而不是通过执行以下操作来搜索服务 id:**

```
$ keystone endpoint-create  --service-id=5844875f25c54e52a0d5c7f6076bff86  --publicurl=https://*controller*:8774/v2/%(tenant_id)s  --internalurl=https://*controller*:8774/v2/%(tenant_id)s  --adminurl=https://*controller*:8774/v2/%(tenant_id)s  --region=regionOne
```

**最后，我想提一下–region 标志，它指定了您所在地区的名称。另一件使端点不能工作的事情是，当你没有使用这个标志时，它有时会为你创建一个不存在的区域名，或者这个区域名的大小写看起来也不同。例如，regionOne、RegionOne 和 regionone 都是不同的地区，因为名称的大小写很重要。我希望这篇文章能帮助你们中的一些人，他们遇到了我经常看到的这个问题。不熟悉 OpenStack？在[https://linuxacademy.com/openstack](https://linuxacademy.com/openstack "https://linuxacademy.com/openstack")查看 LinuxAcademy.com open stack 课程，并在未来经常回来查看更多课程！**