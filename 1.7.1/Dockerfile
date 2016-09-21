FROM ubuntu:xenial
MAINTAINER Rex Tsai "https://about.me/chihchun"

ENV QMAPSHACK_VERSION "V 1.7.1"
ENV ROUTINO_VERSION "3.1.1"

ENV DEBIAN_FRONTEND noninteractive
ENV HOME /root
RUN apt-get update \
 && apt-get install -y mercurial subversion vim \
 && apt-get build-dep -o APT::Get::Build-Dep-Automatic=true -y qmapshack \
 && apt-get build-dep -o APT::Get::Build-Dep-Automatic=true -y libroutino-dev \
 && apt-get purge -y libroutino-dev libroutino-slim0 libroutino0 routino-common

# Build routino
WORKDIR /tmp
RUN svn checkout http://routino.org/svn/tags/${ROUTINO_VERSION}/ routino
RUN cd routino \
 && make && make install

# Build qmapshack
WORKDIR /tmp
RUN hg clone https://bitbucket.org/maproom/qmapshack -r "${QMAPSHACK_VERSION}" \
 && mkdir build \
 && cd build && cmake ../qmapshack \
 && make && make install

RUN ldconfig
# RUN apt-get autoremove -y 
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
RUN useradd --uid 1000 --create-home -g 100 -d /home/qmapshack qmapshack
USER qmapshack
WORKDIR /home/qmapshack
ENV HOME /home/qmapshack

CMD /usr/local/bin/qmapshack
