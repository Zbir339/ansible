FROM ubuntu:22.04

## We first install dependecies in need
RUN apt-get update && \
    apt-get install -y \
        openssh-server \
        python3 \
        python3-pip \
        sudo && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

## We create a user and give it sudo properties with no pass
RUN useradd -m ansible && \
    echo "ansible ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

USER ansible
WORKDIR /home/ansible
## we generate the ssh key (we'll publish it after words)
RUN ssh-keygen -t rsa -f ~/.ssh/id_rsa

CMD ["sleep", "infinity"]