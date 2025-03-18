# Prerequiste
Configure NFS Server settings, allow mount from all nodes.
```
cat /etc/exports
/srv/nfs/k3s-stg *(rw,sync,no_subtree_check)
```
Nodes that will be using NFS storage needs to be install with nfs-common
```
sudo apt update && sudo apt install -y nfs-common
```

# Install NFS Provisioner

Installation is done in the default namespace.
```
$ helm repo add nfs-subdir-external-provisioner https://kubernetes-sigs.github.io/nfs-subdir-external-provisioner/
$ helm install nfs-subdir-external-provisioner nfs-subdir-external-provisioner/nfs-subdir-external-provisioner \
   --version 4.0.18 \
  --set nfs.server=xx.xx.xx.xx \
  --set nfs.path=<NFS_PATH>
```

```
$ kubectl get pods  
NAME                                               READY   STATUS    RESTARTS   AGE
nfs-subdir-external-provisioner-85dfb4fcd6-fdbm4   1/1     Running   0          27s
```

```
$ kubectl get sc  
NAME         PROVISIONER                                     RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE  
nfs-client   cluster.local/nfs-subdir-external-provisioner   Delete          Immediate    
```

# Set as default sc
```
$ kubectl patch sc nfs-client -p '{"metadata": {"annotations": {"storageclass.kubernetes.io/is-default-class": "true"}}}'
```

# Uninstall NFS Provisioner
```
$ helm uninstall nfs-subdir-external-provisioner
```
