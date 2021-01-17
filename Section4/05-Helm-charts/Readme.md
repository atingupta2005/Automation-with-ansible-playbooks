## Helm Installation
```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```

## Using Helm
 - helm repo add stable https://charts.helm.sh/stable
 - helm repo update              # Make sure we get the latest list of chartshelm ls
 - helm search hub
 - helm search hub wordpress
 - helm get -h
 - helm create currency-exchange  # Create a blank helm project

## Using Helm Charts to deploy Spring Boot Microservice to Kubernetes
```
wget -c https://github.com/atingupta2005/12-helm/blob/master/currency-exchange.zip?raw=true -O currency-exchange.zip
unzip currency-exchange.zip
tree currency-exchange
helm install ./currency-exchange/ --generate-name
kubectl get pods
kubectl get service
curl http://104.42.78.59:8000/
```

## Using Helm Charts to manage Releases to Kubernetes Cluster
```
helm list -aq
helm history currency-exchange-1610709528
helm uninstall currency-exchange-1610707809
```

## Using Helm Charts to manage Releases to Kubernetes Cluster
 - Do modification in helm chart to increase the replicas
```
helm install ./currency-exchange/ --generate-name
helm upgrade currency-exchange-1610709528 ./currency-exchange/.  --description "My Upgrade to latest
version"
helm history currency-exchange-1610709528
helm rollback currency-exchange-1610709528 1
```

## Cheat Sheet
 - [Helm Charts Cheatsheet](Helmchart-Cheatsheet.md)
