# nacos

nacos k8s部署

## 执行步骤

1. 修改 docker 仓库密文中配置
2. 修改 nacos config 及 service中配置
3. 有选择执行下面步骤

### 导入mysql库及建表语句 

```SHELL
mysql -udevops -p < deploy/db/mysql-schema.sql
```

### 创建 K8S namespace

```SHELL
kubectl create namespace dawn-system
```

### 创建 K8S docker 仓库密文

```SHELL
kubectl create secret docker-registry harbor --docker-server=<your-registry-server> --docker-username=<your-name> --docker-password=<your-pword> --docker-email=<your-email>
```

### 创建 K8S nacos 数据库配置

```SHELL
kubectl apply -f deploy/nacos-config.yaml
```

### 创建 K8S nacos 服务

```SHELL
kubectl apply -f deploy/nacos-service.yaml
```

### 创建 K8S nacos 有状态服务

```SHELL
kubectl apply -f deploy/nacos-statefulset.yaml
```