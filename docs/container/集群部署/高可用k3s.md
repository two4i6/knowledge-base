# 🏠 部署高可用k3s

使用内置etcd来部署高可用k3s。

---

## 🏠 创建一个master节点并禁用自带的 load balance 和 treafik
``` shell
curl -sfL https://get.k3s.io | sh -s - server --cluster-init - --disable traefik --disable servicelb
```

---

## ⚖️ 配置 kube-vip
[kube-vip](/container/集群部署/kube-vip)

---

## 🔒 获取 token
``` shell
sudo cat /var/lib/rancher/k3s/server/node-token
```

---

## 🏠 创建额外 master 节点

### 新建配置文件
``` shell
sudo mkdir -p /etc/rancher/k3s
sudo echo 'token: "刚刚获取的token"' > /etc/rancher/k3s/config.yaml
sudo echo 'server: "https://kube-vip地址:6443"' >> /etc/rancher/k3s/config.yaml
```

### 安装
``` shell
curl -sfL https://get.k3s.io | sh -s - --disable traefik --disable servicelb
```

---

## 👷‍♀️ 创建 worker 节点
``` shell
curl -sfL https://get.k3s.io | K3S_URL=https://master节点:6443 K3S_TOKEN=XXXXXXXXXXXXXXXXX sh - --disable traefik
```

---

## 🔍 检查新的节点是否加入集群
``` shell
kubectl get nodes

NAME        STATUS   ROLES                       AGE    VERSION
k3s-node0   Ready    control-plane,etcd,master   4m2s   v1.22.6+k3s1
k3s-node1   Ready    control-plane,etcd,master   45s    v1.22.6+k3s1
k3s-node4   Ready    control-plane,etcd,master   60s    v1.22.6+k3s1
```

---

## ⚙️ 额外

### 安装 helm
在任意master节点安装helm
``` shell
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```

> 当使用 helm 安装的时候可能会提示 ```Kubernetes cluster unreachable``` 错误， [解决方法](/container/集群部署/常见问题)

### 配置 loadbalancer

[使用 MetalLB 作为 load balancer](/container/集群部署/loadbalance/metalLB)

### 配置 treafik ingress

[使用 treafik 作为 ingress controller](/container/集群部署/ingress/traefik)

### 配置 nginx ingress

[使用 nginx 作为 ingress controller](/container/集群部署/ingress/nginx)

### 卸载k3s master节点
``` shell
/usr/local/bin/k3s-uninstall.sh
```

### 卸载k3s agent节点
```
/usr/local/bin/k3s-agent-uninstall.sh
```

