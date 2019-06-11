# DOCKERFILE to run mapping for pATLAS
FROM ubuntu:16.04
MAINTAINER Tiago F. Jesus, tiagojesus@medicina.ulisboa.pt

# INSTALL DEPENDENCIES
RUN apt-get update && apt-get -y install \
    python3 \
    python3-pip \
    python3-setuptools \
    python3-biopython \
    git

WORKDIR /ngstools/bin/

# update pip3
RUN pip3 install --upgrade pip

# install dependency for setup.py
RUN pip3 install Cython

# install the package itself
RUN git clone https://github.com/tiagofilipe12/plasmidpredictor

WORKDIR /ngstools/bin/plasmidpredictor

RUN python3 setup.py install

ENV PATH="/ngstools/bin/plasmidpredictor/scripts/:$PATH"

WORKDIR /ngstools/data/
