# Add kubernetes-dashboard repository
$ helm repo add kubernetes-dashboard https://kubernetes.github.io/dashboard/

# Create namespace
$ kubectl apply -f create-namespace-k8s-dashboard.yaml

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

