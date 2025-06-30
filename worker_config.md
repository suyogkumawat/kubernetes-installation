## Perform pre-flight checks:
```bash
sudo kubeadm reset pre-flight checks
```

## Paste the join command you got from the master node and append --v=5 at the end: Example:

sudo kubeadm join <private-ip-of-control-plane>:6443 --token <token> --discovery-token-ca-cert-hash sha256:<hash> --cri-socket 
"unix:///run/containerd/containerd.sock" --v=5
#Note: When pasting the join command from the master node:

Add sudo at the beginning of the command
Add --v=5 at the end
Example format:

```bash
sudo <paste-join-command-here> --v=5
```
