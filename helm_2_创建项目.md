### 创建项目
```shell
[root@AIOps helm]# helm create my-microservice
Creating my-microservice
[root@AIOps helm]# tree my-microservice/
my-microservice/
├── charts
├── Chart.yaml
├── templates
│   ├── deployment.yaml
│   ├── _helpers.tpl
│   ├── hpa.yaml
│   ├── ingress.yaml
│   ├── NOTES.txt
│   ├── serviceaccount.yaml
│   ├── service.yaml
│   └── tests
│       └── test-connection.yaml
└── values.yaml

3 directories, 10 files

```