FROM openjdk:8u171-jdk-stretch
EXPOSE 5601
EXPOSE 22
RUN apt update && apt install -y curl && \
apt install -y vim && \
groupadd elastic && echo 'root:elastic' | chpasswd && \
echo "export VISIBLE=now" >> /etc/profile && \
useradd -m -s /bin/bash -g elastic elastic && \
cd /home/elastic && su - elastic && \
curl -s -O https://artifacts.elastic.co/downloads/kibana/kibana-6.2.4-linux-x86_64.tar.gz && \
tar -xf kibana-6.2.4-linux-x86_64.tar.gz && chown -R elastic kibana-6.2.4-linux-x86_64
WORKDIR /home/elastic
USER elastic
COPY .tmux.conf .
CMD ["/bin/bash"]
