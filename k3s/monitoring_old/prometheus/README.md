
Github: https://github.com/prometheus-community/helm-charts

Promethues version: prometheus-27.2.0.tgz

$ grep "version:" Chart.yaml
version: 27.2.0

# Add repo
$ helm repo add prometheus-community https://prometheus-community.github.io/helm-charts

$ helm search repo prometheus
$ helm pull prometheus-community/prometheus --version 27.2.0
$ cd prometheus
$ helm install prometheus prometheus-community/prometheus -f values.yaml -n monitoring
$ helm uninstall prometheus -n monitoring

