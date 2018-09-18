FROM ubuntu:16.04
MAINTAINER Tiago F. Jesus, tiagojesus@medicina.ulisboa.pt

# INSTALL DEPENDENCIES
RUN apt-get update && apt-get -y install \
    python3 \
    wget \
    zip \
    libgomp1

WORKDIR /ngstools/bin/fast_ani

# DOWNLOAD fastANI and install it
RUN wget https://github.com/ParBLiSS/FastANI/releases/download/v1.1/fastani-Linux64-v1.1.zip
RUN unzip fastani-Linux64-v1.1.zip

# Add it to the path
ENV PATH="/ngstools/bin/fast_ani:$PATH"

WORKDIR /ngstools/data/