# 部署高可用k3s

使用内置etcd来部署高可用k3s

## 创建一个master节点 并禁用自带的load balancer
``` shell
curl -sfL https://get.k3s.io | sh -s - server --cluster-init - --disable traefik
```

查看pods
``` shell
kubectl get pods -A

NAMESPACE     NAME                                      READY   STATUS    RESTARTS   AGE
kube-system   coredns-96cc4f57d-78bs2                   1/1     Running   0          46s
kube-system   local-path-provisioner-84bb864455-dt2s7   1/1     Running   0          46s
kube-system   metrics-server-ff9dbcb6c-h2w67            1/1     Running   0          46s
```

## 获取token
``` shell
sudo cat /var/lib/rancher/k3s/server/node-token
```

## 创建其他master节点

### 新建配置文件
``` shell
sudo mkdir -p /etc/rancher/k3s
sudo echo 'token: "刚刚获取的token"' > /etc/rancher/k3s/config.yaml
sudo echo 'server: "https://master节点:6443"' >> /etc/rancher/k3s/config.yaml
```

### 安装其他master节点
``` shell
curl -sfL https://get.k3s.io | sh -s - --disable traefik
```

## 安装agent节点
``` shell
curl -sfL https://get.k3s.io | K3S_URL=https://master节点:6443 K3S_TOKEN=XXXXXXXXXXXXXXXXX sh - --disable traefik
```

## 检查新的节点是否加入集群
``` shell
kubectl get nodes

NAME        STATUS   ROLES                       AGE    VERSION
k3s-node0   Ready    control-plane,etcd,master   4m2s   v1.22.6+k3s1
k3s-node1   Ready    control-plane,etcd,master   45s    v1.22.6+k3s1
k3s-node4   Ready    control-plane,etcd,master   60s    v1.22.6+k3s1
```

# 安装helm
在任意master节点安装helm
``` shell
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```

# 配置 loadbalancer

[使用 MetalLB 作为 load balancer](/k3s/metalLB)


# 配置 ingress controller

[使用 treafik 作为 ingress controller](/k3s/treafik)

# 其他

## 卸载k3s master节点
``` shell
/usr/local/bin/k3s-uninstall.sh
```

##卸载k3s agent节点
```
/usr/local/bin/k3s-agent-uninstall.sh
```

## 出现错误
当出现 ```Error: INSTALLATION FAILED: Kubernetes cluster unreachable: Get "http://localhost:8080/version": dial tcp [::1]:8080: connect: connection refused```

输入
``` shell
export KUBECONFIG=/etc/rancher/k3s/k3s.yaml
```
