# kube-prometheus

## diff to https://github.com/coreos/kube-prometheus   
### 1.Add kube-controller-manager and kube-scheduler service yaml

### 2.Add etcd service and servicemonitor yaml

### 3.Change image repo `quay.io` to `quay.mirrors.ustc.edu.cn` or `quay.azk8s.cn` for china user

### 4.Prometheus add etcd secrets
```
# kubeadm cluster use this cmd to create etcd secrets 
kubectl -n monitoring create secret generic etcd-certs --from-file=/etc/kubernetes/pki/etcd/healthcheck-client.crt --from-file=/etc/kubernetes/pki/etcd/healthcheck-client.key --from-file=/etc/kubernetes/pki/etcd/ca.crt

# prometheus-prometheus.yaml
...
  secrets:
  - etcd-certs
...
```

## etcd grafana dashboard

Grafana dashboard：
- https://grafana.com/grafana/dashboards/9733
- https://grafana.com/grafana/dashboards/3070
- https://grafana.com/grafana/dashboards/10859
- https://grafana.com/grafana/dashboards/10323

官方提供dashboard：
- https://github.com/etcd-io/etcd/blob/master/Documentation/op-guide/monitoring.md
- https://github.com/etcd-io/etcd/blob/master/Documentation/op-guide/grafana.json
这里有一个坑，导入grafana前需要将前两行及后最一行括号的去掉
