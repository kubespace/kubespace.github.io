# KubeSpace

KubeSpace是一个DevOps以及Kubernetes多集群管理平台。KubeSpace可以兼容不同云厂商的Kubernetes集群，极大的方便了集群的管理工作。

KubeSpace平台当前包括如下功能：

1. 集群管理：Kubernetes集群原生资源的管理；
2. 工作空间：以环境（测试、生产等）以及应用为视角的工作空间管理；
3. 流水线：通过多种任务插件支持CICD，快速发布代码并部署到不同的工作空间；
4. 应用商店：内置丰富的中间件（mysql、redis等），以及支持导入发布自定义应用；
5. 平台配置：密钥、镜像仓库管理，以及不同模块的权限管理。

### 安装

通过[helm](https://helm.sh/docs/intro/install/)安装kubespace，执行如下命令：
```
helm repo add kubespace https://kubespace.cn/charts
helm install kubespace -n kubespace kubespace/kubespace --create-namespace
```

安装之后，查看所有Pod是否运行正常：
```
kubectl get pods -n kubespace -owide -w
```

当所有Pod运行正常后，通过如下命令查看浏览器访问地址：
```
export NODE_PORT=$(kubectl get -n kubespace -o jsonpath="{.spec.ports[0].nodePort}" services kubespace)
export NODE_IP=$(kubectl get nodes -o jsonpath="{.items[0].status.addresses[0].address}")
echo http://$NODE_IP:$NODE_PORT
```

### 升级

通过[helm](https://helm.sh/docs/intro/install/)升级kubespace，执行如下命令：
```
helm repo update
helm upgrade -n kubespace kubespace kubespace/kubespace
```

### 交流讨论

如果您在使用过程中，有任何问题、建议或功能需求，欢迎随时跟我们交流。

可以使用QQ扫描下面二维码，加入我们的QQ交流群。

<img src="images/qq-qrcode.png" alt="image-20220504114207452" style="zoom:30%;" />
