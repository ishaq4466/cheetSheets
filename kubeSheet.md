### Kubernetes CheetSheet

1. k get pod -n kube-system -o wide
2. k get svc -o wide
3. k get po -L env # getting the pods with the label selector
4. k get nodes 
5. k get componentstatus
6. k cluster-info 
7. k create namespace "my-ns"
8. k -n my-ns create -f deployment.yml
9. k get pods -o custom-columns=POD:metadata.name,NODE:spec.nodeName --sort-by spec.nodeName -n kube-system
10. sudo apt-mark unhold kubeadm kubelet 
11. k version --short # return the client(k version ) and server version(kube-apiserver version)

12. sudo kubeadm upgrade plan # for upgrading the contrpol plan compo
13. k drain [node_name] --ignore-daemonsets # for evicting all of the pods from a node
14. k uncordon [node_name] # for rescheduling of the pods on that nodes

15. kubeadm token list # getting all of the token list
16. kubeadm token generate # generating a new token for node for joining the cluster
17. kubeadm token create <generated-token> --ttl 2h --print-joint-command
18. k get endpoints, svc
19. k logs <pods-name>
20. k run nginx --image=nginx # creating an nginx deployment  
21. k scale deployments nginx --replicas=2
22. k port forward
23. k expose deployment nginx --port 80 --type NodePort
24. kubectl create rolebinding <rolebinding-name> --role=<role-name> --serviceaccount=<ns>:<sa> -n <ns>
```
	kubectl create rolebinding test --role=service-reader --serviceaccount=webns:default -n web
```
25. kubectl create clusterrole pv-reader --verb=get,list --resource=persistentvolumes
	kubectl create clusterrolebinding pv-test --clusterrole=pv-reader --serviceaccount=web:default

26. k config view # View the kubeconfig content
27. k run nginx --image=nginx --replicas=2

















