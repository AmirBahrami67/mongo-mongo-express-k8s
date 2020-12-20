# Mongo on Kubernetes 
This is a Kubernetes configuration project to deploy and run Mongo and Mongo express instances.

### Prerequisites 
install kubectl command line and configure it with your cluster

### Getting Started

1- config mongo instance secrets file deploy/mongo/secrets.yaml and define your username and password. 
The values must be base64 encoded.
* Current configured username: mongo
* Current configured password: mongo

2- Apply mongo secrets to the k8s cluster
```
kubectl apply -f deploy/mongo/secrets.yaml
```

3- Apply mongo deployment file to the k8s cluster
```
kubectl apply -f ./deploy/mongo/deployment.yaml
```
