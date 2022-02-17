# 直接挂载nfs在 depolyments

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

如果出现错误 ```Kubernetes NFS volume mount fail with exit status 32```

再每个节点安装
```
apt-get install -y nfs-common
```