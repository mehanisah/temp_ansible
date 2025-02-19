# Install NFS Provisioner

$ helm install nfs-subdir-external-provisioner nfs-subdir-external-provisioner/nfs-subdir-external-provisioner \
  --set nfs.server=xx.xx.xx.xx \
  --set nfs.path=/srv/nfs/k3s-stg

$ kubectl get pods
NAME                                               READY   STATUS    RESTARTS   AGE
nfs-subdir-external-provisioner-85dfb4fcd6-fdbm4   1/1     Running   0          27s

$ kubectl get sc
NAME         PROVISIONER                                     RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
nfs-client   cluster.local/nfs-subdir-external-provisioner   Delete          Immediate    

# Set as default sc
$ kubectl patch sc nfs-client -p '{"metadata": {"annotations": {"storageclass.kubernetes.io/is-default-class": "true"}}}'

# Uninstall NFS Provisioner
$ helm uninstall nfs-subdir-external-provisioner
