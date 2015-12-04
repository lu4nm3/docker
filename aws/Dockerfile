FROM gliderlabs/alpine
MAINTAINER Luis Medina <luis@escala.io>

RUN \
    # Install necessary packages.
    apk --update add python py-pip jq curl wget bash && \
    
    # Install AWS client.
    pip install --upgrade awscli && \
    
    # Create directory for AWS credentials.
    mkdir /root/.aws

# Expose root volume for adding credentials and etcd-aws-cluster script.
VOLUME ["/root"]

# Run the script.
ENTRYPOINT ["/root/etcd-aws-cluster"]
