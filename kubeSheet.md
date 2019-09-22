### Kubernetes CheetSheet

1. kubectl get pod -n kube-system -o wide
2. kubectl get svc -o wide
3. kubectl get po -L env # getting the pods with the label selector
4. kubectl get nodes
5. kubectl get componentstatus
6. kubectl cluster-info 
7. kubectl create namespace "my-ns"
8. kubectl -n my-ns create -f deployment.yml
9. kubectl get pods -o custom-columns=POD:metadata.name,NODE:spec.nodeName --sort-by spec.nodeName -n kube-system
10. sudo apt-mark unhold kubeadm kubelet 

11. kubectl version --short 
# return the client(kubectl version ) and server version(kube-apiserver version)

12. sudo kubeadm upgrade plam # for upgrading the contrpol plan compo
13. kubectl drain [node_name] --ignore-daemonsets # for evicting all of the pods from a node
14. kubectl uncordon [node_name] # for rescheduling of the pods on that nodes

15. kubeadm token list # getting all of the token list
16. kubeadm token generate # generating a new token for node for joining the cluster
17. kubeadm token create <generated-token> --ttl 2h --print-joint-command


curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -

cat << EOF | sudo tee /etc/apt/sources.list.d/kubernetes.list
deb https://apt.kubernetes.io/ kubernetes-xenial main
EOF


sudo apt-get update

sudo apt-get install -y docker-ce=18.06.1ce3-0~ubuntu kubelet=1.12.7-00 kubeadm=1.12.7-00 kubectl=1.12.7-00

sudo apt-mark hold docker-ce kubelet kubeadm kubectl



sudo kubeadm join 10.0.1.118:6443 --token u1hgnw.diktxwouv9o1kyd9 --discovery-token-ca-cert-hash sha256:9e9f555229a022710933d07901d99f21b81ac8cae52fa6511e1809f12f910408
kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml

ssh cloud_user@3.231.33.248



