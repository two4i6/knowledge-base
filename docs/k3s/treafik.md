# Treafik

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