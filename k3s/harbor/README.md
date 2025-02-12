Harbor  version: harbor-1.16.0.tgz

# Prerequisite
Ensure the NFS folder is created before installaing Harbor in the Kubernetes cluster.
Log in to the NFS server and set up the Harbor folder for persistent storage.

$ sudo chown nobody:nogroup harbor
$ sudo chmod 777 harbor

# Install Harbor
$ kubectl create namespace harbor
$ kubectl create secret tls domain-cert --cert=domain-name.crt --key=domain-name.key  -n harbor
$ kubectl apply -f harbor-pv.yaml
$ kubectl apply -f harbor-pvc.yaml
$ cd harbor 
$ helm install harbor -f values.yaml . -n harbor

# Uninstall Harbor
$ helm uninstall harbor -n harbor
