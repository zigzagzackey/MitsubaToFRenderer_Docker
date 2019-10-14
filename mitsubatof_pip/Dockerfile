FROM zigzagzackey/mitsubatof_linuxbrew

MAINTAINER zigzagzackey <yamazaki.keita.xa@alumni.tsukuba.ac.jp>
ARG DEBIAN_FRONTEND=noninteractive

WORKDIR /Downloads

### Get package for pyenv-install
RUN apt-get update \
    && apt-get install -y \
    make\
    build-essential \
    libssl-dev \
    zlib1g-dev \
    libbz2-dev \
    libreadline-dev \
    libsqlite3-dev \
    wget \
    curl \
    llvm \
    libncurses5-dev \
    libncursesw5-dev \
    xz-utils \
    tk-dev \
    libffi-dev \
    liblzma-dev \
    python-openssl \
    git \
    && apt-get clean

### Install pyenv
RUN brew install pyenv
RUN pyenv -v

### Setting up pyenv environment
ENV PYENV_ROOT=/.pyenv
ENV PATH=$PYENV_ROOT/bin:$PYENV_ROOT/shims/:$PATH
RUN eval "$(pyenv init -)"

### Install Python from pyenv
RUN pyenv install $(pyenv install -l | grep -v '[a-zA-Z]' | grep -e '\s2\.?*' | tail -1)
RUN pyenv install $(pyenv install -l | grep -v '[a-zA-Z]' | grep -e '\s3\.?*' | tail -1)
RUN pyenv global $(pyenv install -l | grep -v '[a-zA-Z]' | grep -e '\s3\.?*' | tail -1)

WORKDIR /mitsuba