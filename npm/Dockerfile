FROM alpine:3.4

MAINTAINER "Luis Medina <luis@escala.io>"

#ENV PATH $PATH:/usr/lib/jvm/java-1.8-openjdk/jre/bin:/usr/lib/jvm/java-1.8-openjdk/bin
#ENV JAVA_HOME /usr/lib/jvm/java-1.8-openjdk
#ENV SCALA_VERSION 2.11.8
#ENV SBT_VERSION 0.13.12
#ENV SCALA_HOME /usr/share/scala
#ENV SBT_HOME /usr/share/sbt
ENV NODE_VERSION 6.2.0-r0

USER root

RUN \
    apk add --no-cache bash && \

    # Install NodeJS
    apk add --no-cache nodejs=$NODE_VERSION

ENTRYPOINT ["/bin/bash"]