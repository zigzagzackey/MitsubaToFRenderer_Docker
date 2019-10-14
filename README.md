# MitsubaToFRenderer_Docker

## MitsubaToFRenderer Base

### How to pull docker image
```
sudo docker pull zigzagzackey/mitsubatof_base
```

### How to run docker container
```
docker run -it zigzagzackey/mitsubatof_base /bin/bash
```

### USAGE
```
cd MitsubaToFRenderer/scenes/cbox/
mitsuba cbox_unified_all.xml -D samples=16 -D decomposition=none -D tMin=0 -D tMax=20000 -D tRes=20000 -D modulation=none -D lambda=200 -D phase=0
```
Other mitsuba arguments are written [here](https://github.com/cmu-ci-lab/MitsubaToFRenderer/blob/master/USAGE.txt).