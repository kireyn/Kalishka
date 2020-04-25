# kalishka
## Creating DO droplet(Ansible Control Node) and setup default settings:
ssh-keygen
apt install python3-pip
pip3 install ansible
git clone https://github.com/kireyn/kalishka.git

mkdir /etc/ansible
sudo nano /etc/ansible/hosts

```
[servers]
new_server ansible_host=insertyourdropletip
#new_server2 ansible_host=xxx.xxx.xxx.xxx
#new_server3 ansible_host=xxx.xxx.xxx.xxx

[all:vars]
ansible_python_interpreter=/usr/bin/python3
```
## Creating Ansible Host
ansible-playbook -i hosts creatingdroplet.yml
## Control of creation:
ansible all -m ping --private-key=~/.ssh/id_rsa
## Setuping Ansible Host:
ansible-playbook -l new_server  setupingdroplet.yml --private-key=~/.ssh/id_rsa
## Running Ad-Hoc Commands on Ansible Host:
ansible new_server -a 'cd /opt/Osmedeus && ./osmedeus.py -t target'  --private-key=~/.ssh/id_rsa
