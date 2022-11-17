# graduation project 
Note: all pictures located in folder my-pictures
Building and deploying an application using Jenkins CI/CD
first we must deploye a yaml file to create a pod for jenkins so we can to it
by using steps installation in this docmuntaion
https://www.jenkins.io/doc/book/installing/kubernetes/

# content of Jenkins file
## jenkins file has 2 stages :
### Build stage :
#### build the app then push it to Docker hub
### Deploy stage :
#### authorize  my service account to  jenkins deployment 
#### create deployment from our Docoratize application 
  
 
Dockerhub jenkins image repository: https://hub.docker.com/repository/docker/hassnzax/build

Build kubertates cluster using terraform and deploy simple web app 🌐
using GCP

#terraform resources :

#vpc

#2 private subnets managment for (VM) && restirected for (cluster)

#private VM

#private cluster

#service account

#firewall to allow IAP to VM

#NAT in managment subnet

#Architecture description

#cluster dont have accses to egress or ingress

#only VM can access our cluster

#VM access only form IAP

#VM cat access internet throw NAT

#store app images into GCR that lets cluster to access them

#Implementation instructions

1- Run terraform code to build infrastructure

2- Configure VM to interact with cluster

3- Build application images and push them to GRC

4- apply deployment using kubectl

5- create ingress to access our app

Run terraform command into terraform Dir

First change project_ID and srvice account Then run :


$ terraform init 

$ terraform plan 

$ terraform apply -auto-approve

configure VM :

1- Connect to VM using console OR from your machine using this command :

$ gcloud container clusters get-credentials k8-cluster --region asia-east1 --project terraform-gcp-368522

2- Copy deployment file into vm

3- Run the following command to setup enviroment :

$ sudo apt update

$ sudo apt install kubectl

$ curl -fsSL https://test.docker.com -o test-docker.sh

$ sudo sh test-docker.sh

$ sudo usermod -aG docker ${USER}

$ gcloud auth configure-docker

#restart VM to cofigure changes 

$ gcloud auth login

Build Application images

If you want deploy your own application it's up to you OR using the Dockerfile that in application dir to buid your custom image

if you want use this application image i built the image and push it into dockerHub

use this command to pull application image  :

$ docker pull hassnzax/build:latest
$ docker pull jenkins


Apply deployment

First if you will use same deployment file dont forget to change image name in yaml file to your image name

connect to your cluster using this command:

$ gcloud container clusters get-credentials k8-cluster --region asia-east1 --project terraform-gcp-368522

deploy the application using jenkins file (pipeline)


#deploy application deployment

$ kubectl apply -f myapp-deployment.yaml

create service loadbalance  to access application externaly



using this command to show  external IP to connect jenkins dashbord
$ kubectl get service -n devops-tools-2
copy IP into your browser
congratulations your application now UP and Running

