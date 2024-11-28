### 安装
```shell
[root@AIOps helm]# wget https://get.helm.sh/helm-v3.15.4-linux-amd64.tar.gz

[root@AIOps helm]# tar -zxvf helm-v3.15.4-linux-amd64.tar.gz

[root@AIOps helm]# helm version
WARNING: Kubernetes configuration file is group-readable. This is insecure. Location: /root/.kube/config
WARNING: Kubernetes configuration file is world-readable. This is insecure. Location: /root/.kube/config
version.BuildInfo{Version:"v3.15.4", GitCommit:"fa9efb07d9d8debbb4306d72af76a383895aa8c4", GitTreeState:"clean", GoVersion:"go1.22.6"}
[root@AIOps helm]#

~~~处理一下权限~~~~
[root@AIOps helm]# chmod 600 /root/.kube/config

```