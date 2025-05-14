# Ansible automating tasks for multiple instances

## 1- SSH CONFIGURATION
- Start the **ssh** serive
> **CMD : service ssh start** 
> **CMD : ssh-copy-id ansible@172.35.0.11**
- Let's create a py virtual env
> **CMD: sudo apt update**
> **CMD: sudo apt install python3-virtualenv**
> **CMD: virtualenv -p python3.10 venv**
> **CMD: source /venv/bin/activate**
> **CMD: pip install ansible**
## 2- Ansible Configuration