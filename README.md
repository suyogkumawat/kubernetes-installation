# kubernetes-installation

##Check iptables rules related to KUBE-SERVICES:
sudo iptables -t nat -L -n | grep KUBE


##Is kube-proxy running?
##On each worker node, check:


ps -ef | grep kube-proxy


##Mini-project: To understand how to add the configuration

###Use kubectl exec to enter the pod and run the redis-cli tool to check the current configuration:

kubectl exec -it redis -- redis-cli

127.0.0.1:6379> CONFIG GET maxmemory

127.0.0.1:6379> CONFIG GET maxmemory-policy

###Add the data now

apiVersion: v1
kind: ConfigMap
metadata:
  name: example-redis-config
data:
  redis-config: |
    maxmemory 2mb
    maxmemory-policy allkeys-lru    

##The configuration values have not changed because the Pod needs to be restarted to grab updated values from associated ConfigMaps. Let's delete and recreate the Pod:

kubectl delete pod redis
kubectl apply -f redis-pod.yml

###Some More commands for containerd
sudo ctr -n k8s.io images ls
sudo crictl ps -a
