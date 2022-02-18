---
tags:
  - k3s
  - k8s 部署
---

# ⚖️ 部署 kube-vip

---

## 📃 下载配置文件
```
curl -s https://kube-vip.io/manifests/rbac.yaml > /var/lib/rancher/k3s/server/manifests/kube-vip-rbac.yaml
```

---

## ⌨️ 配置变量

### 检查 interface
```
ifconfig 
```

### 设置变量

``` shell
export VIP=192.168.0.100
export INTERFACE=eth0
```
> ⚠️ ```VIP=192.168.0.100``` 是kube-vip的ip

---

## 🪛 配置 manifests
在 /etc/kuberentes/manifests 中设置静态 pod 的 yaml 资源清单文件，这样 Kubernetes 就会自动在每个控制平面节点上部署 kube-vip 的 pod 了。

``` shell
# pull image
ctr image pull docker.io/plndr/kube-vip:latest

# create alias
alias kube-vip="ctr run --rm --net-host docker.io/plndr/kube-vip:latest vip /kube-vip"

# generate manifest
kube-vip manifest daemonset \
    --arp \
    --interface $INTERFACE \
    --address $VIP \
    --controlplane \
    --leaderElection \
    --taint \
    --services \
    --inCluster | tee /var/lib/rancher/k3s/server/manifests/kube-vip.yaml
```

---

## 👩‍🔧 修改 kube-vip.yaml 

``` shell
nano /var/lib/rancher/k3s/server/manifests/kube-vip.yaml
```

修改 ```tolerations``` 片段

``` yaml
    tolerations:
    - effect: NoSchedule
    key: node-role.kubernetes.io/master
    operator: Exists
```

---

## 🧪 测试 
```
ping 192.168.0.100
```

---

## ⚙️ 修改 kubeconfig

K3S: 
``` shell
nano /etc/rancher/k3s/k3s.yaml
```

修改 ```server``` 片段

```
server: https://192.168.0.100:6443
```


