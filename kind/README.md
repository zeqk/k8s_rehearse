# K8S Rehearse with KIND

## Installing 

https://kind.sigs.k8s.io/docs/user/quick-start/

## Commands

```
kind --help
```

```bash
sudo kind create cluster --kubeconfig .kube/config --name k8s-rehearse1  --image kindest/node:v1.17.17
```


```bash
sudo kind create cluster --config kind.yml --kubeconfig .kube/config --name k8s-rehearse2
```

```
sudo kind delete cluster --name k8s-rehearse2
```

## My errors

## Failed to creat cluster

```
ERROR: failed to create cluster: failed to init node with kubeadm: command "docker exec --privileged kind-control-plane kubeadm init --ignore-preflight-errors=all --config=/kind/kubeadm.conf --skip-token-print --v=6" failed with error: exit status
```

### Aproach 1: Increase WSL memory 

https://github.com/kubernetes-sigs/kind/issues/1437#issuecomment-865253504

I'am using WSL 2, I was limited the WSL2 memory to 5GB, and [kind require at least 8GB of memory](https://kind.sigs.k8s.io/docs/user/using-wsl2/#installing-on-a-virtual-machine)

```powershell
code %UserProfile%\.wslconfig
```

`.wslconfig`
```
[wsl2]
memory=9GB   # Limits VM memory in WSL 2 up to 3GB
```

```powershell
wsl.exe --shutdown
```

## Aproach 2: 


https://github.com/kubernetes-sigs/kind/issues/2323

Use image `kindest/node:v1.17.17`

```bash
sudo kind create cluster --kubeconfig .kube/config --name k8s-rehearse1  --image kindest/node:v1.17.17
```
