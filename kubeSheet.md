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

12. sudo kubeadm upgrade plan # for upgrading the contrpol plan compo
13. kubectl drain [node_name] --ignore-daemonsets # for evicting all of the pods from a node
14. kubectl uncordon [node_name] # for rescheduling of the pods on that nodes

15. kubeadm token list # getting all of the token list
16. kubeadm token generate # generating a new token for node for joining the cluster
17. kubeadm token create <generated-token> --ttl 2h --print-joint-command
18. kubectl get endpoints, svc
19. kubectl logs <pods-name>
20. kubectl run nginx --image=nginx # creating an nginx deployment  
21. kubectl scale deployments nginx --replicas=2
22. kubectl port forward
23. kubect expose deployment nginx --port 80 --type NodePort



