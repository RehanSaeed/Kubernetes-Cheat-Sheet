# Kubernetes Cheat Sheet

 A cheat sheet for Kubernetes commands.

## Get Commands

```
kubectl get nodes
kubectl get pods
kubectl get rs
kubectl get svc kuard
kubectl get endpoints kuard
```

Additional switches that can be added to the above commands:

- `-o wide` - Show more information.
- `-w` - watch for changes.

## Describe Command

```
kubectl describe nodes [id]
kubectl describe pods [id]
kubectl describe rs [id]
kubectl describe svc kuard [id]
kubectl describe endpoints kuard [id]
```

## Delete Command


```
kubectl delete nodes [id]
kubectl delete pods [id]
kubectl delete rs [id]
kubectl delete svc kuard [id]
kubectl delete endpoints kuard [id]
```

## Create vs Apply

`kubectl create` can be used to create new resources while `kubectl apply` inserts or updates resources while maintaining any manual changes made like scaling pods.

## Create Pod

```
kubectl run kuard --generator=run-pod/v1 --image=gcr.io/kuar-demo/kuard-amd64:1 -o yaml --dry-run > kuard-pod.yml
kubectl apply -f kuard-pod.yml
```

## Create Deployment

```
kubectl run kuard --image=gcr.io/kuar-demo/kuard-amd64:1 -o yaml --dry-run > kuard-deployment.yml
kubectl apply -f kuard-deployment.yml
```

## Create Service

```
kubectl expose deployment kuard --port 8080 --target-port=8080 -o yaml --dry-run > kuard-service.yml
kubectl apply -f kuard-service.yml
```

## Export YAML for New Pod

```
kubectl run my-cool-app —-image=me/my-cool-app:v1 -o yaml --dry-run > my-cool-app.yaml
```

## Export YAML for Existing Object

```
kubectl get deployment my-cool-app -o yaml --export > my-cool-app.yaml
```
