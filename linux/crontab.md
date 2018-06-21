## crontab

### 简介

主要是linux用来做定时任务,可以具体的分钟/小时/天/月/周

### 使用

#### 说明

```shell
usage:	crontab [-u user] file
	crontab [ -u user ] [ -i ] { -e | -l | -r }
		(default operation is replace, per 1003.2)
	-e	(edit user's crontab)
	-l	(list user's crontab)
	-r	(delete user's crontab)
	-i	(prompt before deleting user's crontab)
```

#### 备份

```shell
crontab -l > crontab.bak
```

#### 恢复

```shell
crontab filename
```

#### 删除

```shell
crontab -r
```

#### 列出

```shell
crontab -l
```

#### 编辑

```
crontab -e
```

