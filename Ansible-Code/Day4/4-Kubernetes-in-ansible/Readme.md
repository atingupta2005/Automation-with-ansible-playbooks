## Automate your container orchestration with Ansible modules for Kubernetes
 - Install Python modules
 ```
pip install kubernetes
pip install openshift
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
sudo kubectl cluster-info
 ```

 - Update playbook and run it
    - open playbook - 1.helm-create-namespace.yml and update the name of Namespace
```
sudo ansible-playbook 1.helm-create-namespace.yml
sudo kubectl get namespaces
```

 - Pull a container image with Podman
 ```
sudo add-apt-repository -y ppa:projectatomic/ppa
sudo apt-get install podman -y
podman info
echo -e "[registries.search]\nregistries = ['docker.io']" | sudo tee /etc/containers/registries.conf
ansible-galaxy collection install containers.podman
ansible-playbook 2.Pull-container-image-with-Podman.yml
sudo podman ps -a
sudo podman images
```

 - Deploy with Ansible
```
ansible-playbook 3.deploy-service-with-ansible.yml
ansible-playbook 4.Remove-service-with-Ansible.yml
ansible-playbook 5.Create-k8s-objects-filesystem.yml

```
