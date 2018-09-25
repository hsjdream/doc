## linux

修改linux时区

```shell
 cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
```

关闭linux交换分区

```shell
# 查看当前的交换分区
cat /proc/swaps
# 关闭所有交换设备和文件
swapoff -a
```

测试udp端口是否可用

```shell
nc -vuz xx.xx.xx.xx 4500
# Connection to xx.xx.xx.xx 4500 port [udp/ipsec-nat-t] succeeded!
```

