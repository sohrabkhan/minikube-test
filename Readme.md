# MiniKube Test
## Solution
### Python Flask App
I developed a hello world app using python flask. It is a simple flask application which uses a jinja template (inside templates folder) and passes the company name the template. The jinja template displays hello world and on the next line outputs the passed value for company variable.

The requirements.txt lists the dependencies of the project. I chose uwsgi as the application server.

The Dockerfile uses the base docker image tiangolo/uwsgi-nginx-flask:python3.7 which is quite well maintained that is why I used this image. In the dockerfile I update pip and install the dependencies from requirements.txt. 

I've pushed the docker image 

### Kubernetes - Minikube
#### Namespace:
I created a namespace called minikube is a good way to divide cluster resources.

#### Deployment:
I created a deployment which gives us better scalability, reliability & rolling update capabilities. I've used 3 replicas which means the app will be run on 3 pods. Because the app is stateless hence there is no need for volumese or any session storage.

#### Service:
I created a loadbalancer service which will load balance any requests among the 3 replicas. Autoscaling can be achieved using horizontal pod autoscaler in case the application needs auto scaling but this hasn't been addressed as it's not a requirement.

### How to run the app:
Extract the zip and change directory to the kubernetes directory. 
1. Run the following kubectl command:
```
kubectl  create-f  .
```
or run the below 3 commands:
```
kubectl create -f namespace.yaml
kubectl create -f deployment.yaml
kubectl create -f service.yaml
```

This will create the service, deployment and namespace. 

2. To get the URL for the app run the following:
```
minikube service minikube-service --url
```

## Author
Name: Sohrab Khan
CV: https://www.sohrabkhan.com/CV.pdf