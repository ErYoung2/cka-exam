#### Tasks
1. Create a new NetworkPolicy named allow-port-from-namespace, allows Pods in the existing namespace internal to connect to port 9000 of other pods in the same namespace.
2. Ensure the NetworkPolicy:
   - doesn't allow to pods not listening on port 9000
   - doesn't allow access from pods not in namespace internal 

#### Commands
1. Create a yaml file NetworkPolicy.yaml(ref from official site)
```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-port-from-namespace
  namespace: internal
spec:
  ingress:
  - from:
    - podSelector: {}
    ports:
    - port: 9000
      protocol: TCP
  podSelector: {}
  policyTypes:
  - Ingress
```

2. Apply this yaml file
kubectl apply -f NetworkPolicy.yaml

#### Ref Doc
> https://kubernetes.io/docs/concepts/services-networking/network-policies/