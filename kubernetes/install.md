### 安装kubernates

部署master节点

```shell
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
cat > /etc/apt/sources.list.d/kubernetes.list  << EOF
deb http://apt.kubernetes.io/ kubernetes-xenial main
EOF
apt-get update
apt-get install -y docker.io kubeadm



kubeadm init --config kubeadm.yaml


mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config

kubectl get nodes
kubectl describe node master
kubectl get pods -n kube-system
# 部署网络插件weave
kubectl apply -f https://git.io/weave-kube-1.6
```

kubeadm.yaml

```yaml
apiVersion: kubeadm.k8s.io/v1alpha1
kind: MasterConfiguration
controllerManagerExtraArgs:
  horizontal-pod-autoscaler-use-rest-clients: "true"
  horizontal-pod-autoscaler-sync-period: "10s"
  node-monitor-grace-period: "10s"
apiServerExtraArgs:
  runtime-config: "api/all=true"
kubernetesVersion: "stable-1.11"
```

部署worker节点

```shell
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
cat > /etc/apt/sources.list.d/kubernetes.list  << EOF
deb http://apt.kubernetes.io/ kubernetes-xenial main
EOF
apt-get update
apt-get install -y docker.io kubeadm

# 之后执行部署完成master之后打印出的kubeadm join
```

通过 Taint/Toleration 调整 Master 执行 Pod 的策略

```shell
kubectl taint nodes node1 foo=bar:NoSchedule
# Taints:             node-role.kubernetes.io/master:NoSchedule
kubectl describe node
# 我们在node-role.kubernetes.io/master这个键后面加上了一个短横线“-”，
# 这个格式就意味着移除所有以node-role.kubernetes.io/master为键的 Taint。
kubectl taint nodes --all node-role.kubernetes.io/master-
```

部署dashboard可视化插件

```shell
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
```

部署容器存储插件

```shell
kubectl apply -f https://raw.githubusercontent.com/rook/rook/master/cluster/examples/kubernetes/ceph/operator.yaml

kubectl apply -f https://raw.githubusercontent.com/rook/rook/master/cluster/examples/kubernetes/ceph/cluster.yaml

kubectl get pods -n rook-ceph-system
kubectl get pods -n rook-ceph
```





