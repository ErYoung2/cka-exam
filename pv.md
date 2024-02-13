### Task
1. Create a pv, name app-config, capacity 2GiB, ReadWriteMany, volume type is hostPath, location is /srv/app-config.

### Command
Create yaml file 12.yaml
```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: app-config
  labels:
    type: local
spec:
  capacity:
    storage: 2Gi
  accessModes:
    - ReadWriteMany
  hostPath:
    path: "/srv/app-config"
```

kubectl apply -f 12.yaml



### ref doc
> https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/