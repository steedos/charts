# charts
Helm charts for steedos platform

### 安装 steedos-community

1、cd steedos-community

2、helm install -n namespace steedos-community ./steedos-community-0.1.0.tgz

### 修改环境变量

cd steedos-community/2.2

vi values.yaml

```yaml
services:
  steedos:
    config:
      root_url: "http://localhost:3000"
      store: "local"
      folder: "/app/storage"
      cacher: "redis://redis:6379"
      transporter: "redis://redis:6379/2"
      mongo_url: "mongodb://mongodb:27017/steedos"
      mongo_oplog_url: "mongodb://mongodb:27017/local"
    storageClass: "resize-sc"
    data_storage: "1Gi"
    installed_packages_storage: "1Gi"
```

### 更新服务

```
cd steedos-community

helm upgrade -n namespace steedos-community ./steedos-community-0.1.0.tgz -f 2.2/values.yaml
```

### 卸载服务

```
helm uninstall steedos-community -n namespace  
```
