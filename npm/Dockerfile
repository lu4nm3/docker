FROM alpine:3.4

MAINTAINER "Luis Medina <luis@escala.io>"

ENV NODE_VERSION 6.2.0-r0

USER root

RUN \
    apk add --no-cache bash git && \

    # Install NodeJS
    apk add --no-cache nodejs=$NODE_VERSION

ENTRYPOINT ["/bin/bash"]