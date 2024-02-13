### Task
1. Create a pod including nginx+redis+memcached+consul


### Command
1. Create 11.yaml
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: kuccl
spec:
  containers:
  - name: nginx
    image: nginx
  - name: redis
    image: redis
  - name: memcached
    image: memcached
  - name: consul
    image: consul
```
kubectl apply -f 11.yaml


### ref doc
> https://kubernetes.io/docs/tasks/configure-pod-container/assign-pods-nodes/