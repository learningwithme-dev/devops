FROM jenkins/jenkins:latest
USER root
RUN apt-get update
# install necessary packages to run docker
RUN apt-get install docker.io -y 
RUN apt-get install sudo -y
# add jenkins user to sudoers, no password
RUN echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers