### systemd

#### 查看systemd文档

```shell
info systemd
```

#### service unit example

```c
[Unit]
Description=Test Service
After=storage.service
After=network.target

[Service]
LimitNOFILE=40960
LimitNPROC=40960
User=test
Group=test
Type=simple
WorkingDirectory=/path/to/work
ExecStart=/path/to/exec
MemoryLimit=2G

Restart=on-failure
RestartSec=2s

[Install]
WantedBy=multi-user.target
```

#### 限制文档

```shell
info systemd.resource-control
```