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

- Docker Desktop

- Minikube

- AWS / GKE / Azure

- MicroK8s

Whichever you use, you need to end up with admin-level `kubectl` access from the command line.

You can check this is working with:

```
kubectl cluster-info
```

4) Set up flux

Follow instructions [here, from 'set up flux' to the end of the page](https://docs.fluxcd.io/en/1.19.0/tutorials/get-started-helm/)

4.1) Summary of commands

EXAMPLE commands here for convenience:

```
echo -n 'Now input your GitHub username: '
read GHUSER
helm repo add fluxcd https://charts.fluxcd.io
kubectl apply -f https://raw.githubusercontent.com/fluxcd/helm-operator/master/deploy/crds.yaml
kubectl create namespace flux
helm upgrade -i flux fluxcd/flux --set git.url=git@github.com:${GHUSER}/flux-get-started --namespace flux
helm upgrade -i helm-operator fluxcd/helm-operator --set git.ssh.secretName=flux-git-deploy --namespace flux --set helm.versions=v3

kubectl -n flux rollout status deployment/flux
echo SSH KEY:
fluxctl identity --k8s-fwd-ns flux
```

Go to https://github.com/YOURUSER/flux-get-started/settings/keys/new and paste the key there with R/W access.

This allows Helm charts to be deployed.
