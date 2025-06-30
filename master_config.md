## Initialize the Cluster:
```bash
sudo kubeadm init
```
## Set Up Local kubeconfig:
```bash
mkdir -p "$HOME"/.kube
sudo cp -i /etc/kubernetes/admin.conf "$HOME"/.kube/config
sudo chown "$(id -u)":"$(id -g)" "$HOME"/.kube/config
```

## Install a Network Plugin (Calico):
```bash
kubectl apply -f https://raw.githubusercontent.com/projectcalico/calico/v3.26.0/manifests/calico.yaml
```

## Generate Join Command:
```bash
kubeadm token create --print-join-command
```
### Copy this generated token for next command.
