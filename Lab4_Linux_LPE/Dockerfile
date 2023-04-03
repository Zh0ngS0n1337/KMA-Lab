FROM ubuntu:latest

COPY . /var/www/html

WORKDIR /var/www/html

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update -y && \
    apt install apache2 -y && \
    apt install python3 -y && \
    chmod u+s $(which python3) && \
    apt install openssl -y && \
    apt-get install php7.4 -y && \
    useradd kmastudent -p $(openssl passwd -1 -salt kmastudent kmasec)

ENTRYPOINT  [ "apache2ctl", "-D", "FOREGROUND"]