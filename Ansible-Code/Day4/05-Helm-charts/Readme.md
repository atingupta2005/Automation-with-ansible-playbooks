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
 - sudo helm install mysql1 stable/mysql
 - sudo helm status mysql1
 - sudo helm uninstall mysql1
 - helm get -h
 - helm create currency-exchange  # Create a blank helm project

## Using Helm Charts to deploy Spring Boot Microservice to Kubernetes
```
wget -c https://github.com/atingupta2005/12-helm/blob/master/currency-exchange.zip?raw=true -O currency-exchange.zip
unzip currency-exchange.zip
tree currency-exchange
sudo helm install ./currency-exchange/ --generate-name
```

## Using Helm Charts to manage Releases to Kubernetes Cluster
```
wget -c https://github.com/atingupta2005/12-helm/blob/master/currency-exchange.zip?raw=true -O currency-exchange.zip
unzip currency-exchange.zip
cat currency-exchange/values.yaml
sudo helm install ./currency-exchange/ --generate-name
curl http://104.42.78.59:8000/
sudo helm list -aq
sudo helm history currency-exchange-1610709528
sudo helm uninstall currency-exchange-1610707809
sudo helm delete  currency-exchange-1610708541
```

## Using Helm Charts to manage Releases to Kubernetes Cluster
 - Do modification in helm chart to increase the replicas
```
sudo helm upgrade currency-exchange-1610709528 ./currency-exchange/.  --description "My Upgrade to latest version"
sudo helm history currency-exchange-1610709528
sudo helm rollback currency-exchange-1610709528 1 --description "Rollback as there was an error"

```
