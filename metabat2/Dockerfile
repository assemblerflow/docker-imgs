FROM ubuntu:16.04
MAINTAINER I Mendes <cimendes@medicina.ulisboa.pt>

WORKDIR /NGStools/

# INSTALL DEPENDENCIES
RUN apt-get update && apt-get -y install \
	libgomp1 \
	build-essential \
	autoconf \
	libboost-all-dev \
	cmake \
	git \
	curl \
	libncurses5-dev \
	zlib1g-dev

# Samtools 0.1.19
RUN apt-get install -qq samtools

# Bowtie2.1.0
RUN apt-get install -qq bowtie2

# INSTALL METABAT
RUN git clone https://bitbucket.org/berkeleylab/metabat.git

RUN cd metabat && \
    mkdir build && \
    cd build && \
    cmake -DCMAKE_INSTALL_PREFIX=/usr/local .. && \
    make -j8 && \
    make install && \
    cd .. && \
    rm -rf build

