# ð æè½½NFS

## âï¸ depolyments / StatefulSets
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

## ðµï¸ââï¸ å¸¸è§é®é¢
å¦æåºç°éè¯¯ ```Kubernetes NFS volume mount fail with exit status 32```ï¼éè¦åæ¯ä¸ªèç¹å®è£ ```nfs-common```ã
```
apt-get install -y nfs-common
```