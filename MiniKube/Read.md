Minikube Installation and Usage
Introduction
Minikube is a tool that makes it easy to run Kubernetes locally. It runs a single-node Kubernetes cluster on your personal computer.

Prerequisites
Virtualization environment (Docker, Hyperkit, VirtualBox, etc.)
kubectl installed
Installation
Step 1: Install Minikube
macOS/Linux:
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64
sudo install minikube-darwin-amd64 /usr/local/bin/minikube

Windows:
Download and run the installer from the official Minikube release page.
Step 2: Start Minikube

minikube start --driver=docker
Step 3: Verify Minikube Installation

kubectl get nodes
Usage
Deploying an Application
Create a deployment:

kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.4
Expose the deployment:

kubectl expose deployment hello-minikube --type=NodePort --port=8080
Access the application:

minikube service hello-minikube