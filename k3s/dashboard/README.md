# Add kubernetes-dashboard repository
helm repo add kubernetes-dashboard https://kubernetes.github.io/dashboard/

# Install
$ helm install kubernetes-dashboard . --namespace kubernetes-dashboard -f values.yaml

# Upgrade
$ helm upgrade kubernetes-dashboard . --namespace kubernetes-dashboard -f values.yaml

# Uninstall
$ helm uninstall kubernetes-dashboard --namespace kubernetes-dashboard

# Create service account
$ kubectl create -f k8s-dashboard-account.yaml
serviceaccount/admin-user created
clusterrolebinding.rbac.authorization.k8s.io/admin-user created

# Create token
$ kubectl -n kube-system create token admin-user

