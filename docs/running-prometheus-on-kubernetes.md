# 在 Kubernetes |云专家上运行普罗米修斯

> 原文：<https://acloudguru.com/blog/engineering/running-prometheus-on-kubernetes>

你想知道如何让普罗米修斯运行在库伯内特？在很大程度上，与普罗米修斯和库伯内特一起工作非常容易。我们将使用一系列 YAML 文件来部署一切。

**在我们进入技术层面之前，我们有几个假设:**

1.  首先，您已经有了一个 Kubernetes 堆栈。这篇文章将不包括设置它。

2.第二，您已经为 Kubernetes 集群配置了端口`9090-9094`。否则，您可能需要更改 Prometheus 服务的目标端口。

## **创建监控名称空间**

我们将从创建监控名称空间开始。使用您选择的编辑器，创建`namespace.yml`并添加以下内容:

```
{  "kind": "Namespace",  "apiVersion": "v1",  "metadata": {    "name": "monitoring",    "labels": {      "name": "monitoring"    }  }}
```

名称空间在 Kubernetes 中充当虚拟集群。我们希望确保在监控名称空间中运行所有的 Prometheus pods 和服务。当您要列出您部署的任何东西时，您将需要使用`-n`标志并将`monitoring`定义为名称空间。例如，如果您想列出普罗米修斯舱，您需要执行以下操作:

```
kubectl get pods -n monitoring
```

**应用名称空间**

现在通过执行`kubectl apply`命令来应用名称空间:

```
kubectl apply -f namespace.yml
```

接下来我们将设置`clusterRole.yml`。这将用于设置群集的角色。我们需要对此进行设置，以便 Prometheus 拥有对 Kubernetes API 的正确权限。

创建`clusterRole.yml`文件，并向其中添加以下内容:

```
apiVersion: rbac.authorization.k8s.io/v1beta1kind: ClusterRolemetadata:  name: prometheusrules:- apiGroups: [""]  resources:  - nodes  - nodes/proxy  - services  - endpoints  - pods  verbs: ["get", "list", "watch"]- apiGroups:  - extensions  resources:  - ingresses  verbs: ["get", "list", "watch"]- nonResourceURLs: ["/metrics"]  verbs: ["get"]---apiVersion: rbac.authorization.k8s.io/v1beta1kind: ClusterRoleBindingmetadata:  name: prometheusroleRef:  apiGroup: rbac.authorization.k8s.io  kind: ClusterRole  name: prometheussubjects:- kind: ServiceAccount  name: default  namespace: monitoring
```

**应用集群角色**将集群角色应用到 Kubernetes 集群:

```
kubectl apply -f clusterRole.yml
```

我们将使用一个 ConfigMap 来将任何配置工件从图像内容中分离出来。这将有助于保持容器化应用程序的可移植性。我们将使用它来管理`prometheus.yml`配置文件。

创建`config-map.yml`并添加以下内容:

