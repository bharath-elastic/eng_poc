FROM openjdk:8u171-jdk-stretch
EXPOSE 9200
RUN apt update && apt install -y curl && \
apt install -y vim && \
groupadd elastic && echo 'root:elastic' | chpasswd && \
echo "export VISIBLE=now" >> /etc/profile && \
useradd -m -s /bin/bash -g elastic elastic && \
cd /home/elastic && su - elastic && \
curl -s -O https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-6.2.4.tar.gz && \
tar -xf elasticsearch-6.2.4.tar.gz && chown -R elastic elasticsearch-6.2.4
WORKDIR /home/elastic
USER elastic
COPY .tmux.conf .
CMD ["/bin/bash"]
