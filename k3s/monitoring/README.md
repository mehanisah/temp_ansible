# Install
```
helm search repo prometheus-community/prometheus --versions

# helm pull prometheus-community/prometheus --version 27.5.1

helm upgrade prometheus prometheus-community/prometheus  \
  --version 27.5.1 \
  --namespace monitoring \
  --set server.ingress.enabled=true \
  --set server.ingress.ingressClassName=nginx \
  --set server.ingress.hosts[0]=prometheus.scm.stg \
  --set server.ingress.tls[0].hosts[0]=prometheus.scm.stg \
  --set server.ingress.tls[0].secretName=scm-stg-cert \
  --set server.persistentVolume.enabled=true \
  --set server.persistentVolume.accessModes[0]=ReadWriteMany \
  --set server.persistentVolume.storageClass=nfs-client \
  --set server.persistentVolume.size=20Gi\
  --set alertmanager.enabled=false
```

# Uninstall
```
helm uninstall prometheus -n monitoring
```
