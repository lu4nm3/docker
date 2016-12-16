FROM alpine:3.4

MAINTAINER "Luis Medina <luis@escala.io>"

ENV YARN_HOME /usr/share/yarn

USER root

RUN \
    # Install dependencies
    apk add --no-cache --virtual .build-dependencies ca-certificates tar wget && \
    apk add --no-cache bash nodejs && \

    # Download Yarn
    wget https://yarnpkg.com/latest.tar.gz -P /tmp && \

    # Install Yarn
    tar zxf /tmp/latest.tar.gz dist -C $YARN_HOME --strip-components=1 && \

    # Cleanup
    apk del .build-dependencies && \
    rm -rf /tmp/*

ENTRYPOINT ["/bin/bash"]
