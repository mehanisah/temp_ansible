$ helm install nfs-subdir-external-provisioner nfs-subdir-external-provisioner/nfs-subdir-external-provisioner \
  --set nfs.server=43.74.40.116 \
  --set nfs.path=/srv/nfs/k3s-stg

OR

helm install nfs-subdir-external-provisioner nfs-subdir-external-provisioner/nfs-subdir-external-provisioner \
  --set nfs.server=43.74.40.116 \
  --set nfs.path=/srv/nfs/k3s-stg \
  --set storageClass.isDefaultClass=true

$ kubectl get pods
NAME                                               READY   STATUS    RESTARTS   AGE
nfs-subdir-external-provisioner-85dfb4fcd6-fdbm4   1/1     Running   0          27s

$ kubectl get sc
NAME         PROVISIONER                                     RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
nfs-client   cluster.local/nfs-subdir-external-provisioner   Delete          Immediate        

$ helm uninstall nfs-subdir-external-provisioner
