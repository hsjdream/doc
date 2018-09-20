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

