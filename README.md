# install csi-nfs-driver helm
helm repo add csi-driver-nfs https://raw.githubusercontent.com/kubernetes-csi/csi-driver-nfs/master/charts
helm install my-csi-driver-nfs csi-driver-nfs/csi-driver-nfs --version 4.9.0


# Deploy nfs ganesha
kubectl apply -f nfs-ganesha-deploy.yaml


# Create nfs volumes and apps
kubectl apply -f ngix-pod.yaml


# Mount command change ip to your cluster ip, this is mount to the your nodes (Optional)
mount -t nfs -o nfsvers=4.1 10.110.226.251:/ /mnt/test