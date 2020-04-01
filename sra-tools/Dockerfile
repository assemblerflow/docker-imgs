# DOCKERFILE for sra-toolkit
FROM ubuntu:16.04
MAINTAINER Tiago F. Jesus, tiagojesus@medicina.ulisboa.pt

# INSTALL DEPENDENCIES
RUN apt-get update && apt-get -y install \
    wget \
    make \
    gcc \
    zlib1g-dev

WORKDIR /ngstools/bin/

# Install pigz
RUN wget http://www.zlib.net/pigz/pigz-2.4.tar.gz

RUN tar xvzf pigz-2.4.tar.gz

WORKDIR /ngstools/bin/pigz-2.4

RUN make

ENV PATH="/ngstools/bin/pigz-2.4/:$PATH"

# Install sra-tools
WORKDIR /ngstools/bin/

RUN wget https://ftp-trace.ncbi.nlm.nih.gov/sra/sdk/2.9.6-1/sratoolkit.2.9.6-1-ubuntu64.tar.gz

RUN tar xvzf sratoolkit.2.9.6-1-ubuntu64.tar.gz

# Remove gz file no longer needed
RUN rm sratoolkit.2.9.6-1-ubuntu64.tar.gz

# add all binaries to the path
ENV PATH="/ngstools/bin/sratoolkit.2.9.6-1-ubuntu64/bin:$PATH"
