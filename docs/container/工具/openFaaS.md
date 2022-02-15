# openFaaS

---

## 安装

为了简化安装，使用 ```arkade```

### 安装 arkade

```
curl -sLS https://dl.get-arkade.dev | sudo sh
```

### 安装 openFaaS

```
arkade install openfaas
arkade info openfaas
```

### 安装 openFaaS cli

```
curl -sSL https://cli.openfaas.com | sudo -E sh
faas version
```

### 查看密码

```
PASSWORD=$(kubectl get secret -n openfaas basic-auth -o jsonpath="{.data.basic-auth-password}" | base64 --decode; echo)
echo -n $PASSWORD | faas-cli login --username admin --password-stdin 
echo $PASSWORD
```

### 登陆web ui

默认用户为 ```admin```
