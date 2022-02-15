# 安装Rancher

## 添加Helm chart源
```
helm repo add rancher-latest https://releases.rancher.com/server-charts/latest
```
## 创建Namespace
```
kubectl create namespace cattle-system
```
## 创建证书
```
sh ./create_self-signed-cert.sh --ssl-domain=xxx.luobo.ca --ssl-trusted-ip=192.168.0.21, 192.168.0.22, 192.168.0.23, 192.168.0.25 --ssl-size=2048 --ssl-date=3650
```

## 导入证书
```
kubectl -n cattle-system create secret generic tls-ca   --from-file=cacerts.pem=./cakey.pem

```

## 安装rancher
```
helm install rancher rancher-latest/rancher --namespace cattle-system --set hostname=xxx.luobo.ca --set ingress.tls.source=secret --set privateCA=true --set replicas=3
```

## 出现错误
```
export KUBECONFIG=/etc/rancher/k3s/k3s.yaml
```
