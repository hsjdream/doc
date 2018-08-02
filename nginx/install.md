## 安装nginx

https://nginx.org/en/linux_packages.html

centos 7.2

```shell
touch /etc/yum.repos.d/nginx.repo
vi /etc/yum.repos.d/nginx.repo

[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/centos/7/$basearch/
gpgcheck=0
enabled=1

wget http://nginx.org/keys/nginx_signing.key
rpm --import nginx_signing.key

yum install -y nginx.x86_64
```

nginx 配置静态页面

```
server {
    listen       80;
    server_name  localhost;
    root /path/to/root;
    index index.html;
}
```



