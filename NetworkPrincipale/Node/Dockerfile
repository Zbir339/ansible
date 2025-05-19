FROM ubuntu:22.04

# Installer les paquets nécessaires
RUN apt-get update && \
    apt-get install -y \
        openssh-server \
        python3 \
        python3-pip \
        sudo && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Créer l'utilisateur ansible avec droits sudo sans mot de passe
RUN useradd -m ansible && \
    echo "ansible:test" | chpasswd && \
    echo "ansible ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# Configurer SSH pour root (à faire avant de changer d'utilisateur)
RUN mkdir -p /var/run/sshd && \
    mkdir -p /home/ansible/.ssh && \
    chmod 700 /home/ansible/.ssh && \
    chown ansible:ansible /home/ansible/.ssh

# Exposer le port SSH
EXPOSE 22

USER ansible
WORKDIR /home/ansible

# Démarrer sshd en root
CMD ["sudo","/usr/sbin/sshd", "-D"]