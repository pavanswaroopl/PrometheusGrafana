Grafana Installation and Usage
Introduction
Grafana is an open-source platform for monitoring and observability. It allows you to query, visualize, alert on, and explore your metrics no matter where they are stored.

Prerequisites
Kubernetes cluster
Helm installed
Prometheus as a data source (optional but recommended)
Installation
Step 1: Add Grafana Helm Repository

helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
Step 2: Install Grafana

helm install grafana grafana/grafana
Step 3: Expose Grafana Service

kubectl expose service grafana --type=NodePort --target-port=3000 --name=grafana-ext
Step 4: Retrieve Admin Password

kubectl get secret --namespace default grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
Accessing Grafana
Access Grafana using the NodePort or port-forwarding:
kubectl port-forward service/grafana-ext 3000:80

Access usign a browser
Adding a Data Source
Log in to Grafana.
Navigate to Configuration > Data Sources.
Add Prometheus or another data source.
Creating a Dashboard
Click the "+" icon and select "Dashboard".
Add panels and configure your visualizations.
