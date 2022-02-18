# 🌍 通过 zerotier 来部署集群

[原文](https://www.danmanners.com/posts/p2-k3s-digitalocean-zerotier-and-more)

---

## 💻 新建 zerotier 网络

[zerotier](https://my.zerotier.com/)

新建一个网络

![新建](/container/集群部署/奇怪的配置/img/zerotier01.png)

---

## 💿 安装zerotier
``` shell
curl -s https://install.zerotier.com | sudo bash
zerotier-cli join **Network ID**
```

---

## 🌍 配置 zerotier 'router'
在debian环境下
```
# Ensure that we can forward packets between interfaces
sudo sysctl net.ipv4.ip_forward=1
sudo sed -i 's/#net.ipv4.ip_forward=1/net.ipv4.ip_forward=1/g' /etc/sysctl.conf

# Set up iptables rules
ip link | awk -F: '$0 !~ "lo|vir|wl|^[^0-9]"{print $2;getline}'
# eth0        <== 物理网口
# ztyou2j6dw  <== Zerotier虚拟网口

PHY_IFACE="eth0"
ZT_IFACE="$(ip l | grep 'zt' | awk '{print substr($2,1,length($2)-1)}')" # <== This command will grab your ZeroTier interface name
sudo iptables -t nat -A POSTROUTING -o $PHY_IFACE -j MASQUERADE
sudo iptables -A FORWARD -i $PHY_IFACE -o $ZT_IFACE -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -A FORWARD -i $ZT_IFACE -o $PHY_IFACE -j ACCEPT

# Make sure the rules are persistent after reboot/poweroff
sudo apt install iptables-persistent
sudo bash -c iptables-save > /etc/iptables/rules.v4

# Ensure that ZeroTier always comes back up after a reboot
sudo systemctl enable zerotier-one
```

---

# 📖 配置 zerotier

进入zerotier网络 > **Advanced** > **Managed Routes** > **Add Routes**

![zerotier](/container/集群部署/奇怪的配置/img/zerotier02.png)

- Destination - router所处的网段 如192.168.0.0/24

- (Via) - router的虚拟ip地址

---

# 🧪 测试

尝试 ping router 网段的设备。

---

# ⌚️ 接下来

[构建高可用k3s](/container/集群部署/高可用k3s)