
1) Go to UI

https://localhost:8080

2) Set up repo

Go to Application => New

```
Application Name: argocd-demo
Project: default
Sync Policy: Automatic
   Prune TICK
   Self-heal TICK
Repository URL: https://github.com/ianmiell/argocd-example-apps
Revision: HEAD
Path: guestbook
Cluster: https://kubernetes.default.svc
Namespace: default   # TODO: can it be new?
Click CREATE
```

Wait for deployment, show pod, service, argocd logs.

3) Add a new namespace

Create a file and put it in the repo:

```
---
apiVersion: v1
kind: Namespace
metadata:
  name: namespace-namespace
```

Commit and push it. Wait for ArgoCD to update, or click refresh.

Namespace was added.

4) Delete the namespace

Remove the namespace, commit and push.

Commit and push it. Wait for ArgoCD to update, or click refresh.

Namespace was removed.
