# MitsubaToFRenderer_Docker

## MitsubaToFRenderer Dockerimages

### How to build docker image
```
sudo docker build -t zigzagzackey/mitsubatof_base .
sudo docker build -t zigzagzackey/mitsubatof_linuxbrew .
sudo docker build -t zigzagzackey/mitsubatof_pip .
sudo docker build -t zigzagzackey/mitsubatof_custom .
```

### How to pull docker image
```
sudo docker pull zigzagzackey/mitsubatof_base
sudo docker pull zigzagzackey/mitsubatof_linuxbrew
sudo docker pull zigzagzackey/mitsubatof_pip
sudo docker pull zigzagzackey/mitsubatof_custom
```

### How to run docker container
```
sudo docker run -it zigzagzackey/mitsubatof_base /bin/bash
sudo docker run -it zigzagzackey/mitsubatof_linuxbrew /bin/bash
sudo docker run -it zigzagzackey/mitsubatof_pip /bin/bash
sudo docker run -it zigzagzackey/mitsubatof_custom /bin/bash
```

### USAGE
```
cd MitsubaToFRenderer/scenes/cbox/
mitsuba cbox_unified_all.xml -D samples=16 -D decomposition=none -D tMin=0 -D tMax=20000 -D tRes=20000 -D modulation=none -D lambda=200 -D phase=0
```
Other mitsuba arguments are written [here](https://github.com/cmu-ci-lab/MitsubaToFRenderer/blob/master/USAGE.txt).

### How to remove docker container
```
docker rmi -f [IMAGE ID]
```