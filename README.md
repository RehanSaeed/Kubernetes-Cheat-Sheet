# Kubernetes Cheat Sheet

 A cheat sheet for Kubernetes commands.

## Get Commands

Add the `-w` switch to any command to watch for changes.

```
kubectl get pods -o wide
kubectl get rs -o wide
kubectl get svc kuard
kubectl get endpoints kuard -o wide
```

## Create Pod

```
kubectl run kuard --generator=run-pod/v1 --image=gcr.io/kuar-demo/kuard-amd64:1 -o yaml --dry-run > kuard-pod.yml
kubectl apply -f kuard-pod.yml
```

## Create Deployment

kubectl run kuard --image=gcr.io/kuar-demo/kuard-amd64:1 -o yaml --dry-run > kuard-deployment.yml
kubectl apply -f kuard-deployment.yml

## Create Service

kubectl expose deployment kuard --port 8080 --target-port=8080 -o yaml --dry-run > kuard-service.yml
kubectl apply -f kuard-service.yml