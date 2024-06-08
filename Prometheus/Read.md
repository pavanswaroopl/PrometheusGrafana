Prometheus Installation and Usage
Introduction
Prometheus is an open-source systems monitoring and alerting toolkit. It is designed for reliability and scalability.

Prerequisites
Kubernetes cluster
Helm installed
Installation
Step 1: Add Prometheus Helm Repository

helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
Step 2: Install Prometheus

helm install prometheus prometheus-community/prometheus
Step 3: Expose Prometheus Service

kubectl expose service prometheus-server --type=NodePort --target-port=9090 --name=prometheus-server-ext
Accessing Prometheus
Access Prometheus using the NodePort or port-forwarding:

kubectl port-forward service/prometheus-server-ext 9090:80

Access the UI on browser