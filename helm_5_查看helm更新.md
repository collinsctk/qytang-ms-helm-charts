### 查看helm更新
```shell
[root@AIOps qytang-microservice]# helm repo update
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "qytang" chart repository
Update Complete. ⎈Happy Helming!⎈
[root@AIOps qytang-microservice]# helm search repo qytang/qytang-microservice
NAME                            CHART VERSION   APP VERSION     DESCRIPTION
qytang/qytang-microservice      0.1.3           1.16.3          A Helm chart for Kubernetes

```