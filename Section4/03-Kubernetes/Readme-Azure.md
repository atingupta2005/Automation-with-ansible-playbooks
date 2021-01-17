# Kubernetes workstation Setup Guide for AWS

 - Install KubeCTL
```
sudo apt-get update && sudo apt-get install -y apt-transport-https gnupg2
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubectl
```

 - Install Azure CLI
```
curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
```

 - Setup autocomplete in bash into the current shell, bash-completion package should be installed first (Optional)
```
source <(kubectl completion bash)
echo "source <(kubectl completion bash)" >> ~/.bashrc # add autocomplete permanently to your bash shell.
```

 - Connect to Azure Kubernetes Cluster
   - Run below commands to connect to Azure Kubernetes Cluster
   - Use these commands if Azure Cluster and your namespace is already created
```
az login
az account set --subscription "<Subscription ID>"
sudo az aks get-credentials --resource-group <resource-group-name> --name <cluster-name>
sudo kubectl config use-context <cluster-name>
kubectl config view
sudo kubectl create namespace "ns-atingupta2005"    # Note: Specify your namespace here.
sudo kubectl get namespaces
sudo kubectl config set-context --current --namespace="ns-atingupta2005"    # Note: Specify your namespace here.
sudo kubectl get nodes
```

 - Deploy Docker image in Kubernetes
```
sudo kubectl create deployment hello-world-rest-api --image=atingupta2005/hello-world-rest-api:latest
sudo kubectl expose deployment hello-world-rest-api --type=LoadBalancer --port=8080
sudo kubectl get service
curl <ExternalIP:8080>
sudo kubectl get pods
```


 - Pods
   - Pod is the smallest deployable unit. Can not have container without Pod. Container lives inside Pod
```
sudo kubectl get pods
sudo kubectl get pods -o wide
```

   - To get details about the artifact
```
sudo kubectl explain pods
```

   - Get list of various artifacts
```
sudo kubectl get all
sudo kubectl get events
sudo kubectl get pods
sudo kubectl get replicaset
sudo kubectl get deployment
sudo kubectl get service
```
