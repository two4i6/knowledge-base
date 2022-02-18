# Argo

---

## 安装 argo-cli
[argo-cli](https://github.com/argoproj/argo-workflows/releases)

``` shell
# Download the binary
curl -sLO https://github.com/argoproj/argo-workflows/releases/download/v3.3.0-rc4/argo-linux-amd64.gz

# Unzip
gunzip argo-linux-amd64.gz

# Make binary executable
chmod +x argo-linux-amd64

# Move binary to path
mv ./argo-linux-amd64 /usr/local/bin/argo

# Test installation
argo version
```

---

## 安装 argo-server 和 argo-controller

### 使用yaml
```
kubectl create namespace argo
kubectl apply -n argo -f https://github.com/argoproj/argo-workflows/releases/download/v3.3.0-rc4/install.yaml
```

### 使用helm
``` shell
helm repo add argo https://argoproj.github.io/argo-helm
```

⚠️ k3s: 需要把 ```containerRuntimeExecutor: docker``` 修改为 ```containerRuntimeExecutor: k8sapi```

---

## 测试
``` shell
argo submit -n argo --watch https://raw.githubusercontent.com/argoproj/argo-workflows/master/examples/hello-world.yaml
```

---

## 使用 argo-UI

### 获取 auth-token
```
kubectl -n argo exec pod/argo-argo-workflows-server-5f5889464c-f8fjm -- argo auth token
```

```argo-argo-workflows-server-5f5889464c-f8fjm``` 是argo-server的pod名称

---

## ⚠️ 常见问题

pod pending 显示 ```MountVolume.SetUp failed for volume “docker-sock” ```

需要把 ```containerRuntimeExecutor: docker``` 修改为 ```containerRuntimeExecutor: k8sapi```