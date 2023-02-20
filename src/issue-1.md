# acme脚本学习笔记

1、acme脚本的安装

```bash
# 安装acme脚本
curl https://get.acme.sh | sh -s email=xxx@xxx.com
# 重新加载环境变量
source ~/.bashrc
```

注意：安装完acme脚本后，需重新加载环境变量，不然会报错：`acme.sh: command not found`。

2、acme脚本的基本使用

```bash
# 切换ca机构
acme.sh --set-default-ca --server letsencrypt
acme.sh --set-default-ca --server zerossl
# nginx模式申请证书
acme.sh --issue -d xxx.example.com --nginx /usr/local/nginx/conf/nginx.conf
# 安装证书
acme.sh --install-cert -d xxx.example.com \
--key-file       /usr/local/nginx/ssl/private/xxx.example.com.key.pem  \
--fullchain-file /usr/local/nginx/ssl/certs/xxx.example.com.cert.pem \
--reloadcmd     "service nginx force-reload"
```
