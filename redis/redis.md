## Redis

临时开启aof

```shell
redis-cli -h host -p port config set appendonly yes
```

临时关闭aof

```shell
redis-cli -h host -p port config set appendonly yes
```

导入aof文件

```
redis-cli -h host -p port -a password --pipe < appendonly.aof
```

