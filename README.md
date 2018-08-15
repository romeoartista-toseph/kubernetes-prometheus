# kubernetes-prometheus

Create `monitoring` namespace
```
$ kubectl create -f prometheus-namespace.yaml
```
---
Get created namespaces
```
$ kubectl get namespaces
```
---
Create `prometheus-config` configmap
```
$ kubectl create -f prometheus-configmap.yaml
```
---
Output created configmap under `monitoring` namespace in YAML format
```
$ kubectl get configmap --namespace=monitoring prometheus-config -o yaml
```
---
Create `prometheus` deployment
```
$ kubectl create -f prometheus-deployment.yaml
```
---
Get created deployments under `monitoring` namespace
```
$ kubectl get deployments --namespace=monitoring
```
---
Create `prometheus` service
```
$ kubectl create -f prometheus-service.yaml
```
---
Output description of `prometheus` service in YAML format
```
$ kubectl get services --namespace=monitoring prometheus -o yaml
```
---
Expose `prometheus` service to localhost to port 9090
```
$ kubectl port-forward <Pod ID> 9090:9090
```
---
Show logs for pod
```
$ kubectl logs <Pod Name> --previous
```
