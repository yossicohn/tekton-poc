# tekton-poc

This example shows how to use the git-clone task from the Tekton (Catalog)[https://github.com/tektoncd/catalog].
We will do it with:
- Secret
- Service Account
- Persistance Volume and Claim

Create in your minikube mounting point for the K8S PVC:
```
minikube ssh
cd /mnt/data
```


Create Secrets and Service Account
```
kubectl apply -f git-secret.yaml
kubectl apply -f serviceaccount.yaml

```

Create Persistance Volume and Claim

```
kubectl apply -f pv-claim.yaml
kubectl apply -f pv-volume.yaml
```

Apply the git-clone from the catalog
```
kubectl apply -f https://github.com/tektoncd/catalog/blob/master/task/git-clone/0.2/git-clone.yaml
```

Create Pipeline and Pipelinerun

```
kubectl create -f git-clone-checking-out-a-branch-secret.yaml
```
