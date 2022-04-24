# WEB APP
This folder contains yaml files that can be used to create a webapp project containing a NodeJS app linked to a MongoDB database.

## Files in this folder
| File | Explanation |
| ------ | ------ |
| mongo-config.yaml | Contains the ConfigMap |
| mongo-secret.yaml | Contains the secrets file |
| mongo.yaml | Contains the Deployment and Service |
| webapp.yaml | Contains the webapp Deployment and Service |

## How To Run
Use the following commands to create the project
_NB: Run them in the order shown_

To create base64 username and password for the mongo-secret file. Replace the username and password with your own values

```sh
echo -n username | base64
echo -n password | base64
```
Mongo ConfigMap creation
```sh
kubectl apply -f mongo-config.yaml
```
Mongo Secret creation
```sh
kubectl apply -f mongo-secret.yaml
```
MongoDB database creation
```sh
kubectl apply -f mongo.yaml
```
Node App creation
```sh
kubectl apply -f webapp.yaml
```

To confirm that all went well use the following commands
```sh
kubectl get all
```
```sh
kubectl get configmap
```
```sh
kubectl get secret
```
```sh
kubectl describe secret/pod <podname/secretname>
```
```sh
kubectl logs <podname> -f(stream logs)
```

```sh
minikube ip
```
```sh
kubectl get node -o wide
```