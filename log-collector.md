### Task
1. Get error unable-to-access-website logs from pod foobar and redirect to path /opt/KUTR00101/foobar

### Command
kubectl logs foobar|grep unable-to-access-website > /opt/KUTR00101/foobar