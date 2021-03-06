# 🚢 Portainer

Portainer 可以通过GUI界面管理 Docker 和 K8s。

---

## 💿 安装

``` shell
helm repo add portainer https://portainer.github.io/k8s/
helm repo update
helm install --create-namespace -n portainer portainer portainer/portainer \
--set service.type=LoadBalancer
```
> ⚠️ 这里使用loadbalancer配置service

---

## 🔍 检查是否安装
``` shell
kubectl get all -n portainer

NAME                        READY   STATUS    RESTARTS   AGE
portainer-f8dbb6c74-p2g75   1/1     Running   0          51s
svclb-portainer-jqf9k       3/3     Running   0          51s
svclb-portainer-r9qlv       3/3     Running   0          51s
svclb-portainer-x4l26       3/3     Running   0          51s

NAME        TYPE           CLUSTER-IP      EXTERNAL-IP     PORT(S)                                        AGE
portainer   LoadBalancer   10.43.126.166   192.168.0.121   9000:30107/TCP,9443:32415/TCP,8000:32327/TCP   84s
```

Now we can access the portainer GUI through http://192.168.0.121:9000