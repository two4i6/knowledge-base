# 🦫 Treafik + 🔒 Cloudflare

使用 helm 安装 Treafik, 并自动配置证书。

---

## 🔒 配置 Seret
```
apiVersion: v1
kind: Secret
metadata:
  name: cloudflare-credentials
  namespace: traefik
type: Opaque
stringData:
  email: **admin@admin.com**
  apiKey: **cloudflare-api-key**
```

---

## 📃 创建 value.yaml
```
additionalArguments:
  - --certificatesresolvers.cloudflare.acme.dnschallenge.provider=cloudflare
  - --certificatesresolvers.cloudflare.acme.email=your-email@example.com
  - --certificatesresolvers.cloudflare.acme.dnschallenge.resolvers=1.1.1.1
  - --certificatesresolvers.cloudflare.acme.storage=/ssl-certs/acme-cloudflare.json

ports:
  web:
    redirectTo: websecure #强制使用https
  websecure:
    tls:
      enabled: true
      certResolver: cloudflare
  
env: 
   - name: CF_API_EMAIL
     valueFrom:
       secretKeyRef:
         key: email
         name: cloudflare-credentials
   - name: CF_API_KEY
     valueFrom:
       secretKeyRef:
         key: apiKey
         name: cloudflare-credentials

persistence: 
  enabled: true
  name: ssl-certs
  size: 1Gi
  path: /ssl-certs

ingressClass:
  enabled: true
  isDefaultClass: true
```

---

## 💿 安装treafik
``` shell
helm repo add traefik https://helm.traefik.io/traefik
helm repo update
helm install traefik traefik/traefik --create-namespace -n treafik -f value.yaml
```

---

## 🔍 检查treafik
``` shell
kubectl get service -A

NAMESPACE     NAME             TYPE           CLUSTER-IP      EXTERNAL-IP     PORT(S)                      AGE
default       kubernetes       ClusterIP      10.43.0.1       <none>          443/TCP                      10m
kube-system   kube-dns         ClusterIP      10.43.0.10      <none>          53/UDP,53/TCP,9153/TCP       10m
kube-system   metrics-server   ClusterIP      10.43.239.79    <none>          443/TCP                      10m
treafik       traefik          LoadBalancer   10.43.212.101   192.168.0.120   80:30228/TCP,443:30832/TCP   34s
```

---

## 🕹️ 配置一个ingress
``` yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: wp-clcreative
  namespace: wp-clcreative
  annotations:
    # (Optional): Annotations for the Ingress Controller
    # ---
    # General:
    # kubernetes.io/ingress.class: traefik
    # 
    # TLS configuration:
    # traefik.ingress.kubernetes.io/router.entrypoints: web, websecure
    # traefik.ingress.kubernetes.io/router.tls: "true"
    # 
    # Middleware:
    # traefik.ingress.kubernetes.io/router.middlewares:your-middleware@kubernetescrd
spec:
  rules:
  - host: "your-hostname.com"  # Your hostname
    http:
      paths:
      # Path-based routing settings:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: your-service-name  # The name of the service
            port:
              number: 80  # Service Portnumber

```