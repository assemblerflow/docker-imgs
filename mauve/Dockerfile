FROM ubuntu:16.04

# File Author / Maintainer
MAINTAINER Inês Mendes <cimendes@medicina.ulisboa.pt>


RUN apt-get update && apt-get -y install \
	bzip2 \
	gzip \
	wget \
	default-jre

WORKDIR /NGStools

RUN wget http://darlinglab.org/mauve/snapshots/2015/2015-02-13/linux-x64/mauve_linux_snapshot_2015-02-13.tar.gz

RUN tar xf mauve_linux_snapshot_2015-02-13.tar.gz && rm mauve_linux_snapshot_2015-02-13.tar.gz

ENV PATH='/NGStools/mauve_snapshot_2015-02-13:/NGStools/mauve_snapshot_2015-02-13/linux-x64'