# Mongo on Kubernetes 
This is a Kubernetes configuration project to deploy and run MongoDB and Mongo express instances.

### Prerequisites 
install kubectl command line and configure it with your cluster

### Getting Started

`#### 1- Config mongo root username/password
Modify file deploy/mongo/secrets.yaml and define your username and password. 
The values must be base64 encoded. You can use below command to base64 encode your values. 
```
$ echo -n 'YOUR_VALUE' | base64 
```

* Current configured username: mongo
* Current configured password: mongo

#### 2- Create mongo secret on the cluster
Mongo secret config file configured with type Opaque and contains mongo-root-username and mongo-root-password
```
kubectl apply -f deploy/mongo/secrets.yaml
```

#### 3- Deploy mongo db on the cluster by applying the deployment file
```
kubectl apply -f ./deploy/mongo/deployment.yaml
```

#### 4- Define mongo db k8s service by applying the service file
```
kubectl apply -f ./deploy/mongo/service.yaml
```

#### 5- Create config map to be used by mongo express
This config map contains the mongo server url which is the link to the mongo db service
```
kubectl apply -f deploy/mongo-express/mongo-configmap.yaml
```

#### 6- Deploy mongo express on the cluster by applying the deployment file
```
kubectl apply -f deploy/mongo-express/deployment.yaml  
```

#### 7- Define mongo express k8s service by applying the service file
```
kubectl apply -f deploy/mongo-express/service.yaml 
```

At this point both services should be running and Kubernetes should assign a public IP with defined port to access to mongo express in browser. 

###### if you are using minikube you have to run below command to assign a public IP address to mongo-express service
```
minikube service mongo-express-service
```

