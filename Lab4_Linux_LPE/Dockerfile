FROM ubuntu:latest

COPY . /var/www/html

WORKDIR /var/www/html

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update -y && \
    apt install sudo -y && \
    apt install apache2 -y && \
    apt install python3 -y && \
    chmod u+s $(which python3) && \
    apt install openssl -y && \
    apt-get install php7.4 -y && \
    apt install ncat -y && \
    apt install openssh-client -y && \
    useradd -m tester && \
    chmod o+w /etc/passwd && \
    mkdir uploads && chmod 0777 uploads/ && \
    echo "www-data ALL=(ALL) NOPASSWD: /usr/bin/awk" >>/etc/sudoers && \
    ssh-keygen -q -t rsa -N '' -f ~/.ssh/id_rsa && \
    mv ~/.ssh/id_rsa.pub ~/.ssh/authorized_keys && \
    mkdir /home/tester/.ssh && mv ~/.ssh/id_rsa /home/tester/.ssh && \
    apt install ssh -y && service ssh start && \
    mv sshd_config /etc/ssh/sshd_config

ENTRYPOINT  [ "./entrypoint.sh"]