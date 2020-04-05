# kube-prometheus

## diff to https://github.com/coreos/kube-prometheus   
### 1.Add kube-controller-manager and kube-scheduler service yaml

### 2.Add etcd service and servicemonitor yaml

### 3.Change image repo `quay.io` to `quay.mirrors.ustc.edu.cn` or `quay.azk8s.cn` for china user

### 4.Prometheus add etcd secrets
```
# kubeadm cluster use this cmd to create etcd secrets 
kubectl -n monitoring create secrets generic etcd-certs --from-file=/etc/kubernetes/pki/etcd/healthcheck-client.crt --from-file=/etc/kubernetes/pki/etcd/healthcheck-client.key --from-file=/etc/kubernetes/pki/etcd/ca.crt

# prometheus-prometheus.yaml
...
  secrets:
  - etcd-certs
...
```
