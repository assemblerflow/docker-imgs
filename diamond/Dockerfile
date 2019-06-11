FROM ubuntu:16.04
LABEL maintainer="tiagojesus@medicina.ulisboa.pt"

RUN apt-get update && apt-get -y install \
    wget

WORKDIR /ngstools/bin/

# install diamond
RUN wget http://github.com/bbuchfink/diamond/releases/download/v0.9.22/diamond-linux64.tar.gz
RUN tar xzf diamond-linux64.tar.gz
RUN rm diamond-linux64.tar.gz *.pdf LICENSE

ENV PATH="/ngstools/bin/:$PATH"

WORKDIR /ngstools/data/
