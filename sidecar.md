### Task
1. Add a busybox sidecar container to the existing pod legacy-app, the new sidecar container will run the following command:
```shell
/bin/sh -c tail -n+1 -f /var/log/legacy-app.log
```
2. Use a volume mount named logs to make the file /var/log/legacy-app.log available to the sidecar container.

Notes:
- Don't modify the existing container.
- Don't modify the path of the log file, both containers.
- Must access it at /var/log/legacy-app.log

### Command
kubectl get pod legacy-app -o yaml > 15.yaml
Edit 15.yaml, add sidecar things.
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: legacy-app
spec:
  containers:
  - name: count-log-1
    image: busybox:1.28
    args: [/bin/sh, -c, 'tail -n+1 -F /var/log/1.log']
    volumeMounts:
    - name: varlog
      mountPath: /var/log
  - name: count-log-2
    image: busybox:1.28
    args: [/bin/sh, -c, 'tail -n+1 -F /var/log/2.log']
    volumeMounts:
    - name: varlog
      mountPath: /var/log
  - name: busybox
    image: busybox:1.28
    args: ["/bin/sh","-c","tail -n+1 -F /var/log/legacy-app.log"]    
    volumeMounts:
    - name: logs
      mountPath: /var/log
  volumes:
  - name: logs
    emptyDir: {}
```

kubectl apply -f 15.yaml



### ref doc
> https://kubernetes.io/docs/concepts/cluster-administration/logging/