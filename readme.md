# MyChat

## Description 
A Group video calling application using the Agora Web SDK with a Django backend.

##  How to use this source code

#### 1 - Clone repo
```
git clone https://github.com/divanov11/mychat
```

#### 2 - Install requirements
```
cd mychat
pip install -r requirements.txt
```

#### 3 - Update Agora credentals
In order to use this project you will need to replace the agora credentials in `views.py` and `streams.js`.

Create an account at agora.io and create an `app`. Once you create your app, you will want to copy the `appid` & `appCertificate` to update `views.py` and `streams.js`. If you have questions about where to get your app I'd recommend referencing this link `https://youtu.be/HX6AM_1-jNM?t=88`

###### views.py
```
def getToken(request):
    appId = "YOUR APP ID"
    appCertificate = "YOUR APPS CERTIFICATE"
    ......
```

###### streams.js
```
....
const APP_ID = 'YOUR APP ID'
....
```


#### 4 - Start server
```
python manage.py runserver
```


## Using Docker and Kubernetes 
For this demo we will be running kubernetes on our local machine, instead of a cloud service. To get the docker and kubernetes running on our system we need to install three set of programs
- [Docker](https://docs.docker.com/desktop/) 
- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [Kubectl](https://kubernetes.io/docs/tasks/tools/)

### How start application with docker and finally deploy to kubernetes

#### 1- Build Docker image locally or pull from docker hub
To build docker image locally
```
docker build -t geoffrey13/vidchat:1.0 .  
```
OR
To pull from docker hub

```
docker pull geoffrey13/vidchat:1.0
```

#### 2- deploy To Kubernetes
For our own case it will be minikube
```
cd deploy
kubectl apply -f mychat.yaml  
```
#### 3- Start our application

```
minikube tunnel  
```
Open another terminal

```
minikube service mychat-service
```
