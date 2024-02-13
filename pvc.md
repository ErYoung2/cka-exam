### Task
1. Create a pvc:
- Name: pv-volume
- Class: csi-hostpath-sc
- Capacity: 10Mi

2. Create a new pod which mounts the pvc as a volume, configure the new pod to have ReadWriteOnce access on the volume.
- Name: web-server
- Image: Nginx
- Mount Point: /usr/share/nginx/html

3. Use kubectl edit or kubectl patch to expand the pvc capacity to 70Mi.

### Command
Create yaml file 13.yaml
```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: pv-volume
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 10Mi
```

kubectl apply -f 13.yaml

Create yaml file 13-pod.yaml
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: web-server
spec:
  volumes:
    - name: pv-volume
      persistentVolumeClaim:
        claimName: pv-volume
  containers:
    - name: nginx
      image: nginx
      volumeMounts:
        - mountPath: "/usr/share/nginx/html"
          name: pv-volume
```

kubectl apply -f 13-pod.yaml

kubectl edit pvc pv-volume, change storage to 70Mi

Or:
kubectl patch pvc pv-volume -p xxx


### ref doc
> https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/