# Flux

These are the instruction to follow on this taster.

## Flux Setup

1) Set up flux

Follow instructions [here, from 'set up flux' to the end of the page](https://docs.fluxcd.io/en/1.19.0/tutorials/get-started-helm/)

1.1) Summary of commands

EXAMPLE commands in `./setup.sh` for convenience

Take outputted key and go to https://github.com/YOURUSER/flux-get-started/settings/keys/new and paste the key there with R/W access.

This allows Helm charts to be deployed.

## Flux Walkthrough

1) Show logs

View flux logs

```
flux/flux-*
```

2) Speed up cycle

Edit deployment/flux

change references to 5m to 1m

3) Clone repo

```
git clone git@github.com:GH_USERNAME/flux-get-started
cd flux-get-started
```

4) Commit a small change

https://docs.fluxcd.io/en/1.19.0/tutorials/get-started-helm/#committing-a-small-change

```
diff --git a/releases/mongodb.yaml b/releases/mongodb.yaml
index 369ef19..98692ca 100644
--- a/releases/mongodb.yaml
+++ b/releases/mongodb.yaml
@@ -16,7 +16,7 @@ spec:
   values:
     image:
       repository: bitnami/mongodb
-      tag: 4.0.13
+      tag: 4.0.14
```

and push it.

5) Wait for mongodb

Check flux logs.

Check mongodb pods showing in demo namespace.

6) Fix bug

Push this change:

```
diff --git a/releases/mongodb.yaml b/releases/mongodb.yaml
index 98692ca..86c1edd 100644
--- a/releases/mongodb.yaml
+++ b/releases/mongodb.yaml
@@ -23,4 +23,4 @@ spec:
     securityContext:
       enabled: true
       fsGroup: 0
-      runAsUser: 0
+      #runAsUser: 0
```

## Flux Challenges

- Create a new namespace

- Add an application deployment to it (ie a Kubernetes deployment)

- Add a helm application deployment
