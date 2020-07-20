# Flux Setup Instructions

# FORK CODE:
#   https://github.com/argoproj/argocd-example-apps
# Go to UI
# Go to Applications, New:
#   Application Name: argocd-demo
#   Project: default
#   Sync Policy: Automatic
#      Prune TICK
#      Self-heal TICK
#   Repository URL: https://github.com/ianmiell/argocd-example-apps
#   Revision: HEAD
#   Path: guestbook
#   Cluster: https://kubernetes.default.svc
#   Namespace: default   # TODO: can it be new?
#   CREATE
#
#   Wait for deployment, show pod, service, argocd logs
#
#   cp ~/git/kubernetes-examples/namespace/namespace.yaml .
#   git commit -am ns
#   git push
#
#   Refresh application on UI, show namespace is there.
#
#   git rm namespace.yaml
#   git commit -am ns
#
#   Refresh application on UI, show namespace now gone.

1) Set up ArgoCD

Follow instructions [here](https://docs.fluxcd.io/en/1.19.0/tutorials/get-started-helm/://argoproj.github.io/argo-cd/getting_started/)

1.1) Summary of setup

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
argocd account update-password
```

2) Fork repo

https://github.com/argoproj/argocd-example-apps
