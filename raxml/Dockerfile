# RAxML
# https://github.com/stamatak/standard-RAxML/
# v8.2.11-PTHREADS-SSE3

# base image: Ubuntu
FROM ubuntu:16.04

# File Author / Maintainer
MAINTAINER Inês Mendes <cimendes@medicina.ulisboa.pt>


WORKDIR /NGStools

RUN apt-get update --fix-missing && apt-get install -y wget gcc make

RUN wget https://github.com/stamatak/standard-RAxML/archive/v8.2.11.tar.gz
RUN tar -xzvf v8.2.11.tar.gz  && rm -rf v8.2.11.tar.gz

RUN cd standard-RAxML-8.2.11 && make -f Makefile.SSE3.PTHREADS.gcc

RUN ln -s /NGStools/standard-RAxML-8.2.11/raxmlHPC-PTHREADS-SSE3 /usr/local/bin/raxmlHPC

ENV PATH="/NGStools/standard-RAxML-8.2.11:${PATH}"

RUN apt-get install -y python3-pip

RUN pip3 install dendropy