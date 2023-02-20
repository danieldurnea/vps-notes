# apache2学习笔记

```bash
# apt安装apache2
apt install apache2
```

在基于debian的linux发行版中，apache http服务器的默认安装目录是`/etc/apache2`。这个目录包含了apache服务器的配置文件和相关资源。

```BASH
.
├── apache2.conf（apache的主要配置文件，包含了全局的apache配置选项和指令）
├── conf-available（包含了可用的apache配置文件模板）
├── conf-enabled（包含了启用的配置文件的符号链接）
├── envvars（包含了apache的环境变量）
├── magic（包含了apache的魔术文件，用来识别文件的类型和编码）
├── mods-available（包含了apache的可用模块）
├── mods-enabled（包含了启用的模块的符号链接）
├── ports.conf（指定了apache监听的端口和协议）
├── sites-available（包含了可用的apache网站配置文件模板）
└── sites-enabled（包含了启用的网站配置文件的符号链接）
```



1、配置http

```bash
# 启用代理模块和反向代理模块
a2enmod proxy
a2enmod proxy_http

cd /etc/apaache2/sites-available
vi xxx.example.com.conf

<VirtualHost *:80>
    ServerName xxx.example.com
    ProxyPass / http://127.0.0.1:xxx/
    ProxyPassReverse / http://127.0.0.1:xxx/
</VirtualHost>

# 启用站点的配置文件
a2ensite xxx.example.com.conf
# 重新加载apache2
systemctl reload apache2
```

