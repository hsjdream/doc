## Docker

### 安装

https://docs.docker.com/

https://docs.docker.com/install/linux/docker-ce/ubuntu/

Ubuntu18.04安装docker

```shell
sudo apt-get remove docker docker-engine docker.io
sudo apt-get update
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
sudo apt-get update
sudo apt-get install docker-ce
```



### 使用    

#### 给运行中容器增加端口映射

http://yaxin-cn.github.io/Docker/expose-port-of-running-docker-container.html

```shell
iptables -A DOCKER ! -i docker0 -o docker0 -p tcp --dport 27017 -d 172.17.0.2 -j ACCEPT
iptables -t nat -A POSTROUTING -p tcp --dport 27017 -s 172.17.0.2 -d 172.17.0.2 -j MASQUERADE
iptables -t nat -A DOCKER ! -i dokcer0 -p tcp --dport 27017 -j DNAT --to-destination 172.17.0.2:27017
```

docker run --link 说明

https://www.jianshu.com/p/21d66ca6115e

#### 