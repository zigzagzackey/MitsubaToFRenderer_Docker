FROM zigzagzackey/mitsubatof_base

MAINTAINER zigzagzackey <yamazaki.keita.xa@alumni.tsukuba.ac.jp>
ARG DEBIAN_FRONTEND=noninteractive

RUN apt install python3-pip -y

### Install python modules using pip3
RUN pip3 install --upgrade pip
RUN pip3 install scipy
RUN pip3 install opencv-python --trusted-host pypi.python.org
RUN pip3 install matplotlib
RUN pip3 install pillow
RUN pip3 install OpenEXR
RUN pip3 install imath
RUN pip3 install imageio
RUN pip3 install tqdm

RUN pip3 install numpy
RUN pip3 install scipy
RUN pip3 install opencv-python
RUN pip3 install matplotlib
RUN pip3 install lxml
RUN pip3 install tqdm
RUN pip3 install joblib

WORKDIR /mitsuba