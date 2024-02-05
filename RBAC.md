1. Create a new clusterrole named deployment-clusterrole, only deployment/statefulset/daemonset can be created.
2. Create a new serviceaccount named cicd-token in the existing app-team1.
3. Bind the new clusterrole deployment-clusterrole to the new serviceaccount cicd-token, limited to the namespace app-team1.

#### Command
kubectl create clusterrole deployment-clusterrole --verb=create--resource=deployments,statefulsets,daemonsets  
kubectl create serviceaccount cicd-token -n app-team1
kubectl create rolebinding cicd-token-binding --clusterrole=deployment-clusterrole --serviceaccount=app-team1:cicd-token --namespace=cicd-token

#### YAML
```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  # "namespace" omitted since ClusterRoles are not namespaced
  name: deployment-clusterrole
rules:
- apiGroups: [""]
  #
  # at the HTTP level, the name of the resource for accessing Secret
  # objects is "secrets"
  resources: ["deployments", "statefulsets", "daemonsets"]
  verbs: ["create"]
```

```yaml for reference
apiVersion: rbac.authorization.k8s.io/v1
# This role binding allows "dave" to read secrets in the "development" namespace.
# You need to already have a ClusterRole named "secret-reader".
kind: RoleBinding
metadata:
  name: cicd-token
  #
  # The namespace of the RoleBinding determines where the permissions are granted.
  # This only grants permissions within the "development" namespace.
  namespace: app-team1
subjects:
- kind: User
  name: dave # Name is case sensitive
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: ClusterRole
  name: secret-reader
  apiGroup: rbac.authorization.k8s.io
```

Ref doc:
> https://kubernetes.io/docs/reference/kubectl/generated/kubectl_create/kubectl_create_clusterrole/