```
apiVersion: v1kind: ConfigMapmetadata:  name: prometheus-server-conf  labels:    name: prometheus-server-conf  namespace: monitoringdata:  prometheus.yml: |-    global:      scrape_interval: 5s      evaluation_interval: 5s    scrape_configs:      - job_name: 'kubernetes-apiservers'        kubernetes_sd_configs:        - role: endpoints        scheme: https        tls_config:          ca_file: /var/run/secrets/kubernetes.io/serviceaccount/ca.crt        bearer_token_file: /var/run/secrets/kubernetes.io/serviceaccount/token        relabel_configs:        - source_labels: [__meta_kubernetes_namespace, __meta_kubernetes_service_name, __meta_kubernetes_endpoint_port_name]          action: keep          regex: default;kubernetes;https      - job_name: 'kubernetes-nodes'        scheme: https        tls_config:          ca_file: /var/run/secrets/kubernetes.io/serviceaccount/ca.crt        bearer_token_file: /var/run/secrets/kubernetes.io/serviceaccount/token        kubernetes_sd_configs:        - role: node        relabel_configs:        - action: labelmap          regex: __meta_kubernetes_node_label_(.+)        - target_label: __address__          replacement: kubernetes.default.svc:443        - source_labels: [__meta_kubernetes_node_name]          regex: (.+)          target_label: __metrics_path__          replacement: /api/v1/nodes/${1}/proxy/metrics      - job_name: 'kubernetes-pods'        kubernetes_sd_configs:        - role: pod        relabel_configs:        - source_labels: [__meta_kubernetes_pod_annotation_prometheus_io_scrape]          action: keep          regex: true        - source_labels: [__meta_kubernetes_pod_annotation_prometheus_io_path]          action: replace          target_label: __metrics_path__          regex: (.+)        - source_labels: [__address__, __meta_kubernetes_pod_annotation_prometheus_io_port]          action: replace          regex: ([^:]+)(?::d+)?;(d+)          replacement: $1:$2          target_label: __address__        - action: labelmap          regex: __meta_kubernetes_pod_label_(.+)        - source_labels: [__meta_kubernetes_namespace]          action: replace          target_label: kubernetes_namespace        - source_labels: [__meta_kubernetes_pod_name]          action: replace          target_label: kubernetes_pod_name      - job_name: 'kubernetes-cadvisor'        scheme: https        tls_config:          ca_file: /var/run/secrets/kubernetes.io/serviceaccount/ca.crt        bearer_token_file: /var/run/secrets/kubernetes.io/serviceaccount/token        kubernetes_sd_configs:        - role: node        relabel_configs:        - action: labelmap          regex: __meta_kubernetes_node_label_(.+)        - target_label: __address__          replacement: kubernetes.default.svc:443        - source_labels: [__meta_kubernetes_node_name]          regex: (.+)          target_label: __metrics_path__          replacement: /api/v1/nodes/${1}/proxy/metrics/cadvisor      - job_name: 'kubernetes-service-endpoints'        kubernetes_sd_configs:        - role: endpoints        relabel_configs:        - source_labels: [__meta_kubernetes_service_annotation_prometheus_io_scrape]          action: keep          regex: true        - source_labels: [__meta_kubernetes_service_annotation_prometheus_io_scheme]          action: replace          target_label: __scheme__          regex: (https?)        - source_labels: [__meta_kubernetes_service_annotation_prometheus_io_path]          action: replace          target_label: __metrics_path__          regex: (.+)        - source_labels: [__address__, __meta_kubernetes_service_annotation_prometheus_io_port]          action: replace          target_label: __address__          regex: ([^:]+)(?::d+)?;(d+)          replacement: $1:$2        - action: labelmap          regex: __meta_kubernetes_service_label_(.+)        - source_labels: [__meta_kubernetes_namespace]          action: replace          target_label: kubernetes_namespace        - source_labels: [__meta_kubernetes_service_name]          action: replace          target_label: kubernetes_name
```

这份文件里有很多东西。简而言之，我们使用带有 Kubernetes API 的服务发现来创建 Prometheus 目标。这就是为什么我们需要更早地配置集群角色的原因。没有它，Prometheus 就没有必要的权限访问 API 来发现目标。

正在使用服务发现将以下作业配置为目标。

*   `kubernetes-apiservers`:获取 Kubernetes APIs 的指标。
*   `kubernetes-nodes`:获取 Kubernetes 节点上的指标。
*   `kubernetes-pods`:从在元数据中定义了 prometheus.io/scrape 和 prometheus.io/port 注释的 pod 中获取指标。
*   `kubernetes-cadvisor`:获取从 Kubernetes 集群报告的 cAdvisor 指标。
*   `kubernetes-service-endpoints`:从元数据中定义了`prometheus.io/scrape`和`prometheus.io/port`注释的服务中获取度量。

通过使用服务发现，我们不需要在新的 pods 和服务联机和脱机时用它们来更新`prometheus.conf`文件。只要在您的 pod 和服务的元数据中定义了`prometheus.io/scrape`和`prometheus.io/port`注释，Prometheus 就会自动更新目标。

