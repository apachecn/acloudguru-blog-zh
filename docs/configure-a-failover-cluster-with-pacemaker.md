# 使用 Pacemaker |云专家配置故障转移集群

> 原文：<https://acloudguru.com/blog/engineering/configure-a-failover-cluster-with-pacemaker>

*高可用性*是 IT 行业的一个主要术语，这有几个原因。随着越来越多的企业通过互联网提供服务，对这些服务始终可访问的需求也在增长。你必须去实体店面购买商品和服务的日子已经一去不复返了。现在，在白天或晚上的任何时候，你都可以购买食物、衣服、娱乐或任何你能想到的东西，并把它们送到你家门口或在媒体设备上消费。这就是高可用性 T4 的用武之地。确保您的服务保持高可用性是在现代市场中取得成功的关键。在本教程中，我们将在两台 CentOS 7 服务器上安装 Pacemaker 集群，并对其进行配置，以确保我们的服务保持高可用性。

## 安装起搏器集群

Pacemaker 是一个高可用性集群资源管理器(CRM ),可用于管理资源，并确保在发生节点故障时资源仍然可用。 首先，我们需要安装 Pacemaker 包和 pcs 命令行工具。在两个节点上，运行:

```
sudo yum install -y pacemaker pcs
```

在两个节点上运行`firewall-cmd`命令，允许 Pacemaker 的流量(TCP 端口 2224、3121、21064 和 UDP 端口 5405):

```
sudo firewall-cmd --permanent --add-service=high-availability sudo firewall-cmd --reload
```

启动并启用 pcsd 服务。同样，在两个节点上运行这些命令:

```
sudo systemctl start pcsd.servicesudo systemctl enable pcsd.service
```

再次在两个节点上为`hacluster`用户设置密码，该密码是在软件包安装期间创建的。该用户将用于向其他集群节点进行身份验证，并在集群上执行操作:

```
sudo passwd hacluster
```

在`node1`日，认证为`hacluster`用户:

```
sudo pcs cluster auth NODE1 NODE2
```

在`node1` : 生成并同步 corosync 配置

```
sudo pcs cluster setup --name cluster_name NODE1 NODE2 
```

在`node1` 上启动集群:

```
sudo pcs cluster start --all
```

## 配置群集资源

现在集群已经启动并运行，我们可以创建我们的集群资源了。首先，我们将创建一个 IP 地址资源，然后创建一个 Apache HTTP 服务器资源。一旦创建了资源，我们就可以设置资源约束来确保 IP 地址总是在 Apache HTTP 服务器之前开始，并且两个资源总是在同一个节点上一起运行。 添加一个 IP 地址资源到`node1` : 上的集群

```
sudo pcs resource create cluster_ip ocf:heartbeat:IPaddr2 ip=192.168.1.100 cidr_netmask=24 op monitor interval=30s
```

在两个节点上安装 Apache HTTP 服务器，打开防火墙的 HTTP 端口:

```
sudo yum install -y httpd sudo firewall-cmd --permanent --add-service=http sudo firewall-cmd --reload
```

在两个节点上，启用状态 URL 进行健康监控:

```
sudo cat > /var/www/html/index.html <<EOF SetHandler server-status Require local EOF
```

将 Apache HTTP 服务器资源添加到`node1` : 上的集群中

```
sudo pcs resource create apache ocf:heartbeat:apache configfile=/etc/httpd/conf/httpd.conf statusurl="https://localhost/server-status" op monitor interval=1min
```

对`node1`设置一个托管约束，保证集群资源运行在同一个节点上:

```
sudo pcs constraint colocation add apache with cluster_ip INFINITY
```

同样，在`node1`上，设置一个顺序约束，以确保集群资源以正确的顺序启动:

```
sudo pcs constraint order cluster_ip then apache
```

验证`node1` : 的资源约束

```
sudo pcs constraint
```

在`node1` : 上验证集群资源的状态

```
sudo pcs status
```

* * *

现在，我们已经使用 Pacemaker 成功配置了故障转移集群！如果一个节点出现故障，资源将自动转移到群集中的一个工作节点。

## 想了解更多？

如果你喜欢这个简短的教程，并想了解关于 Pacemaker 的更多信息，请查看我的 [*LPIC-3 304 虚拟化和高可用性*](https://linuxacademy.com/linux/training/course/name/linux-academys-lpic-3-304-virtualization-and-high-availability-preparation-course) 预备课程。本课程涵盖 Pacemaker，以及其他几种支持高可用性和虚拟化的技术和服务。