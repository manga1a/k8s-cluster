# k8s-cluster

spin up three node cluster

- 192.168.33.13 master
- 192.168.33.14 worker-1
- 192.168.33.15 worker-2

see the corresponding post from [here](https://baykara.medium.com/setup-own-kubernetes-cluster-via-virtualbox-99a82605bfcc)

- requirements

```
vagrant
virtualbox
```

Fire up vms

```
vagrant up
```

To access each machine respectively via

```
vagrant ssh master
```

in master node

```
1. set root password
2. switch root account
3. kubeadm init --apiserver-advertise-address 192.168.33.13 --pod-network-cidr=10.244.0.0/16
4. remove --port 0 from /etc/kubernetes/manifests/kube-[controller-api| scheduler].yaml
5. join workers to master node
```

Run `kubectl get cs` before executing 4th step. It may not required if controller-manager and scheduler are healthy already.

for workers

```
vagrant ssh [worker1|worker2]
```

Vagrant help

```
vagrant list-commands
```
