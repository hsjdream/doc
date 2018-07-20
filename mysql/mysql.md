### mysql

安装mysql客户端在centos7上


https://dev.mysql.com/downloads/repo/yum/

下载完成之后,通过rpm安装

```shell
wget https://dev.mysql.com/get/mysql80-community-release-el7-1.noarch.rpm
rpm -Uvh mysql80-community-release-el7-1.noarch.rpm
yum install mysql-community-client.x86_64 
```

mysql binlog文档

https://blog.csdn.net/leshami/article/details/39801867



mysql client登录数据库

```
mysql -h 127.0.0.1 -P 3306 -u xx -p xx
```

mysqlbinlog文档

https://blog.csdn.net/leshami/article/details/41962243

