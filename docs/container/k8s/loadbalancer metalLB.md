# MetlLB

## 安装

通过helm安装

### 创建values.yaml
``` shell
configInline:
  address-pools:
   - name: default
     protocol: layer2
     addresses:
     - 192.168.0.120-192.168.0.130
```
这将配置一个由 MetalLB 二层模式控制的 service 外部 IP 段为 ```192.168.0.120-192.168.0.130```。

### 通过helm安装 MetalLB
``` shell
helm repo add metallb https://metallb.github.io/metallb
helm repo update
helm install metallb metallb/metallb -f values.yaml --create-namespace -n metallb
```

### 检查MetalLB
``` shell
kubectl get pods -n metallb
```