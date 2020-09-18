# Overview

# In this lab, we'd learn how to deploy a containerized application with Kubernetes Engine 
# in less than 30 minutes. Using CloudShell.

#step 1
echo "Set compute zone to us-central1-a..."
gcloud config set compute/zone us-central1-a
echo " "

#step 2
echo "Verify Configuration details..."
gcloud config list
echo " "

#step 3
echo "Create a Kubernetes cluster:- cluster1..."
gcloud container clusters create cluster1
echo " "

#step 4
echo "Let's see the nodes or VMs of the cluster..."
gcloud compute instances list
echo " "

#step 5
echo "Authenticate the cluster credentials..."
gcloud container clusters get-credentials cluster1
echo " "

#step 6
echo "Create a new deployment hello-server from the hello-app container image..."
kubectl create deployment hello-server --image=gcr.io/google-samples/hello-app:1.0
echo " "

#step 7
echo "Expose the application to external traffic via a load balancer..."
kubectl expose deployments hello-server --type=LoadBalancer --port 8080
echo " "

#step 8
echo "Let's see the exposed deployment and its external IP address..."
kubectl get service
echo " "

#step 9
echo "If the EXTERNAL_IP is pending, wait a few minutes and repeat:-"
echo "kubectl get service"
echo " "

#step 10
echo "When you see the external IP address, then run:-  curl -ks http://EXTERNAL_IP:8080..."
echo "replace EXTERNAL_IP above with the real value of the external ip address."
echo " "

#step 11
echo "That should print out the following:-" 
echo "Hello, world!"
echo "Version: 1.0.0"
echo "Hostname: hello-server-********"
echo " "

#step 12
echo "Delete cluster1, run the command:- gcloud container clusters delete cluster1"
