### 创建github仓库(需要是公开的项目)
```shell
https://github.com/collinsctk/qytang-ms-helm-charts

```

### 创建令牌,并记录令牌
```shell
https://github.com/settings/tokens

```

### 初始化Git仓库并添加远程仓库
```shell
git init
git remote add origin https://github.com/collinsctk/qytang-ms-helm-charts.git

```


### 将当前 Helm Chart 添加到仓库
```shell
git add .
git commit -m "Add qytang-microservice Helm Chart"

[root@AIOps qytang-microservice]# git push -u origin main
Username for 'https://github.com': collinsctk@qytang.com
Password for 'https://collinsctk@qytang.com@github.com': <第二步申请的令牌>
Enumerating objects: 29, done.
Counting objects: 100% (29/29), done.
Delta compression using up to 16 threads
Compressing objects: 100% (26/26), done.
Writing objects: 100% (29/29), 9.81 KiB | 4.91 MiB/s, done.
Total 29 (delta 13), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (13/13), done.
To https://github.com/collinsctk/qytang-ms-helm-charts.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.

```

### 保存认证信息
```shell
git config --global credential.helper cache
git config --global credential.helper store

```

### 创建gh-pages分支
```shell
git checkout --orphan gh-pages
git rm -rf .
helm package /qytang-aliyun/aliyun_7_k8s/helm/qytang-microservice/
helm repo index . --url https://collinsctk.github.io/qytang-ms-helm-charts/
echo "<h1>qytang-microservice Helm Chart</h1>" > index.html
git add index.html
git add qytang-microservice-0.1.0.tgz 
git add index.yaml
git commit -m "Initialize gh-pages"
git push origin gh-pages

```

### 使用github上的helm仓库并安装
```shell
helm repo add my-charts https://您的用户名.github.io/helm-charts/
helm repo update
helm search repo qytang/qytang-microservice

kubectl create namespace qytang-ns
kubectl label namespace qytang-ns app.kubernetes.io/managed-by=Helm
kubectl annotate namespace qytang-ns meta.helm.sh/release-name=qytang-ms
kubectl annotate namespace qytang-ns meta.helm.sh/release-namespace=qytang-ns
 
helm install qytang-ms qytang-microservice/ --namespace qytang-ns
```
