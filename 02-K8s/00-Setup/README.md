# In the following demo will be setting up 3 Node Kubernetes Cluster ( 1 Master & 2 Workers  


 

## Now provision three virtual machines with following commands:

```
VM Template - Master, Worker1 & Worker2
OS - Ubuntu 20.04
Size - Standard D2s v3 (2 vcpus, 8 GiB memory)
Network - Same VNet for all the VMs
Port    - 22,80,443

```

## Please ensure the name resolution is configured:


### Step 1: Set the hostname on all the nodes correctly: 
```
hostname master 
hostname > /etc/hostname
```

### Step 2: Check each nodes hostname & their respective route able IP Address:
```
ip addr 
```

### Step 3: Update /etc/hosts local linux resolver file like below: 
```
vi /etc/hosts

```

### Sample: /etc/hosts

```
root@master:~# cat /etc/hosts
127.0.0.1 localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


# K8s Node Name Resolution
<master-ip-address>    master master
<worker1-ip-address>   worker2 worker2
<worker2-ip-address>   worker1 worker1
root@master:~#
```


## Login to master node & clone the repo after that execute install-kubernetes.sh. 

Note : 

1.	Check your master machines ip address & update the same in install-k8s-master-node.sh (--apiserver-advertise-address="YourMasterIP")
2.	Please copy the joining token which is generated by the execution script. 


##login to your master node: 

```
sudo su - 
git clone https://github.com/amitvashisttech/docker-k8s-ey-14-Sept-2024.git
cd docker-k8s-ey-14-Sept-2024/02-k8s/00-Setup
sh install-k8s-master-node.sh

---
Your Kubernetes master has initialized successfully!

To start using your cluster, you need to run the following as a regular user:

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config

You should now deploy a pod network to the cluster.
Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
  https://kubernetes.io/docs/concepts/cluster-administration/addons/

You can now join any number of machines by running the following on each node
as root:

  kubeadm join 172.31.0.100:6443 --token mr74fn.m4upjko4cfm5uwmz --discovery-token-ca-cert-hash sha256:cb406434a7f06d213eabfce7d6980b3948525d13e1c25b9f061831039bf49f52

---
```
## In order to intract with kubernetes cluster run the following commands
```
root@master:~# mkdir -p $HOME/.kube
root@master:~# sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
root@master:~# sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

### To Check the K8s Node Status
```
root@k8s-master:~# kubectl get nodes 
NAME         STATUS   ROLES    AGE    VERSION
master   Ready    master   5m6s   v1.18.0
```


## In parallel Login to both the nodes /workers & clone the repo after that execute install-node.sh. 

```
login to your woker nodes
sudo su - 
git clone https://github.com/amitvashisttech/docker-k8s-ey-14-Sept-2024.git
cd docker-k8s-ey-14-Sept-2024/02-k8s/00-Setup
sh install-k8s-worker-node.sh
```

## Now apply the joining token on both the workers what you have recived on your master node. 
```
kubeadm join 172.31.0.100:6443 --token mr74fn.m4upjko4cfm5uwmz --discovery-token-ca-cert-hash sha256:cb406434a7f06d213eabfce7d6980b3948525d13e1c25b9f061831039bf49f52
```

## Note: In case you are getting CRI Error, then please append the join token with crisocket "--cri-socket unix://var/run/crio/crio.sock"

## Let check the kubernetes cluster nodes status & details
```
root@master:~# kubectl  get nodes
NAME      STATUS   ROLES           AGE     VERSION
master    Ready    control-plane   10m     v1.29.9
worker1   Ready    <none>          7m27s   v1.29.9
worker2   Ready    <none>          7m53s   v1.29.9



root@master:~# kubectl  get nodes -o wide
NAME      STATUS   ROLES           AGE     VERSION   INTERNAL-IP   EXTERNAL-IP   OS-IMAGE             KERNEL-VERSION      CONTAINER-RUNTIME
master    Ready    control-plane   10m     v1.29.9   10.4.0.104    <none>        Ubuntu 20.04.6 LTS   5.15.0-1046-azure   cri-o://1.23.5
worker1   Ready    <none>          7m30s   v1.29.9   10.4.0.140    <none>        Ubuntu 20.04.6 LTS   5.15.0-1046-azure   cri-o://1.23.5
worker2   Ready    <none>          7m56s   v1.29.9   10.4.0.172    <none>        Ubuntu 20.04.6 LTS   5.15.0-1046-azure   cri-o://1.23.5
root@master:~#
```


