FROM debian:9.0
MAINTAINER finlay@dragonfly.co.nz

RUN apt-get update \
	&& apt-get install -y --no-install-recommends \
       vim git make cmake zlib1g-dev ca-certificates gcc \
	&& rm -rf /var/lib/apt/lists/*

##  https://github.com/kdmurray91/axe
RUN git clone --recursive https://github.com/kdmurray91/axe.git axe
RUN mkdir -p axe/build
RUN cd axe/build && cmake ..
RUN cd axe/build && make
RUN cd axe/build && make install

##  https://github.com/kdmurray91/seqhax
RUN git clone https://github.com/kdmurray91/seqhax.git
RUN mkdir seqhax/build
RUN cd seqhax/build && cmake ..
RUN cd seqhax/build && make
RUN cd seqhax/build && make install

RUN apt-get update
RUN apt-get install -y --no-install-recommends curl fastqc

