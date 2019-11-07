FROM dorowu/ubuntu-desktop-lxde-vnc:xenial

MAINTAINER zigzagzackey <yamazaki.keita.xa@alumni.tsukuba.ac.jp>

### Get basic packages
RUN apt-get update -y
RUN apt-get upgrade -y
RUN echo "yes" | apt-get install ttf-mscorefonts-installer -y
RUN echo "1" | apt-get install postfix sasl2-bin -y
RUN apt-get install -y \
    subversion \
    git-core \
    mercurial \
    keychain \
    openssh-client \
    openssh-server \
    g++ \
    g++-multilib \
    build-essential \
    zip \
    unzip \
    p7zip-full \
    python2.7 \
    python-dev \
    apt-file \
    vim \
    scons \
    qt4-dev-tools \
    libpng12-dev \
    libjpeg8 \
    libjpeg8-dev \
    libpng3 \
    libilmbase-dev \
    libxerces-c-dev \
    libglewmx1.6-dev \
    libxxf86vm-dev \
    libbz2-dev \
    htop \
    zlib1g-dev \
    aptitude \
    dkms \
    gedit-plugins \
    gedit-latex-plugin \
    ntp \
    gnome-terminal \
    gimp \
    gimp-ufraw \
    ufraw \
    ufraw-batch \
    dcraw \
    valgrind \
    linux-tools-common \
    smartmontools \
    libapache2-mod-perl2 \
    gnome-disk-utility \
    libapache2-svn \
    subversion-tools \
    gnome-system-tools \
    unrar xml-twig-tools \
    linux-headers-4.15.0-65-generic \
    rsync \
    inkscape \
    irssi \
    mutt \
    s3cmd \
    meshlab \
    openexr \
    libopenexr-dev \
    openexr-viewers \
    libgnome2-bin \
    gparted \
    ubuntu-restricted-extras \
    uml-utilities \
    gpick \
    gnome-color-manager \
    libfftw3-3 \
    libfftw3-dev \
    libboost1.58-all-dev \
    pkg-config

### Reduction for Docker image size
RUN apt-get clean \
    && apt-get autoclean \
    && apt-get autoremove

### Preparation for installations
WORKDIR /Downloads
WORKDIR /install_dirs
RUN echo -e 'PKG_CONFIG_PATH="/usr/local/lib/pkgconfig"' | tee -a /etc/environment > /dev/null
ENV PKG_CONFIG_PATH /usr/local/lib/pkgconfig

### Install and link eigen
RUN curl -L -o /Downloads/eigen-3.2.10.zip https://esa-storage-tokyo.s3-ap-northeast-1.amazonaws.com/uploads/production/attachments/13189/2019/10/14/62987/01dce542-7047-4986-8a6a-6d182456b138.zip
WORKDIR /install_dirs
RUN unzip /Downloads/eigen-3.2.10.zip 
RUN mv eigen-eigen-* eigen_3.2.10
RUN chown -R root:root eigen_3.2.10/
RUN mv eigen_3.2.10/ /usr/local/
WORKDIR /usr/local/
RUN ln -sf eigen_3.2.10/ eigen
RUN ln -sf eigen_3.2.10/ eigen3
WORKDIR /usr/include/
RUN ln -sf /usr/local/eigen eigen3
#RUN cd

### Install MitsubaToFRenderer
WORKDIR /mitsuba
RUN git clone https://github.com/cmu-ci-lab/MitsubaToFRenderer.git 
WORKDIR /mitsuba/MitsubaToFRenderer
RUN scons --clean
RUN scons

WORKDIR /mitsuba

### Setting up MitsubaToFRenderer environment
ENV mitsuba_plugin_dir /mitsuba/MitsubaToFRenderer/dist/plugins
ENV PATH /mitsuba/MitsubaToFRenderer/dist:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
RUN echo "/mitsuba/MitsubaToFRenderer/dist" | tee /etc/ld.so.conf.d/mitsuba.conf > /dev/null
RUN ldconfig

### Initializing the development environment