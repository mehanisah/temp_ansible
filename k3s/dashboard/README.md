Prerequisite:
1. Create 'kubernetes-dashboard' namespace
2. Create TLS secret for 'kubernetes-dashboard' namespace

# Install
$ cd kubernetes-dashboard/
$ helm install kubernetes-dashboard . --namespace kubernetes-dashboard -f values.yaml

# Upgrade
$ cd kubernetes-dashboard/
$ helm upgrade kubernetes-dashboard . --namespace kubernetes-dashboard -f values.yaml

# Uninstall
$ helm uninstall kubernetes-dashboard --namespace kubernetes-dashboard

# Create service account
$ kubectl create -f service-account-k8s-dashboard.yaml

# Create cluster role binding
$ kubectl -f cluster-role-binding-k8s-dashboard.yaml

# Create token
$ kubectl -n kubernetes-dashboard create token admin-user

