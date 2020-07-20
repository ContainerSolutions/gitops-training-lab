# General Setup Instructions

1) Create GitHub account

Note your username, which will be referred to later as `YOUR_USERNAME` below.

2) Clone repo

```
git clone https://github.com/ContainerSolutions/gitops-training-lab
cd gitops-training-lab
```

3) Gain access to Kubernetes cluster

Some options for creating a cluster:

- Docker Desktop

- Minikube

- AWS / GKE / Azure

- MicroK8s

Whichever you use, you need to end up with admin-level `kubectl` access from the command line.

You can check this is working with:

```
kubectl cluster-info
```
