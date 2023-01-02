# From amazonlinux, install nodejs 18.x and build the AWS SDK lambda layer.
# The AWS SDK layer is used by the lambda function to access AWS services.
# The layer is built in /opt/layer.zip.

# Must use amazonlinux:2022 because nodejs 18.x reqiures glibc 2.28 or later.
FROM amazonlinux:2022

# Install sudo. This is required for the nodejs install script.
RUN yum update && yum install -y sudo
RUN sudo yum install -y gcc-c++ make patch

# Install nodejs.
RUN curl -sL https://rpm.nodesource.com/setup_18.x > /tmp/node.js
# COPY local opt/node_setup_amazonlinux2022.patch to /opt
COPY opt/node_setup_amazonlinux2022.patch /opt
RUN cd /tmp && patch -p0 < /opt/node_setup_amazonlinux2022.patch
RUN sudo bash /tmp/node.js
RUN yum install -y nodejs 
RUN echo "Node: " && node -v
RUN echo "NPM: " && npm -v

# Build AWS SDK lambda layer
RUN mkdir -p /tmp/layer \
 && cd /tmp/layer \
 && npm install aws-sdk \
 && cd node_modules \
 && zip -r /tmp/layer.zip * 

VOLUME [ "/opt" ]

