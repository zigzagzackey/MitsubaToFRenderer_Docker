FROM zigzagzackey/mitsubatof_base

MAINTAINER zigzagzackey <yamazaki.keita.xa@alumni.tsukuba.ac.jp>
ARG DEBIAN_FRONTEND=noninteractive

### Get package for linuxbrew
RUN apt-get update \
	&& apt-get install -y --no-install-recommends ca-certificates curl file g++ git locales make uuid-runtime \
	&& apt-get clean \
	&& rm -rf /var/lib/apt/lists/* \
	&& localedef -i en_US -f UTF-8 en_US.UTF-8 \
	&& useradd -m -s /bin/bash linuxbrew \
	&& echo 'linuxbrew ALL=(ALL) NOPASSWD:ALL' >>/etc/sudoers

WORKDIR /home/linuxbrew

### Install linuxbrew
RUN git clone https://github.com/Homebrew/brew /home/linuxbrew/.linuxbrew/Homebrew
WORKDIR /home/linuxbrew/.linuxbrew/bin
WORKDIR /home/linuxbrew/.linuxbrew/etc
WORKDIR /home/linuxbrew/.linuxbrew/include
WORKDIR /home/linuxbrew/.linuxbrew/lib
WORKDIR /home/linuxbrew/.linuxbrew/opt 
WORKDIR /home/linuxbrew/.linuxbrew/sbin 
WORKDIR /home/linuxbrew/.linuxbrew/share 
WORKDIR /home/linuxbrew/.linuxbrew/var/homebrew/linked 
WORKDIR /home/linuxbrew/.linuxbrew/Cellar
WORKDIR /home/linuxbrew
RUN chown -R $(whoami) /home/linuxbrew/.linuxbrew/etc
RUN chown -R $(whoami) /home/linuxbrew/.linuxbrew/include
RUN chown -R $(whoami) /home/linuxbrew/.linuxbrew/lib
RUN chown -R $(whoami) /home/linuxbrew/.linuxbrew/opt 
RUN chown -R $(whoami) /home/linuxbrew/.linuxbrew/sbin 
RUN chown -R $(whoami) /home/linuxbrew/.linuxbrew/share 
RUN chown -R $(whoami) /home/linuxbrew/.linuxbrew/var/homebrew/linked 
RUN chown -R $(whoami) /home/linuxbrew/.linuxbrew/Cellar
RUN ln -s ../Homebrew/bin/brew /home/linuxbrew/.linuxbrew/bin
RUN eval $(/home/linuxbrew/.linuxbrew/bin/brew shellenv)

### Setting up linuxbrew environment
ENV PATH=/home/linuxbrew/.linuxbrew/bin:/home/linuxbrew/.linuxbrew/sbin:$PATH
ENV MANPATH /home/linuxbrew/.linuxbrew/share/man
ENV INFOPATH /home/linuxbrew/.linuxbrew/share/info
ENV LD_LIBRARY_PATH /home/linuxbrew/.linuxbrew/lib

### Check linuxbrew
RUN brew doctor

WORKDIR /mitsuba