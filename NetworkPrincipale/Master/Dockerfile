FROM ubuntu:22.04

RUN apt-get update && \
    apt-get install -y \
        openssh-server \
        python3 \
        sshpass\
        python3-pip \
        sudo && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN useradd -m ansible && \
    echo "ansible ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

RUN apt-get update && \
    apt-get install -y python3-virtualenv

RUN mkdir -p /home/ansible/.ssh && \
    chown ansible:ansible /home/ansible/.ssh && \
    chmod 700 /home/ansible/.ssh

RUN ssh-keygen -t rsa -f /home/ansible/.ssh/id_rsa -N "" && \
    chown ansible:ansible /home/ansible/.ssh/id_rsa*

RUN mkdir -p /run/sshd

WORKDIR /home/ansible
RUN virtualenv -p python3.10 venv
RUN venv/bin/pip install ansible

USER ansible



EXPOSE 22

CMD ["sudo", "/usr/sbin/sshd", "-D"]