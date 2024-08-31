# Kubectl commands

# *Installing Miniqube*
1. Brew Update
2. Brew install minikube

# *Start Miniqube*
1. miniqube start --vm-driver=docker

# *Check Status*
1. minqube status
2. kubectl get pods

# *kubectl commands*
1. kubectl get nodes
2. kubectl get pod
3. kubectl get services
4. kubectl create deployment nginx-depl --image=nginx
5. kubectl get deployment
6. kubectl get replicaset
7. kubectl edit deployment nginx-depl

# *debugging*
1. kubectl logs {pod-name}
2. kubectl exec -it {pod-name} -- bin/bash
3. kubctl describe pod {pod-name}

# *delete deployment*
1. kubectl delete deployment {deployment-name}
2. kubectl delete deployment nginx-depl

# *create or edit config file*
1. vim nginx-deployment.yaml
2. kubectl apply -f nginx-deployment.yaml
3. kubectl get pod
4. kubectl get deployment

# *delete with config files*
1. kubectl delete -f nginx-deployment.yaml

# *Metrics*
1. kubectl top
