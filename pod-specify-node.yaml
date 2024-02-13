### Task
1. Schedule a pod nginx-kusc00401 to node selector is spinning


### Command
1. Create 9.yaml
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-kusc00401
spec:
  containers:
  - name: nginx
    image: nginx
    imagePullPolicy: IfNotPresent
  nodeSelector:
    disk: spinning
```
kubectl apply -f 9.yaml


### ref doc
> https://kubernetes.io/docs/tasks/configure-pod-container/assign-pods-nodes/