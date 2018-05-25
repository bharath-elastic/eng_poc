FROM openjdk:8u171-jdk-stretch
EXPOSE 5601
EXPOSE 22
RUN apt update && apt install -y curl && \
apt install -y vim && apt-get install -y openssh-server && \
mkdir /var/run/sshd && groupadd elastic && echo 'root:elastic' | chpasswd && \
sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd && \
echo "export VISIBLE=now" >> /etc/profile && \
/usr/sbin/sshd -D && \
useradd -m -s /bin/bash -g elastic elastic && \
mkdir /home/elastic/.ssh && ssh-keygen -t rsa -N "" -f /home/elastic/.ssh/ssh_host_key && \ 
cd /home/elastic && su - elastic && \
curl -s -O https://artifacts.elastic.co/downloads/kibana/kibana-6.2.4-linux-x86_64.tar.gz && \
tar -xf kibana-6.2.4-linux-x86_64.tar.gz && chown -R elastic kibana-6.2.4-linux-x86_64
WORKDIR /home/elastic
USER elastic
COPY .tmux.conf .
COPY sshd_config /etc/ssh/
CMD ["/usr/sbin/sshd", "-D"]
