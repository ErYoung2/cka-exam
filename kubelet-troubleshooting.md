### Task
1. Node wk8s-node-0 is NotReady, make some steps to make it Ready.

### Command
ssh wk8s-node-0
sudo -i
systemctl enable --now kubelet

## Ref Doc
> https://kubernetes.io/docs/tasks/configure-pod-container/static-pod/