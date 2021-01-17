# Kubernetes Workstation Setup Guide

 - Install KubeCTL (AWS)
    - Refer: https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html
```
curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.18.9/2020-11-02/bin/linux/amd64/kubectl
chmod +x ./kubectl
mkdir -p $HOME/bin && cp ./kubectl $HOME/bin/kubectl && export PATH=$PATH:$HOME/bin
kubectl version --short --client
```

 - Install AWS-cli 2.0
```
sudo yum install unzip
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

 - Setup autocomplete in bash into the current shell, bash-completion package should be installed first (Optional)
```
source <(kubectl completion bash)
echo "source <(kubectl completion bash)" >> ~/.bashrc # add autocomplete permanently to your bash shell.
```

 - AWS Configure
    - Provide Access_Key, Secret_key and region
```
aws configure
```

 - Deploy Docker image in Kubernetes
```
kubectl create deployment hello-world-rest-api --image=atingupta2005/hello-world-rest-api:latest
kubectl expose deployment hello-world-rest-api --type=LoadBalancer --port=8080
kubectl get service
curl <ExternalIP:8080>
kubectl get pods
```


 - Pods
   - Pod is the smallest deployable unit. Can not have container without Pod. Container lives inside Pod
```
kubectl get pods
kubectl get pods -o wide
```

   - To get details about the artifact
```
kubectl explain pods
```

   - Get list of various artifacts
```
kubectl get all
kubectl get events
kubectl get pods
kubectl get replicaset
kubectl get deployment
kubectl get service
```
