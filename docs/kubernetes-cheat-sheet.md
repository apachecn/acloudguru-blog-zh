# Kubectl 备忘单- Kubernetes 命令|云专家

> 原文：<https://acloudguru.com/blog/engineering/kubernetes-cheat-sheet>

如果你像我一样，你可能会有这样的时刻，你在终端前，双手在键盘上徘徊，然后…什么都没有。我似乎总是僵住，可能太依赖于 [bash 历史](https://acloudguru.com/blog/engineering/tutorial-the-best-tips-tricks-for-bash-explained)。(向上的箭头是我的朋友。)

在学习 Kubernetes 的时候，我最终在我的显示器上贴了 14 或 15 个便利贴来帮助我——但过了一段时间，我几乎看不清屏幕上的内容。所以最后，我写了一张小而易读的纸，当我或者你陷入困境时可以参考。

但首先，让我们花点时间来建立一些基础知识。

### What is Kubernetes?

Kubernetes 是一个管理容器化工作负载的平台。Kubernetes 协调计算、
网络和存储，以提供跨基础设施提供商的无缝可移植性。迷茫？查看[Kubernetes](https://acloudguru.com/course/introduction-to-kubernetes)简介，我们的 Kubernetes 101 速成课程包含你需要知道的所有基础知识。

### What is Kubectl?

kubectl 是 Kubernetes 命令行工具。它允许我们对 Kubernetes 集群运行命令——部署应用程序、检查和管理集群资源以及查看日志。

### Kubernetes 学习资源

## 忽必烈中的忽必烈命令

这个 Kubernetes 备忘单旨在让您开始在 Kubernetes 中执行 Kubectl 命令，并为您提供所有基本命令。(查看下面的可下载资产！)

**命令结果**这个备忘单上的一些命令可能不会返回任何结果，但是不用担心！下面是一些你可以创建的资源，然后快速转身运行你的备忘单中的命令来改变你的资源。先说豆荚。

### 基本 busybox pod 的 YAML

```
apiVersion: v1kind: Podmetadata:name: busyboxspec:containers:- image: busybox:1.28.4command:- sleep- "3600"name: busyboxrestartPolicy: Always
```

[**在这里了解更多关于 YAML 的信息。**](https://acloudguru.com/blog/engineering/learn-the-yaml-basics) 用此命令创建 pod:

```
kubectl create -f busybox.yaml
```

使用此命令创建部署:

```
kubectl run nginx --image=nginx
```

使用此命令从上面的部署创建服务:

```
kubectl expose deployment nginx --port=80 --type=NodePort
```

以下是使用节点本地存储的简单持久性卷的 YAML:

```
apiVersion: v1kind: PersistentVolumemetadata:name: data-pvnamespace: webspec:storageClassName: local-storagecapacity:storage: 1GiaccessModes:- ReadWriteOncehostPath:path: /mnt/data
```

使用以下命令创建永久卷:

```
kubectl apply -f my-pv.yaml
```

以下是简单配置图的 YAML:

```
apiVersion: v1kind: ConfigMapmetadata:name: my-config-mapdata:myKey: myValueanotherKey: anotherValue
```

使用以下命令创建配置映射:

```
kubectl apply -f configmap.yaml
```

下面是 YAML 的一个秘密:

```
apiVersion: v1kind: Secretmetadata:name: my-secretstringData:myKey: myPassword
```

使用此命令创建密码:

```
kubectl apply -f secret.yaml
```

以下是服务帐户的 YAML:

```
apiVersion: v1kind: ServiceAccountmetadata:name: acrnamespace: defaultsecrets:- name: acr
```

使用此命令创建服务帐户:

```
kubectl apply -f serviceaccount.yaml
```

## **立即下载！**

这应该足以让你开始！我还创建了这个 PDF 供您下载，并放在旁边供您参考！如果您喜欢这些练习并遵循这些命令，请查看我们的[云原生认证 Kubernetes 管理员(CKA)](https://acloudguru.com/course/cloud-native-certified-kubernetes-administrator-cka-legacy) 课程，深入了解 Kubernetes！

### 想要更多云技术的好处吗？看看这些:

* * *

## 掌握最受欢迎的技能

通过 ACG 的课程、实验室、学习路径和[沙盒软件](https://acloudguru.com/platform/cloud-sandbox-playgrounds)学习按需云技能。查看 [ACG 目前的免费课程](https://acloudguru.com/blog/news/whats-free-at-acg)或[立即开始](https://acloudguru.com/pricing)免费试用。

* * *

## 库柏切叶刀

### 查看资源信息

#### 节点

| $ kubectl get no |
| $ kubectl get no -o wide |
| $ kubectl describe no |
| $ kubectl get no -o yaml |
| $ ku bectl get node–select or =[label _ name] |
| $ kubectl get nodes -o jsonpath='{。items[*].status.addresses[？(@.type=="ExternalIP")]。地址} ' |
| $ kubectl top node [node_name] |

#### 分离舱

| $ kubectl 获取采购订单 |
| $ kubectl 获得 po -o wide |
| $ kubectl 描述采购订单 |
| $ kubectl 获取采购订单-显示-标签 |
| -= ytet-伊甸园字幕组=-翻译:粒粒粒尘紫月猫姐 scenery 校对:阿衡时间轴:邦德猪 |
| $ kubectl get po -o yaml |
| $ ku bect l get pod[pod _ name]-o YAML–export |
| $ ku bect l get pod[pod _ name]-o YAML–export > nameoffile . YAML |
| $ ku bectl get pods–字段选择器状态。phase =正在运行 |

#### Namespaces

| $ kubectl get ns |
| $ kubectl get ns -o yaml |
| $ kubectl 描述 ns |

#### 部署

| $ kubectl 获得部署 |
| $ kubectl 描述部署 |
| $ kubectl 得到广泛部署 |
| $ kubectl get deploy -o yam |

#### 服务

| $ kubectl 获取服务 |
| $ kubectl 描述 svc |
| $ kubectl 获得 svc -o 范围 |
| 库布特雷得到 svc 或 yaml |
| $ ku bectl get SVC–显示-标签 |

#### 达蒙塞特

| $ kubectl 获取 ds |
| $ ku bectl get ds–所有名称空间 |
| $ ku bectl describe ds[daemon set _ name]-n[namespace _ name] |
| $ ku bectl get ds[ds _ name]-n[ns _ name]-o YAML |

#### 事件

| $ kubectl 获取事件 |
| $ kubectl 获取事件-n kube-system |
| $ kubectl 获取事件-w |

#### 日志

| $ kubectl logs [pod_name] |
| $ ku bectl logs–since = 1h[pod _ name] |
| $ ku bectl logs–tail = 20[pod _ name] |
| $ ku bectl logs-f-c[容器名称] [pod 名称] |
| $ kubectl logs [pod_name] > pod.log |

#### 服务帐户

| $ kubectl 获取 sa |
| 库布特雷得到了 sa -o yaml |
| $ ku bectl get service accounts default-o YAML >。/sa.yaml |
| $ kubectl 替换 serviceaccount 默认值-f. /sa.yaml |

#### 复制集

| $ kubectl 获取 rs |
| $ kubectl 描述 rs |
| $ kubectl 获得 rs -o 宽度 |
| 库布特雷得到了 rs -o yaml |

#### 角色(Roles)

| $ kubectl 获取角色-所有-名称空间 |
| $ ku bectl get roles–all-namespaces-o YAML |

#### -秘密

| 忽必烈得到秘密 |
| $ ku bectl get secrets–所有名称空间 |
| $ kubectl 获取秘密-o yaml |

#### ConfigMaps(配置映射)

| 立方英尺 |
| $ ku bectl get cm–所有名称空间 |
| $ ku bectl get cm–all-namespaces-o YAML |

#### 进入

| $ kubectl get ing |
| $ ku bectl get ing–所有名称空间 |

#### 持久卷

| $ kubectl 获取 pv |
| $ kubectl 描述 pv |

#### PersistentVolumeClaim

| 卡布拉尔得到 pvc |
| $ kubectl 描述 pvc |

#### 存储类

| $ kubectl 获取 sc |
| $ kubectl 获取 sc -o yaml |

#### 多重资源

| 卡布拉尔得到 svc，po |
| $ kubectl 获得部署，否 |
| $ kubectl get all |
| $ kubectl 获取所有名称空间 |

### 更改资源属性

#### 污点

| $ kubectl 污点[节点名][污点名] |

#### 标签

| $ kubectl label [node_name] disktype=ssd |
| $ kubrectl label[pod _ name]env = prod |

#### 警戒线/非警戒线

| $ kubectl cordon [node_name] |
| $ kubi con sol[node _ name] |

#### 流干

| $ kubectl drain [node_name] |

#### 节点/单元

| $ kubectl delete node [node_name] |
| $多维数据集删除在[sub _ name]之下 |
| $ kubectl edit node [node_name] |
| $多维数据集编辑下[subname] |

#### 部署/名称空间

| $ kubectl 编辑部署[部署名称] |
| $ kubectl 删除部署[部署名称] |
| $ ku bectl expose deploy[depl oy _ name]–port = 80–type = node port |
| $ ku bectl scale deploy[deploy _ name]–副本数=5 |
| $ kubectl delete ns |
| $ kubectl edit ns [ns_name] |

#### 服务

| $ kubectl 编辑服务[服务名称] |
| $ kubectl 删除服务提供商[服务提供商名称] |

#### 达蒙塞特

| $ kubectl edit ds [ds_name] -n kube-system |
| $ kubectl delete ds [ds_name] |

#### 服务帐户

| $ kubectl edit sa [sa_name] |
| $ kubectl delete sa [sa_name] |

#### 给…作注解

| $ kubectl annotate po [pod_name] [annotation] |
| $ kubectl annotate no [node_name] |

### 添加资源

#### 创建 Pod

| $ ku bectl create-f[文件名] |
| $ ku bectl apply-f[文件名] |
| $ ku bectl run[pod _ name]–image = ngi NX–restart = Never |
| $ ku bectl run[pod _ name]–generator = run-pod/v1–image = nginx |
| $ ku bectl run[pod _ name]–image = nginx–restart = Never |

#### 创建服务

| $ kubectl 创建 svc 节点端口[SVC _ name]–TCP = 8080:80 |

#### 创建部署

| $ ku bectl create-f[文件名] |
| $ ku bectl apply-f[文件名] |
| $ ku bectl create deploy[deploy _ name]–image = ngi NX |

#### 交互式 Pod

| $ ku bectl run[pod _ name]–image = busybox–RM-it–restart = Never—sh |

#### 输出 YAMLto 文件

| $ ku bectl create deploy[deploy _ name]–image = ngi NX–dry-run-o YAML > deploy . YAML |
| $多维数据集获取 po[pod _ name]-o YAML-导出> |

#### 获得帮助

| $ kubectl -h |
| $ kubectl create -h |
| $ kubectl run -h |
| $ kubectl 解释 deploy.spec |

### 要求

#### API 调用

| $ ku bectl get–raw/API/metrics . k8s . io/ |

#### 集群信息

| $ kubectl 配置 |
| $ kubectl 集群信息 |
| $ kubectl 获取组件状态 |