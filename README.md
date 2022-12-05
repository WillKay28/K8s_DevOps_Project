# K8s_DevOps_Project

In this project, we I use Kubernetes to implement a project where Mongo Express UI is connected with MongoDB and the Mongo Express makes requests to the DataBase. 

The project includes the following files: 

1. Deployments for pods & services of mongodb and mongo express with environment variables and container target ports specified
    - Services: They generate a static IP address that can be attached to a Pod to ensure consistency of pod IPs.
 
2. A ConfigMap file - Connected to the Pod so that the Pod gets access to the data that the configMap file contains through a Database URL

3. A secret file - They are meant for data that you don't want anything or anyone to know about except the application. Used to store secrete data and credentials that helps to authenticate environment variables such as USERNAME & PASSWORD, not in plain text but in base64 encoded format.


# Setting Up the Linux Environment for K8s Cluster

1. First, because I am setting up the kubernetes environment using minikube, I need a virtualization. I install hyperkit (virtualbox can be used too)
    - brew update
    - brew install hyperkit

2. Install minikube to create kubernetes environment using the code:
    - brew install minikube

3. To start minikube, run the code below (NB: Use "--vm-driver=virtualbox" for Oracle virtualbox):
    - minikube start --vm-driver=hyperkit

4. Because the deployments of mongodb and mongo express reference secret and configmap, run the commands to deploy them in this order:
    - kubectl apply -f mongo-secret.yaml
    - kubectl apply -f mongo-configmap.yaml
    - kubectl apply -f mongo.yaml
    - kubectl apply -f mongo-express.yaml

5. To give a URL to external service in minikube:
    - minikube service mongo-express-service

To RUN Mongo Express App on a browser:
    - Take the assigned external IP from step 5 and load it through port 30002
    - Paste IP_address:30002 in your browser to load app
