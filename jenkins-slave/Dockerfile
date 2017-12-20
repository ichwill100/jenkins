FROM ubuntu:xenial
MAINTAINER Saul Ramos Vaca <ichwill100@hotmail.com>

RUN apt-get update &&\
    apt-get install -y openssh-server curl git &&\
    apt-get clean -y && rm -rf /var/lib/apt/lists/* &&\
    sed -i 's|session    required     pam_loginuid.so|session    optional     pam_loginuid.so|g' /etc/pam.d/sshd &&\
    mkdir -p /var/run/sshd

RUN adduser --quiet jenkins &&\
    echo "jenkins:jenkins" | chpasswd

RUN curl https://releases.rancher.com/install-docker/17.03.sh | sh
RUN apt-get update &&\
    apt-get install -y openjdk-8-jdk &&\
        apt-get clean -y && rm -rf /var/lib/apt/lists/*

RUN usermod -aG docker jenkins

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
