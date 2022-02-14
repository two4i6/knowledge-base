# 准备工作
## 安装mriadb
``` shell
sudo apt install mariadb-server
```
## 创建database
``` shell
sudo mysql

```
## 新建用户
## 授权用户
## 开放端口
``` shell
#查看端口是否被绑定在本地端口127.0.0.1：3396 
netstat -an | grep 3306
# 如绑定在本地端口则修改配置文件
sudo nano /etc/mysql/my.cnf
#在最后添加 
bind-address = 0.0.0.0
#保存并重启
sudo /etc/init.d/mysql restart
```


# 安装k3s
```
curl -sfL https://get.k3s.io | sh -s - server --datastore-endpoint='mysql://用户名:密码@tcp(数据库地址:3306)/db名称'
# 注意database name不要加特殊字符
```

curl -sfL https://get.k3s.io | sh -s - server --cluster-init

curl -sfL https://get.k3s.io | K3S_TOKEN='mytoken' sh -s - server https://xx.xx.xx.xx:6443


curl -sfL https://get.k3s.io | K3S_URL=https://10.147.17.12:6443 K3S_TOKEN=XXXXXXXXX sh -