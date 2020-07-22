# ArgoCD Setup Instructions

## 1) Set up ArgoCD

Follow instructions [here](https://argoproj.github.io/argo-cd/getting_started/).

## 2) Summary of setup

Install argocd. See [here](https://argoproj.github.io/argo-cd/getting_started/#2-download-argo-cd-cli)

Fork [repo](https://github.com/argoproj/argocd-example-apps) to your account.

Run:

```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

Wait for pod to come up.
Port-forward the GUI.

```
kubectl port-forward svc/argocd-server -n argocd 8080:443 > /dev/null 2>&1 &
```

Get password and log in:

```
PASS=$(kubectl get pods -n argocd -l app.kubernetes.io/name=argocd-server -o name | cut -d'/' -f 2)
echo $PASS
argocd login localhost:8080 # admin / $PASS
argocd account update-password --server localhost:8080
```

# ArgoCD Walkthrough

## 1) Go to UI

UI is [here](https://localhost:8080)

Skip SSL warning and log in.

## 2) Set up repo

Go to Application => New

```
Application Name: argocd-demo
Project:          default
Sync Policy:      Automatic
   Prune          TICK
   Self-heal      TICK
Repository URL:   https://github.com/YOUR_GH_USER/argocd-example-apps
Revision:         HEAD
Path:             guestbook
Cluster:          https://kubernetes.default.svc
Namespace:        default
Click:            CREATE
Click:            Sync
```
Wait for deployment, show pod, service, argocd logs.

## 3) Clone repo

```
git clone git@github.com:YOUR_GH_USER/argocd-example-apps
```

## 4) Add a new namespace

Create a file and put it in the repo:

```
---
apiVersion: v1
kind: Namespace
metadata:
  name: test-namespace
```

Commit and push it. Wait for ArgoCD to update (up to 3 minutes), or click refresh.

Namespace was added.

## 5) Change an object

Edit the guestbook UI object to change the 'replicas' item from 1 to 2. ArgoCD will revert the change.

## 5) Delete the namespace

Remove the namespace, commit and push.

Wait for ArgoCD to update, or click refresh.

Namespace was removed.
