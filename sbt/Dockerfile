FROM alpine:3.4

MAINTAINER "Luis Medina <luis@escala.io>"

ENV PATH $PATH:/usr/lib/jvm/java-1.8-openjdk/jre/bin:/usr/lib/jvm/java-1.8-openjdk/bin
ENV JAVA_HOME /usr/lib/jvm/java-1.8-openjdk
ENV SCALA_VERSION 2.11.8
ENV SBT_VERSION 0.13.12
ENV SCALA_HOME /usr/share/scala
ENV SBT_HOME /usr/share/sbt

USER root

RUN \
    apk add --no-cache --virtual .build-dependencies wget ca-certificates && \
    apk add --no-cache bash && \

    # Install OpenJDK
    apk add --no-cache openjdk8 && \

    cd /tmp && \

    # Install Scala
    wget https://downloads.typesafe.com/scala/$SCALA_VERSION/scala-$SCALA_VERSION.tgz && \
    tar xzf scala-$SCALA_VERSION.tgz && \
    mkdir $SCALA_HOME && \
    rm /tmp/scala-$SCALA_VERSION/bin/*.bat && \
    mv /tmp/scala-$SCALA_VERSION/bin /tmp/scala-$SCALA_VERSION/lib $SCALA_HOME && \
    ln -s $SCALA_HOME/bin/* /usr/bin/ && \

    # Install SBT
    wget http://dl.bintray.com/sbt/native-packages/sbt/$SBT_VERSION/sbt-$SBT_VERSION.tgz && \
    tar xzf sbt-$SBT_VERSION.tgz && \
    mv /tmp/sbt $SBT_HOME && \
    ln -s $SBT_HOME/bin/* /usr/bin/ && \

    # Cleanup
    apk del .build-dependencies && \
    rm -rf /tmp/*

ENTRYPOINT ["/bin/bash"]