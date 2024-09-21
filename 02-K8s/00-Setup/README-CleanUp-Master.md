

## In case API Server is giving you errors, then please follow the below command for clean up: 

```
   42  kubectl  get nodes
   45  systemctl stop kubelet
   46  systemctl status  kubelet
   47  crictl ps
   48  crictl ps -q
   50  crictl stop $(crictl ps -q)
   52  crictl rm  $(crictl ps -qa)
   53  crictl ps -a
   54  rm -rf  /etc/kubernetes/*
   56  rm -rf /var/lib/etcd/*
   58  rm -rf /var/lib/kubelet/*
```

## Now you can do the re-installation
```

   60  cd docker-k8s-ey-14-Sept-2024/
   62  cd 02-K8s/
   64  cd 00-Setup/
   66  cat install-k8s-master-node.sh
```
