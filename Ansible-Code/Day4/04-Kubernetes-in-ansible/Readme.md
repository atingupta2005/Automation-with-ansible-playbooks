## Automate your container orchestration with Ansible modules for Kubernetes
 - Install Python modules
 ```
sudo pip install kubernetes
sudo pip install openshift
 ```

 - Install Ansible if required:
```
sudo apt update && sudo apt install software-properties-common &&
sudo apt-add-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
ansible --version
cp /etc/ansible/ansible.cfg .
cp /etc/ansible/hosts .
vim ansible.cfg   # Update Hosts file path
vim hosts         # Add localhost
```

 - Install kubernetes plugins
 ```
ansible-galaxy collection install community.kubernetes
 ```

 - Get Kubernetes Info
 ```
kubectl cluster-info
 ```

 - Update playbook and run it
    - open playbook - 01.helm-create-namespace.yml and update the name of Namespace
```
ansible-playbook 1.Create-namespace.yml
kubectl get namespaces
```

 - Install Podman in CentOS
```
sudo curl -L -o /etc/yum.repos.d/devel:kubic:libcontainers:stable.repo https://download.opensuse.org/repositories/devel:/kubic:/libcontainers:/stable/CentOS_7/devel:kubic:libcontainers:stable.repo
sudo yum -y install yum-plugin-copr
sudo yum -y copr enable lsm5/container-selinux
sudo yum -y install podman --allowerasing
podman info
```

 - Install Podman in Ubuntu
 ```
sudo add-apt-repository -y ppa:projectatomic/ppa
sudo apt-get install podman -y
podman info
```

 - Pull a container image with Podman
 ```
echo -e "[registries.search]\nregistries = ['docker.io']" | sudo tee /etc/containers/registries.conf
ansible-galaxy collection install containers.podman
ansible-playbook 2.Pull-container-image-with-Podman.yml
sudo podman ps -a
sudo podman images
```

 - Deploy with Ansible
```
kubectl config set-context --current --namespace=atintesting
ansible-playbook 3.Deploy-service-with-Ansible.yml
ansible-playbook 4.Remove-service-with-Ansible.yml
ansible-playbook 5.Create-k8s-objects-filesystem.yml

```
