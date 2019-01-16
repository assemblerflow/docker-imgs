# DOCKERFILE for rematch https://github.com/B-UMMI/ReMatCh
FROM ubuntu:16.04
MAINTAINER Inês Mendes, cimendes@medicina.ulisboa.pt

RUN apt-get update && apt-get -y install \
	git \
	wget  \
	python \
	python3 \
	python3-pip \
	parallel

RUN pip3 install setuptools

WORKDIR /NGStools

# INSTALL REMATCH

RUN git clone https://github.com/B-UMMI/ReMatCh.git && \
    cd ReMatCh && \
    python3 setup.py install

ENV PATH="/NGStools/ReMatCh/src/bcftools-1.3.1/bin:$PATH"
ENV PATH="/NGStools/ReMatCh/src/bowtie2-2.2.9"$PATH
ENV PATH="/NGStools/ReMatCh/src/samtools-1.3.1/bin"$PATH

WORKDIR /NGStools

ENV PATH="/NGStools/ReMatCh:$PATH"


