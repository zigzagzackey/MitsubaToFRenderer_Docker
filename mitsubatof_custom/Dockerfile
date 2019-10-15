FROM zigzagzackey/mitsubatof_pip

MAINTAINER zigzagzackey <yamazaki.keita.xa@alumni.tsukuba.ac.jp>
ARG DEBIAN_FRONTEND=noninteractive

WORKDIR /Downloads

### Upgrade Homebrew
RUN brew upgrade

### Install python modules using pip
RUN pip install numpy
RUN pip install scipy
RUN pip install opencv-python
RUN pip install matplotlib
RUN pip install lxml
RUN pip install tqdm
RUN pip install joblib

WORKDIR /mitsuba