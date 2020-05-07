POD create and display
1. create pod by following command
    -kubectl create -f nginx-pod.yml
2. kubectl get po -o wide
3. kubectl describe po
4. kubectl get po nginx-pod -o yaml
5. Getting a shell to running container
    -kubectl exec -it Nginx-pod  - -  /bin/sh
6. Delete a Pod
    -kubectl delete -f nginx-pod.yml
