
$ helm install kubernetes-dashboard . --namespace kubernetes-dashboard -f values.yaml
$ helm upgrade kubernetes-dashboard . --namespace kubernetes-dashboard -f values.yaml
$ helm uninstall kubernetes-dashboard --namespace kubernetes-dashboard


$ kubectl create -f k8s-dashboard-account.yaml
serviceaccount/admin-user created
clusterrolebinding.rbac.authorization.k8s.io/admin-user created

$ kubectl -n kube-system create token admin-user

