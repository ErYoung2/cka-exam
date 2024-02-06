### Task
1. Unavailable node ek8s-node-1 and reschedule pods

### Command
kubectl config use-context ek8s
kubectl condon ek8s-node-1 ## set the node as unavailable
kubectl drain ek8s-node-1 --delete-emptydir-data --ignore-daemonsets --force ## schedule the pods away from this node

### ref doc
> https://kubernetes.io/docs/reference/kubectl/generated/kubectl_cordon/
> https://kubernetes.io/docs/tasks/administer-cluster/safely-drain-node/
> https://kubernetes.io/docs/reference/kubectl/generated/kubectl_drain/