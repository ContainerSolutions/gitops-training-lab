# GitOps Training Lab

Part of the GitOps training materials for Container Solutions

## Pre-Requisites

1) Access to a Kubernetes cluster with admin privileges.

Ideally, the cluster will be newly-created with no applications or non-standard operators running on it.

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

2) Set up GitHub ccount

Note your username, which will be referred to later as `YOUR_USERNAME` (or similar).

3) Clone this repo

```
git clone https://github.com/ContainerSolutions/gitops-training-lab
cd gitops-training-lab
```

## Flux Walkthrough and Challenges

See `flux/`

## ArgoCD Walkthrough and Challenges

See `argocd/`
