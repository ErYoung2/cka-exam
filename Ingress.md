### Task
1. Create a new nginx ingress as follows:
- Name: pong
- Namespace: ing-internal
- Exposing service hi on path /hi using service port 5678


### Command
kubectl config use-context k8s
Edit config file ingress.yaml
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: pong
  namespace: ing-internal
spec:
  ingressClassName: nginx-example
  rules:
  - http:
      paths:
      - path: /hi
        pathType: Prefix
        backend:
          service:
            name: hi
            port:
              number: 5678
```
kubectl apply -f ingress.yaml
curl -kL <internal-ip>/hi

### ref doc
> https://kubernetes.io/docs/concepts/services-networking/ingress/