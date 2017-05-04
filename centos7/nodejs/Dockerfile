FROM centos:7

MAINTAINER "Amakasu Ryoma"

RUN yum update -y && yum clean all && yum install -y \
    gcc gcc-c++ make git curl-devel openssl-devel patch \
    bzip2-devel zlib-devel readline-devel libffi-devel libxslt-devel

# Node.js
ENV NVM_DIR /usr/local/nvm
ENV NVM_PROFILE /etc/bashrc
ENV NODE_VERSION 6.10.3
## NVM を install
RUN git clone https://github.com/creationix/nvm.git $NVM_DIR && \
    cd $NVM_DIR && \
    git checkout -b `git describe --abbrev=0 --tags --match "v[0-9]*" origin`
## Node.js を install
RUN source $NVM_DIR/nvm.sh && \
    nvm install v$NODE_VERSION && \
    nvm alias default v$NODE_VERSION && \
    nvm use default
ENV NODE_PATH $NVM_DIR/versions/node/v$NODE_VERSION/lib/node_modules
ENV PATH $NVM_DIR/versions/node/v$NODE_VERSION/bin:$PATH

RUN echo 'export NVM_DIR='$NVM_DIR >> $NVM_PROFILE && \
    echo 'source $NVM_DIR/nvm.sh' >> $NVM_PROFILE && \
    echo 'nvm alias default v'$NODE_VERSION' > /dev/null' >> $NVM_PROFILE && \
    echo 'nvm use default > /dev/null' >> $NVM_PROFILE
