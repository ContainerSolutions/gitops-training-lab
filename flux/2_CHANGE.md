1) Show logs

Show and talk through the flux logs

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

