搭建 Shadowsocks-rust， V2ray+ Nginx + WebSocket 和 Reality, Hysteria2 代理脚本，支持 Debian、Ubuntu、Centos，并支持甲骨文ARM平台。

简单点讲，没域名的用户可以安装 Reality 和 hy2 代理，有域名的可以安装 V2ray+ Nginx + WebSocket 代理，各取所需。

运行脚本：

```
wget https://raw.githubusercontent.com/zhaodengfeng/v2ray-wss/main/tcp-wss.sh && bash tcp-wss.sh
```

**便宜VPS推荐：** https://hostalk.net/deals.html

![image](https://github.com/user-attachments/assets/76396d58-3fef-4028-8a5f-f8c9260c76e5)

已测试系统如下：

Debian 9, 10, 11, 12

Ubuntu 16.04, 18.04, 20.04, 22.04

CentOS 7

WSS客户端配置信息保存在：
`cat /usr/local/etc/v2ray/client.json`

Shadowsocks客户端配置信息：
`cat /etc/shadowsocks/config.json`

Reality客户端配置信息保存在：
`cat /usr/local/etc/xray/reclient.json`

Hysteria2客户端配置信息保存在：
`cat /etc/hysteria/hyclient.json`

卸载方法如下：
https://1024.day/d/1296

**提醒：连不上的朋友，建议先检查一下服务器自带防火墙有没有关闭？**
卸载ss-rust，命令如下：

systemctl stop shadowsocks

rm /usr/local/bin/ssserver

rm /etc/systemd/system/shadowsocks.service

systemctl daemon-reload

卸载 v2ray-wss 命令如下：

systemctl stop v2ray
systemctl stop nginx

bash <(curl -L https://raw.githubusercontent.com/v2fly/fhs-install-v2ray/master/install-release.sh) --remove

apt purge nginx -y

systemctl daemon-reload

卸载 Reality 命令如下：

systemctl stop xray

bash -c "$(curl -L https://github.com/XTLS/Xray-install/raw/main/install-release.sh)" @ remove
卸载 Hysteria2 命令如下：

bash <(curl -fsSL https://get.hy2.sh/) --remove
