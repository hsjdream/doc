### systemctl

service

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

Restart=on-failure
RestartSec=2s

[Install]
WantedBy=multi-user.target
```

