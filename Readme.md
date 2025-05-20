# Ansible automating tasks for multiple instances

## 1- SSH CONFIGURATION (Manuel)
- Start the **ssh** serive
> **CMD : service ssh start** 

> **CMD : ssh-copy-id ansible@172.35.0.11**
- Let's create a py virtual env
> **CMD: sudo apt update**

> **CMD: sudo apt install python3-virtualenv**

> **CMD: virtualenv -p python3.10 venv**

> **CMD: source /venv/bin/activate**

> **CMD: pip install ansible**
## 1.1- AUTOMATED CONFIGURATION 
- Since in docker the **ssh** service is ran at the creation of the container we'll use the ansible playbook we made to copy the ssh key and secure it.
> **!! BEFORE make sure to add the servers near the ansible server as known_hosts check the commandes.txt**

> **CMD: ansible-playbook -i hosts/hosts.ini playbooks/test.yaml --ask-pass**
- In here I am asking the password for the first time so I can use the ssh key generated afterward
- Make sure to do this for all the types **individually** (server_web,databases)
- For the seconde network check yet again the **commandes.txt**
> **CMD: ansible all -i hosts/hosts.ini -m ping**
- With this commande we check if our ssh key is ready to be used 
- OK once done and checked we can go ahead and launch the zabbix playbook 
> **CMD: ansible-playbook -i hosts/hosts.ini playbooks/zabbix-playbook.yaml**