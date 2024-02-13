### Task
1. Get the cluster ready nodes(NoSchedule nodes excluded) and output the number in /opt/KUSC00402/kusc00402.txt


### Command
kubectl get nodes|grep Ready|grep -v NoSchedule|wc -l >> /opt/KUSC00402/kusc00402.txt
