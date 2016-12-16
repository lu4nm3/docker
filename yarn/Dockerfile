FROM alpine:3.4

MAINTAINER "Luis Medina <luis@escala.io>"

ENV YARN_HOME /usr/share/yarn
ENV PATH $PATH:$YARN_HOME/bin

USER root

RUN \
    # Install dependencies
    apk add --no-cache --virtual .build-dependencies ca-certificates tar wget && \
    apk add --no-cache bash nodejs && \

    # Download Yarn
    wget https://yarnpkg.com/latest.tar.gz -P /tmp && \

    # Create Yarn directory
    mkdir $YARN_HOME && \

    # Install Yarn
    tar zxf /tmp/latest.tar.gz -C $YARN_HOME --strip-components=1 && \

    # Cleanup
    apk del .build-dependencies && \
    rm -rf /tmp/*

ENTRYPOINT ["/bin/bash"]
