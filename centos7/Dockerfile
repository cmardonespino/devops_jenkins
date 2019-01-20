FROM centos

RUN yum -y install openssh-server
RUN yum -y install java-1.8.0-openjdk-devel
RUN mkdir /var/jenkins_home
RUN chmod -R 777 /var/jenkins_home

RUN useradd remote_user && \
    echo "1234" | passwd remote_user --stdin && \
    mkdir /home/remote_user/.ssh && \
    chmod 700 /home/remote_user/.ssh

COPY remote-key.pub /home/remote_user/.ssh/authorized_keys

RUN chown remote_user:remote_user -R /home/remote_user/.ssh/ && \
    chmod 600 /home/remote_user/.ssh/authorized_keys

RUN /usr/sbin/sshd-keygen

CMD /usr/sbin/sshd -D 
