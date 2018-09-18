### ipsec

#### server

docker.sh

```shell
docker run \
    --name ipsec-vpn-server \
    --env-file ./vpn.env \
    --restart=always \
    -p 500:500/udp \
    -p 4500:4500/udp \
    -v /lib/modules:/lib/modules:ro \
    -d --privileged \
    hwdsl2/ipsec-vpn-server
```

vpn.env 

```
VPN_IPSEC_PSK=xxx
VPN_USER=xxx
VPN_PASSWORD=xxx
```

#### client