# DOCKERFILE for sra-toolkit
FROM ubuntu:16.04
MAINTAINER Tiago F. Jesus, tiagojesus@medicina.ulisboa.pt

# INSTALL DEPENDENCIES
RUN apt-get update && apt-get -y install \
    wget

WORKDIR /ngstools/bin/

RUN wget http://ftp-trace.ncbi.nlm.nih.gov/sra/sdk/2.9.1-1/sratoolkit.2.9.1-1-ubuntu64.tar.gz

RUN tar xvzf sratoolkit.2.9.1-1-ubuntu64.tar.gz

# Remove gz file no longer needed
RUN rm sratoolkit.2.9.1-1-ubuntu64.tar.gz

# add all binaries to the path
ENV PATH="/ngstools/bin/sratoolkit.2.9.1-1-ubuntu64/bin:$PATH"
