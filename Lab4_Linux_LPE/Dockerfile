FROM ubuntu:latest

RUN apt-get update -y && \
    apt install apache2 -y && \
    chmod u+s $(which cat)

ENTRYPOINT  [ "apache2ctl", "-D", "FOREGROUND"]