1. Create a new clusterrole named deployment-clusterrole, only deployment/statefulset/daemonset can be created.
2. Create a new serviceaccount named cicd-token in the existing app-team1.
3. Bind the new clusterrole deployment-clusterrole to the new serviceaccount cicd-token, limited to the namespace app-team1.


kubectl create clusterrole deployment-clusterrole --verb=create,get,list --resource=deployments,statefulsets,daemonsets 
kubectl create serviceaccount cicd-token -n app-team1
kubectl create rolebinding cicd-token-binding --clusterrole=deployment-clusterrole --serviceaccount=app-team1:cicd-token --namespace=cicd-token


Ref doc:
> https://kubernetes.io/docs/reference/kubectl/generated/kubectl_create/kubectl_create_clusterrole/

