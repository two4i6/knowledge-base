# 📁 挂载NFS

## ⚙️ depolyments / StatefulSets
``` yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
        volumeMounts:
        - name: data
          mountPath: /usr/share/nginx/html
      volumes:
      - name: data
        nfs:
          path: /opt/nfs-deployment
          server: 172.26.204.144
```

## 🕵️‍♀️ 常见问题
如果出现错误 ```Kubernetes NFS volume mount fail with exit status 32```，需要再每个节点安装 ```nfs-common```。
```
apt-get install -y nfs-common
```