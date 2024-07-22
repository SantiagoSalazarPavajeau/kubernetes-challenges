# kubernetes-challenges

# deploy pod
kubectl run nginx-pod -image:ngnix:alpine

# verify pod
kubectl describe pod nginx-pod

# deploy pod with label
kubectl run messaging --image:redis:alpine --labels="tier=msg"

# verify pod
kubectl get pod
kubectl describe pod messaging

# create namespace
kubectl create namespace dev

# verify namespace
kubectl get ns

# get all nodes
kubectl get nodes -o json > /all_nodes.json
cat /all_nodes.json

# create a service 
kubectl expose pod messaging - port 6379 --name messaging-service

# verify service
kubectl get svc
kubectl describe svc messaging-service

# verify endpoint
kubectl get pods -o wide

# create a deployment
kubectl create deployment hr-web-app --image=kodecloud/webapp-color --replicas=2

# verify a deployment
kubctl get deploy
kubectl describe deploy hr-web-app

# create pod that does not get destroyed (sleep) and is managed by kubelet on local node instead of kubernetes api on management server
kubctl run static-busybox --image=busybox --dry-run=client -o yaml --command -- sleep 1000 > static-busybox.yaml

# verify file
cat static-busybox.yaml

# move file to dir for it to be implemented
mv static-busyboc.yaml /etc/kubernetes/manifests/

# verify pod
kubctl get pods
kubectl describe pod static-busybox-controller

# create pod on specific namespace
kubectl run temp-bus --image=redis:alpine -n finance

# verify pod on specific namespace
kubectl get pod -n finance
kubectl describe pod temo-bus -n finance

# check logs on pod/container
kubectl logs orange init-myservice

# edit a pod to fix issue
kubectl edit pod orange
kubectl replace --force -f /tmp/kubectl-edit-abd.yaml

# verify issue is fixed
kubectl get pods --watch

# expose deployment 
kubectl expose deploy hr-web-app --name=hr-web-app-service --type NodePort --port 8080

# set nodeport to 30082 (access from outside cluster)
kubectl edit svc hr-web-app-service

# get os info from nodes with jsonpath query
kubectl get nodes -o jsonpath='{.items[*].status.nodeInfo.osImage} > /opt/outputs/nodes_os_list.txt

# create a persistent volume
vi pv.yaml
kubectl create -f pv.yaml

# verify persistent volume
kubctl get pv
kubectl describe pv pv-analytics









