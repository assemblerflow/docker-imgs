FROM ubuntu:16.04
MAINTAINER Inês Mendes, cimendes@medicina.ulisboa.pt

#DEFINE WORKDIR
WORKDIR /NGStools/

#INSTALL DEPENDENCIES
RUN apt-get update
RUN apt-get install -y make wget bzip2 gcc libz-dev

# INSTALL SAMTOOLS

RUN wget https://sourceforge.net/projects/samtools/files/samtools/1.4.1/samtools-1.4.1.tar.bz2
RUN mkdir samtools && tar jxf samtools-1.4.1.tar.bz2 -C samtools --strip-components=1

WORKDIR /NGStools/samtools/

RUN ./configure --without-curses --disable-bz2 --disable-lzma
RUN make
ENV PATH="/NGStools/samtools:$PATH"

WORKDIR /NGStools/

RUN rm -rf samtools-1.4.1.tar.bz2

#DOWNLOAD AND EXTRACT BWA
RUN wget https://sourceforge.net/projects/bio-bwa/files/bwa-0.7.17.tar.bz2
RUN tar -jxvf bwa-0.7.17.tar.bz2

#CHANGE TO BOWTIE DIR
WORKDIR ./bwa-0.7.17

#RUN MAKE AND ADD TO PATH
RUN make
ENV PATH="/NGStools/bwa-0.7.17:${PATH}"