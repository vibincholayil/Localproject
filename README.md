# Localproject
Localproject


### Bring up the network interface
```
sudo ip link set ens33 up → activates the interface   
sudo dhclient ens33 → requests an IPv4 via DHCP from your network/router
```
Check if you got IPv4
```
ip a show ens33
hostname -I
```
Run Minikube
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
deployment.yml
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 2  
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
```

