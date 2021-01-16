# Setup Python3 with Ansible
```
sudo apt install python3-venv
python3 -m venv my-ansible-python3
source my-ansible-python3/bin/activate
pip install ansible
ansible --version
vim hosts
  [localhost]
  localhost ansible_python_interpreter=/home/atingupta2005/my-ansible-python3/bin/python

```
