# Flux Setup Instructions

1) Create GitHub account

Note your username, which will be referred to later as `YOUR_USERNAME` below.

2) Clone repo

```
git clone https://github.com/ContainerSolutions/gitops-training-lab
cd gitops-training-lab
```

3) Gain access to Kubernetes cluster

Some options for creating a cluster:

- Minikube

- AWS / GKE / Azure

- MicroK8s

Whichever you use, you need to end up with admin-level `kubectl` access from the command line.

You can check this is working with:

```
kubectl cluster-info
```

4) Set up flux

Follow instructions [here, from 'set up flux' to the end of the page](https://docs.fluxcd.io/en/1.19.0/tutorials/get-started/)

NOTE: that there is no `PODINFO_UI_MESSAGE` in the `podinfo-dep.yaml` file. Add, rather than change it.
