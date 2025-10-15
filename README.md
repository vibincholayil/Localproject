# Localproject
Localproject


```
minikube version
minikube start --driver=docker
minikube status
minikube profile list
kubectl get nodes
kubectl get pods
```
Create po
```
nano nginx-pod.yaml
```
yaml file
```
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
  labels:
    app: nginx
spec:
  containers:
  - name: nginx
    image: nginx:latest
    ports:
    - containerPort: 80
```
Apply nginx-pod.yml
```
kubectl apply -f nginx-pod.yml  
kubectl logs nginx-pod

Expose pod to outside world  
```
kubectl expose pod nginx-pod --type=NodePort --port=80  
kubectl get svc
```
