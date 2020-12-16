# KubeSim

A simulator of Kubernetes for batch and offline workload.

Kubesim is based on kubemark on kubernetes `release-1.18`, tag `v1.18.6`, commit  `dff82dc0de47299ab66c83c626e08b245ab19037`

## Quick start
1. create `kubesim` namespace
```
kubectl create ns kubesim
```

2. create comfig map `node-configmap`
```
kubectl create configmap node-configmap -n kubesim --from-literal=content.type="test-cluster"
```

3. create secret `kubeconfig`
```
kubectl create secret generic kubeconfig --type=Opaque --namespace=kubesim --from-file=kubelet.kubeconfig={{kubeconfig_file_path}} --from-file=kubeproxy.kubeconfig={{kubeconfig_file_path}}
```

4. deploy kubesim
```
kubectl apply -f ./example/kubesim-cm.yaml
kubectl apply -f ./example/kubesim-rc.yaml
```
