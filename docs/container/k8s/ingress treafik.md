# Treafik

## 配置 Seret
```
apiVersion: v1
kind: Secret
metadata:
  name: cloudflare-credentials
  namespace: traefik
type: Opaque
stringData:
  email: admin@admin.com
  apiKey: t0p-Secret
```

## 配置value.yaml
```
additionalArguments:
# Configure your CertificateResolver here...
# 
# HTTP Challenge
# ---
# Generic Example:
#   - --certificatesresolvers.generic.acme.email=your-email@example.com
#   - --certificatesresolvers.generic.acme.caServer=https://acme-v02.api.letsencrypt.org/directory
#   - --certificatesresolvers.generic.acme.httpChallenge.entryPoint=web
#   - --certificatesresolvers.generic.acme.storage=/ssl-certs/acme-generic.json
#
# Prod / Staging Example:
#   - --certificatesresolvers.staging.acme.email=your-email@example.com
#   - --certificatesresolvers.staging.acme.caServer=https://acme-staging-v02.api.letsencrypt.org/directory
#   - --certificatesresolvers.staging.acme.httpChallenge.entryPoint=web
#   - --certificatesresolvers.staging.acme.storage=/ssl-certs/acme-staging.json
#   - --certificatesresolvers.production.acme.email=your-email@example.com
#   - --certificatesresolvers.production.acme.caServer=https://acme-v02.api.letsencrypt.org/directory
#   - --certificatesresolvers.production.acme.httpChallenge.entryPoint=web
#   - --certificatesresolvers.production.acme.storage=/ssl-certs/acme-production.json
#
# DNS Challenge
# ---
# Cloudflare Example:
  - --certificatesresolvers.cloudflare.acme.dnschallenge.provider=cloudflare
  - --certificatesresolvers.cloudflare.acme.email=your-email@example.com
  - --certificatesresolvers.cloudflare.acme.dnschallenge.resolvers=1.1.1.1
  - --certificatesresolvers.cloudflare.acme.storage=/ssl-certs/acme-cloudflare.json
#
# Generic (replace with your DNS provider):
#  - --certificatesresolvers.generic.acme.dnschallenge.provider=generic
#  - --certificatesresolvers.generic.acme.email=your-email@example.com
#  - --certificatesresolvers.generic.acme.storage=/ssl-certs/acme-generic.json

logs:
# Configure log settings here...
  general:
    level: ERROR

ports:
# Configure your entrypoints here...
  web:
    # (optional) Permanent Redirect to HTTPS
    redirectTo: websecure
  websecure:
    tls:
      enabled: true
      # (optional) Set a Default CertResolver
      certResolver: cloudflare
  

env:
# Set your environment variables here...
# 
# DNS Challenge Credentials
# ---
# Cloudflare Example:
   - name: CF_API_EMAIL
     valueFrom:
       secretKeyRef:
         key: email
         name: cloudflare-credentials
   - name: CF_API_KEY
     valueFrom:
       secretKeyRef:
         key: apiKey
#         name: cloudflare-credentials

# Disable Dashboard
#ingressRoute:
#  dashboard:
#    enabled: false

# Persistent Storage
persistence:
  enabled: true
  name: ssl-certs
  size: 1Gi
  path: /ssl-certs

deployment:
  initContainers:
    # The "volume-permissions" init container is required if you run into permission issues.
    # Related issue: https://github.com/containous/traefik/issues/6972
    - name: volume-permissions
      image: busybox:1.31.1
      command: ["sh", "-c", "chmod -Rv 600 /ssl-certs/*"]
      volumeMounts:
        - name: ssl-certs
          mountPath: /ssl-certs

# Set Traefik as your default Ingress Controller, according to Kubernetes 1.19+ changes.
ingressClass:
  enabled: true
  isDefaultClass: true

```


## 安装treafik
``` shell
helm repo add traefik https://helm.traefik.io/traefik
helm repo update
helm install traefik traefik/traefik --create-namespace -n treafik
```

## 检查treafik
``` shell
kubectl get service -A

NAMESPACE     NAME             TYPE           CLUSTER-IP      EXTERNAL-IP     PORT(S)                      AGE
default       kubernetes       ClusterIP      10.43.0.1       <none>          443/TCP                      10m
kube-system   kube-dns         ClusterIP      10.43.0.10      <none>          53/UDP,53/TCP,9153/TCP       10m
kube-system   metrics-server   ClusterIP      10.43.239.79    <none>          443/TCP                      10m
treafik       traefik          LoadBalancer   10.43.212.101   192.168.0.120   80:30228/TCP,443:30832/TCP   34s
```

## 配置第一个应用
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