**应用配置图**

现在应用配置图:

```
kubectl apply -f config-map.yml
```

现在配置图已经就绪，我们可以创建 Prometheus 部署和服务了。

创建`prometheus-deployment.yml`并添加以下内容:

```
apiVersion: extensions/v1beta1kind: Deploymentmetadata:  name: prometheus-deployment  namespace: monitoringspec:  replicas: 1  template:    metadata:      labels:        app: prometheus-server    spec:      containers:        - name: prometheus          image: prom/prometheus:v2.2.1          args:            - "--config.file=/etc/prometheus/prometheus.yml"            - "--storage.tsdb.path=/prometheus/"          ports:            - containerPort: 9090          volumeMounts:            - name: prometheus-config-volume              mountPath: /etc/prometheus/            - name: prometheus-storage-volume              mountPath: /prometheus/      volumes:        - name: prometheus-config-volume          configMap:            defaultMode: 420            name: prometheus-server-conf        - name: prometheus-storage-volume          emptyDir: {}---apiVersion: v1kind: Servicemetadata:  name: prometheus-service  namespace: monitoring  annotations:      prometheus.io/scrape: 'true'      prometheus.io/port:   '9090'spec:  selector:    app: prometheus-server  type: NodePort  ports:    - port: 8080      targetPort: 9090      nodePort: 30000
```

有几件事我想指出来。正在创建两个卷装载。

这些是`prometheus-config-volume`和`prometheus-storage-volume`。

```
...volumeMounts:            - name: prometheus-config-volume              mountPath: /etc/prometheus/            - name: prometheus-storage-volume              mountPath: /prometheus/...
```

`prometheus-config-volume`将使用我们的配置图来管理`prometheus.yml`，这反映在 volumes 部分中。

```
...- name: prometheus-config-volume         configMap:           defaultMode: 420           name: prometheus-server-conf...
```

这就是我们如何将`prometheus-server-conf`配置图用于 Prometheus 部署。

对于`prometheus-storage-volume`，我们正在创建一个空目录来存储普罗米修斯数据。

```
...- name: prometheus-storage-volume          emptyDir: {}...
```

这个卷是短暂的，随着 Pod 一起被创建和销毁。这意味着如果您出于任何原因删除 Pod，`prometheus-storage-volume`中的数据也会随之删除。如果您希望这些数据是持久的，那么您将需要使用一个持久卷。

现在让我们看看服务中定义的元数据。

```
metadata:  name: prometheus-service  namespace: monitoring  annotations:      prometheus.io/scrape: 'true'      prometheus.io/port:   '9090'
```

在这里，我们设置注释，以便普罗米修斯发现该服务，将其作为要清除的目标。要使服务可用，请将`prometheus.io/scrape`设置为`true`。然后，您需要确保`prometheus.io/port`是服务中定义的目标端口。如果不这样，目标就不会被发现。

```
ports:    - port: 8080      targetPort: 9090      nodePort: 30000
```

因为目标端口被设置为`9090`，我们将使用带有`prometheus.io/port`的端口。

```
annotations:      prometheus.io/scrape: 'true'      prometheus.io/port:   '9090'
```

通过执行`kubectl apply`创建部署和服务。

```
kubectl apply -f prometheus-deployment.yml
```

让我们验证 pod 和服务是否已创建。

```
kubectl get pods -n monitoringkubectl get services -n monitoring
```

一旦 pod 和服务可用，您就可以通过前往`https://<KUBERNETES_MASTER_IP>:9090`访问 Prometheus 的表情浏览器。现在，您可以监视部署到集群的 pod 和服务。

## **关于在 Kubernetes 上运行 Prometheus 的更多信息**

如果你想了解更多关于在 Kubernetes 上运行 Prometheus 的信息，可以去看看我的实践课程[用 Prometheus](https://acloudguru.com/course/monitoring-kubernetes-with-prometheus) 监控 Kubernetes。快乐监控！