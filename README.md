# v2ray-installer

1. 在<https://freenom.com/>上申请免费域名，免费12个月
2. 在google cloud上创建虚拟机
3. 利用<https://www.cloudflare.com/>做域名解析
4. 配置虚拟机


虚拟机配置步骤

1. 选用Debian系统
2. 运行如下代码更新系统和安装必备软件`apt update -y && apt install -y curl && apt install -y wget`
3. 安装宝塔`wget -O install.sh http://download.bt.cn/install/install-ubuntu_6.0.sh && bash install.sh`
4. 搭建xray面板：
`bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)`
5. 安装BBR加速：
`wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh" && chmod +x tcp.sh && ./tcp.sh`

宝塔配置
1. 添加网站
2. 申请SSL证书使用Let's Encrypt
3. 证书申请成功了，就可以开启强制SSL
4. 如果SSL证书申请不成功可以使用如下方法，最后把公钥和私钥粘会宝塔的SSL配置页面
```
apt install -y socat  # Debian/Ubuntu 命令

curl https://get.acme.sh | sh
~/.acme.sh/acme.sh --register-account -m jack.zxzhou@gmail.com

~/.acme.sh/acme.sh --issue -d bytesmonster.xyz --standalone

~/.acme.sh/acme.sh --installcert -d bytesmonster.xyz --key-file /root/private.key --fullchain-file /root/cert.crt

pbcopy < /root/private.key
pbcopy < /root/cert.crt
```

x-ray网站配置


