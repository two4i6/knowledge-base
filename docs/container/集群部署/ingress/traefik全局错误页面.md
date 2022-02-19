# 🦦 Treafik ingress 默认错误页面 

Treafik 自带的错误页面只会显示 ```404 page not found```, 我们可以设置一个自定义的默认的错误页面。

---

## ⚠️ 开始

最简单的方法是配置一个ingress使用```defaultBackend```, 使用一个 service 返所有错误页面。

我们可以使用 [tarampampam/error-pages](https://hub.docker.com/r/tarampampam/error-pages) 这个镜像来方便的生成错误页面。

### 声明 deployment
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

## 声明 service
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

### 声明 middleware
```yaml
apiVersion: traefik.containo.us/v1alpha1
kind: Middleware
metadata:
  name: errorpage
  namespace: default
spec:
  errors:
    status:
      - "500-599"
    query: /{status}.html
    service:
      name: #处理错误信息的service
      port: 80
```
关于 middleware 请参考 [traefik中间件](traefik中间件.md)

### 声明 ingress
``` yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: errorpage
  # 使用 errorpage 中间件
  traefik.ingress.kubernetes.io/router.middlewares: default-errorpage@kubernetescrd
spec:
  defaultBackend:
    service:
      name: errorpage # 可以使用一个空的web server
      port:
        number: 8080
```

> ⚠️ 这个方法并不适用需要TLS认证的页面

---

[学习关于 traefik routing 的更多内容](https://doc.traefik.io/traefik/routing/providers/kubernetes-ingress/)