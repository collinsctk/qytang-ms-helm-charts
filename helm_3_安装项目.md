### 基本检查
```shell
[root@AIOps helm]# helm lint qytang-microservice/
==> Linting qytang-microservice/

1 chart(s) linted, 0 chart(s) failed

```

### 查看helm
```shell
[root@AIOps helm]# helm list --all-namespaces
NAME                            NAMESPACE       REVISION        UPDATED                                 STATUS          CHART                                APP VERSION
ack-node-problem-detector       kube-system     1               2024-11-28 00:58:14.540029378 +0000 UTC deployed        ack-node-problem-detector-1.2.20     0.8.0
ack-pod-identity-webhook        kube-system     1               2024-11-28 02:29:16.649583036 +0000 UTC deployed        ack-pod-identity-webhook-0.1.1       0.1.1
arms-prometheus                 arms-prom       1               2024-11-28 00:58:12.336277439 +0000 UTC deployed        ack-arms-prometheus-1.1.27           4.2.2
gateway-api                     kube-system     1               2024-11-28 00:57:18.212759599 +0000 UTC deployed        gateway-api-1.1.0                    v1.1.0

[root@AIOps helm]# helm list --namespace kube-system
NAME                            NAMESPACE       REVISION        UPDATED                                 STATUS          CHART                                APP VERSION
ack-node-problem-detector       kube-system     1               2024-11-28 00:58:14.540029378 +0000 UTC deployed        ack-node-problem-detector-1.2.20     0.8.0
ack-pod-identity-webhook        kube-system     1               2024-11-28 02:29:16.649583036 +0000 UTC deployed        ack-pod-identity-webhook-0.1.1       0.1.1
gateway-api                     kube-system     1               2024-11-28 00:57:18.212759599 +0000 UTC deployed        gateway-api-1.1.0                    v1.1.0

```

### 创建命名空间
```
kubectl create namespace qytang-ns
kubectl label namespace qytang-ns app.kubernetes.io/managed-by=Helm
kubectl annotate namespace qytang-ns meta.helm.sh/release-name=qytang-ms
kubectl annotate namespace qytang-ns meta.helm.sh/release-namespace=qytang-ns
```

### helm install
```shell
[root@AIOps helm]# helm install qytang-ms qytang-microservice/ --namespace qytang-ns
NAME: qytang-ms
LAST DEPLOYED: Thu Nov 28 17:21:05 2024
NAMESPACE: qytang-ns
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
Thank you for installing qytang-microservice.

Your release is named qytang-ms.

To learn more about the release, try:

  $ helm status qytang-ms
  $ helm get all qytang-ms

```

### 查看状态
```shell
[root@AIOps helm]# helm status qytang-ms --namespace qytang-ns
NAME: qytang-ms
LAST DEPLOYED: Thu Nov 28 17:21:05 2024
NAMESPACE: qytang-ns
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
Thank you for installing qytang-microservice.

Your release is named qytang-ms.

To learn more about the release, try:

  $ helm status qytang-ms
  $ helm get all qytang-ms
  
[root@AIOps helm]# helm get all qytang-ms --namespace qytang-ns
NAME: qytang-ms
LAST DEPLOYED: Thu Nov 28 17:21:05 2024
NAMESPACE: qytang-ns
STATUS: deployed
REVISION: 1
CHART: qytang-microservice
VERSION: 0.1.0
APP_VERSION: 1.16.0
TEST SUITE: None
USER-SUPPLIED VALUES:
null
~~~大量详细内容~~~~

```


### 查看helm
```shell
[root@AIOps helm]# helm list --all-namespaces
NAME                            NAMESPACE       REVISION        UPDATED                                 STATUS          CHART                                APP VERSION
ack-node-problem-detector       kube-system     1               2024-11-28 00:58:14.540029378 +0000 UTC deployed        ack-node-problem-detector-1.2.20     0.8.0
ack-pod-identity-webhook        kube-system     1               2024-11-28 02:29:16.649583036 +0000 UTC deployed        ack-pod-identity-webhook-0.1.1       0.1.1
arms-prometheus                 arms-prom       1               2024-11-28 00:58:12.336277439 +0000 UTC deployed        ack-arms-prometheus-1.1.27           4.2.2
gateway-api                     kube-system     1               2024-11-28 00:57:18.212759599 +0000 UTC deployed        gateway-api-1.1.0                    v1.1.0
qytang-ms                       qytang-ns       1               2024-11-28 17:21:05.276405606 +0800 CST deployed        qytang-microservice-0.1.0            1.16.0

```

### uninstall
```shell
[root@AIOps helm]# helm uninstall qytang-ms --namespace qytang-ns
release "qytang-ms" uninstalled

~~~ns也会被删除~~~
[root@AIOps helm]# kubectl get ns
NAME              STATUS   AGE
ack-csi-fuse      Active   8h
arms-prom         Active   8h
default           Active   8h
kube-node-lease   Active   8h
kube-public       Active   8h
kube-system       Active   8h


```
