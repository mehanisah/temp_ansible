Harbor  version: harbor-1.16.0.tgz

$ grep "version:" Chart.yaml
version: 1.16.0

# Install
$ kubectl create namespace harbor
$ kubectl create secret tls domain-cert --cert=domain-name.crt --key=domain-name.key  -n harbor
$ kubectl apply -f harbor-pv.yaml
$ kubectl apply -f harbor-pvc.yaml
$ cd harbor && helm install harbor harbor/harbor -f values.yaml

# Uninstall
$ helm uninstall harbor -n harbor
