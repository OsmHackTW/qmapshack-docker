qmapshack within Ubuntu 16.04.

# Features

- Ubuntu 16.04
- qmapshack
- routino


## Usage

    docker run --rm -t -i -v [maps dir]:/home/qmapshack -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=$DISPLAY osmtw/qmapshack


[![Docker Automated build](https://img.shields.io/docker/automated/osmtw/qmapshack.svg?maxAge=2592000)](https://hub.docker.com/r/osmtw/qmapshack/)

[![](https://images.microbadger.com/badges/image/osmtw/qmapshack.svg)](https://microbadger.com/images/osmtw/qmapshack)
