# 🦦 Treafik ingress 全局错误页面 

Treafik 自带的错误页面只会显示 ```404 page not found```, 我们可以设置一个自定义的全局错误页面。

---

## ⚠️ 开始

最简单的方法是配置一个ingress使用```defaultBackend```, 使用一个 service 返所有错误页面。
``` yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: errorpage
spec:
  defaultBackend:
    service:
      name: errorpage
      port:
        number: 8080
```

我们可以使用 [tarampampam/error-pages](https://hub.docker.com/r/tarampampam/error-pages) 这个镜像来生成错误页面。

---

## 📃 配置deployment
``` yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: errorpage
  labels:
    app: errorpage
spec:
  replicas: 1
  selector:
    matchLabels:
      app: errorpage
  template:
    metadata:
      labels:
        app: errorpage
    spec:
      containers:
      - name: errorpage
        image: tarampampam/error-pages
        env:
        - name: TEMPLATE_NAME
          value: random
        - name: SHOW_DETAILS
          value: "true"
        ports:
        - containerPort: 8080
```

---

## 📃 配置service
``` yaml
apiVersion: v1
kind: Service
metadata:
  name: errorpage
spec:
  selector:
    app: errorpage
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080
```

---

[学习关于 traefik routing 的更多内容](https://doc.traefik.io/traefik/routing/providers/kubernetes-ingress/)