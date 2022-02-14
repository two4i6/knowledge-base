## 创建第一个master节点
```
curl -sfL https://get.k3s.io | sh -s - server --cluster-init
```

## 获取token
```
sudo cat /var/lib/rancher/k3s/server/node-token
```

## 创建第二个master节点
```
#新建配置文件
nano /etc/rancher/k3s/config.yaml
#加入下面的内容
token: "刚刚获取的token"
server: "https://刚刚节点的ip:6443"
#安装k3s
curl -sfL https://get.k3s.io | sh -
```

## 检查新的节点是否加入集群
```
kubectl get node
```

helm install rancher rancher-latest/rancher \
  --namespace cattle-system \
  --set hostname=rancher.luobo.ca \
  --set replicas=3


mkdir /etc/rancher
mkdir /etc/rancher/k3s
nano /etc/rancher/k3s/config.yaml

token: "XXXXXXXXX"
server: "https://k3s-node2.luobo.ca:6443"

curl -sfL https://get.k3s.io | sh -

/usr/local/bin/k3s-uninstall.sh

curl -sfL https://get.k3s.io | K3S_URL=https://k3s-node1.luobo.ca:6443 K3S_TOKEN=XXXXXXXXXXXXXXXXX sh -

/usr/local/bin/k3s-agent-uninstall.sh

docker logs  108e46b38832  2>&1 | grep "Bootstrap Password:"