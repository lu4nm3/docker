FROM ubuntu:14.04
MAINTAINER Luis Medina <lu4nm3@gmail.com>

# Create zookeeper group and user.
RUN adduser --disabled-password --shell /bin/bash zookeeper && \
	grep -q "%sudo ALL=(ALL) NOPASSWD:ALL" /etc/sudoers || echo "\n%sudo ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers && \
	adduser zookeeper sudo

# Create necessary directories.
RUN	mkdir -p /zookeeper/data && \
	mkdir -p /zookeeper/log && \
	mkdir -p /opt/zookeeper/3.4.6 && \
	mkdir -p /var/log/zookeeper

# Changes ownership to zookeeper user.
RUN	chown -R zookeeper:zookeeper /zookeeper && \
	chown -R zookeeper:zookeeper /opt/zookeeper && \
	chown -R zookeeper:zookeeper /var/log/zookeeper

# Install Java
RUN echo oracle-java7-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections && \
	apt-get update && \
	apt-get install -y software-properties-common && \
	add-apt-repository -y ppa:webupd8team/java && \
	apt-get update && \
	apt-get install -y oracle-java7-installer && \
	rm -rf /var/lib/apt/lists/* && \
  	rm -rf /var/cache/oracle-jdk7-installer

# Swith to ZooKeeper user.
USER zookeeper

# Set logging location.
ENV ZOO_LOG_DIR=/var/log/zookeeper \
	ZOO_LOG4J_PROP='INFO,ROLLINGFILE'

# Download ZooKeeper.
RUN	sudo apt-get install -y wget && \
	wget http://www.us.apache.org/dist/zookeeper/zookeeper-3.4.6/zookeeper-3.4.6.tar.gz -P /tmp && \
	tar -xvzf /tmp/zookeeper-3.4.6.tar.gz -C /home/zookeeper && \
	cp -nr /home/zookeeper/zookeeper-3.4.6/* /opt/zookeeper/3.4.6/

# Configure ZooKeeper.
#COPY conf/zoo.cfg /opt/zookeeper/3.4.6/conf/
#RUN sudo chown zookeeper:zookeeper /opt/zookeeper/3.4.6/conf/zoo.cfg

# Create ZooKeeper id file.
#RUN echo ${MY_ID} >> /zookeeper/data/myid

# Set Java heap size.
#COPY conf/java.env /opt/zookeeper/3.4.6/conf/
#RUN sudo chown zookeeper:zookeeper /opt/zookeeper/3.4.6/conf/java.env

# Start ZooKeeper
ENTRYPOINT ["/bin/bash", "/opt/zookeeper/3.4.6/bin/zkServer.sh", "start-foreground"]