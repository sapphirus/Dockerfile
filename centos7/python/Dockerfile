FROM centos:7

MAINTAINER "Amakasu Ryoma"

RUN yum update -y && yum clean all && yum install -y \
    gcc gcc-c++ make git curl-devel openssl-devel patch \
    bzip2-devel zlib-devel readline-devel libffi-devel libxslt-devel \
    sqlite sqlite-devel python-devel

# Python
## pyenv と virtualenv を install
RUN git clone https://github.com/yyuu/pyenv.git /usr/local/pyenv && \
    git clone https://github.com/yyuu/pyenv-virtualenv.git /usr/local/pyenv/plugins/pyenv-virtualenv
ENV PYENV_ROOT /usr/local/pyenv
ENV PATH ${PYENV_ROOT}/bin:${PATH}
ENV eval "$(pyenv init -)"
ENV PYTHON_VERSION 3.5.2
## pyenv で Python 3.5.2 を install
RUN pyenv install $PYTHON_VERSION && \
    pyenv global $PYTHON_VERSION && pyenv rehash
## pip を install
RUN curl -kL https://bootstrap.pypa.io/get-pip.py | python
## ansible
RUN pip install ansible
# RUN ansible --version
