## kubeadm init

kubeadm init --kubernetes-version=1.31.0 \
--pod-network-cidr 192.168.0.0/16 \
--ignore-preflight-errors=NumCPU \
--ignore-preflight-errors=Mem

# kubeadm join

kubeadm join 172.30.1.2:6443 --token abc \
        --discovery-token-ca-cert-hash sha256:abc
