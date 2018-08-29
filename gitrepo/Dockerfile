FROM ubuntu:14.04

RUN apt-get -y update
RUN apt-get -y install openssh-server
RUN apt-get -y install git

# Setting openssh
RUN mkdir /var/run/sshd
#RUN sed -i "s/#PasswordAuthentication yes/" /etc/ssh/sshd_config
#RUN sed -i "s/PasswordAuthentication no/" /etc/ssh/sshd_config
RUN sed -ie 's/#\?PasswordAuthentication yes/PasswordAuthentication no/' /etc/ssh/sshd_config


# Adding git user
RUN adduser --system git
RUN mkdir -p /home/git/.ssh

# Clearing and setting authorized ssh keys
#RUN echo '' > /home/git/.ssh/authorized_keys
RUN echo 'ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC0pK+hVQPtVFP0K56yoddg5HBCBTtFhCQM20vmGonDIfImO19s3YatyJuJx4p8xPclJ/ONAOpL+QKvfvu3eJh96/zpfsq61ynXMhJqDy7vMd/CBEOGb4wa7XgNWGH6ZvBCPFFEj/0+eNax5kafdnX0j7NR2KolmqWbbrMjpWjEZgrut6QzHeYNLpHcSIXSpl5HUUHRoD7sY6AgD3z5LgVO3Am9gREm5Eusmei9u7ua9ROlyHEZsr+bXdRgrdu8aSH6n5lwm9NBs3W+GRz/3Sh50cXpWEqqGZ8Daa8/QRLOXnUqKeb0bAX+Pcf5Duwd/cR6BKugO5kLvsfwH3oZv0r/ centos@centos-1' >> /home/git/.ssh/authorized_keys
#RUN cat /home/centos/.ssh/id_rsa.pub >> /home/git/.ssh/authorized_keys
#RUN echo 'ssh-rsa key ...' >> /home/git/.ssh/authorized_keys
#RUN echo 'Second SSH public key' >> /home/git/.ssh/authorized_keys
# ...

# Updating shell to bash
RUN sed -i s#/home/git:/bin/false#/home/git:/bin/bash# /etc/passwd

# Set Name Servers
COPY /files/resolv.conf /etc/resolv.conf

EXPOSE 22
#CMD ["/usr/sbin/sshd", "-D"]
CMD service ssh restart && bash

