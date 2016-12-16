FROM alpine:3.4

MAINTAINER "Luis Medina <luis@escala.io>"

ENV PATH $PATH:$HOME/.yarn/bin

USER root

RUN \
    # Install dependencies
    apk add --no-cache bash curl gnupg nodejs tar && \

    # Create bash profile to include yarn in PATH
    touch ~/.bash_profile && \

    # Install Yarn
    curl -o- -L https://yarnpkg.com/install.sh | bash && \

    apk del curl gnupg tar

ENTRYPOINT ["/bin/bash"]