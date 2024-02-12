### Task
1. Specify port 80(HTTP) on existing deployment via http.
2. Create a new service(front-end-svc) to expose the container port http, use Nodeport type.


### Command
kubectl config use-context k8s
kubectl edit deploy front-end, add ports info.
```yaml
name: nginx
ports:
- containerPort: 80
  name: http
  protocol: TCP
```
kubectl expose deploy front-end --name=front-end-svc --port=80 --target-port=http --type=NodePort

### ref doc
> https://kubernetes.io/docs/tutorials/services/connect-applications-service/