FROM ubuntu:14.04
MAINTAINER Luis Medina <lu4nm3@gmail.com>

# Create necessary directories.
RUN mkdir -p /zookeeper/data && \
    mkdir -p /zookeeper/log && \
    mkdir -p /opt/zookeeper/3.4.6 && \
    mkdir -p /var/log/zookeeper

# Install Java.
RUN echo oracle-java7-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections && \
    apt-get update && \
    apt-get install -y software-properties-common && \
    add-apt-repository -y ppa:webupd8team/java && \
    apt-get update && \
    apt-get install -y oracle-java7-installer && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /var/cache/oracle-jdk7-installer

# Download ZooKeeper.
RUN apt-get install -y wget && \
    wget http://www.us.apache.org/dist/zookeeper/zookeeper-3.4.6/zookeeper-3.4.6.tar.gz && \
    tar -xvzf zookeeper-3.4.6.tar.gz && \
    cp -nr zookeeper-3.4.6/* /opt/zookeeper/3.4.6/

# Clean up unnecessary files.
RUN rm -rf *

# Expose ports.
EXPOSE 2181 2888 3888

# Start ZooKeeper.
ENTRYPOINT ["/bin/bash", "/opt/zookeeper/3.4.6/bin/zkServer.sh", "start-foreground"]
