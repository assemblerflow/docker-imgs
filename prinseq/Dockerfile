FROM ubuntu:16.04
MAINTAINER I Mendes <cimendes@medicina.ulisboa.pt>

WORKDIR /NGStools/

# INSTALL DEPENDENCIES
RUN apt-get update && apt-get -y install \
	bzip2 \
	gzip \
	wget \
	gcc

# INSTALL PERL AND CPAN
RUN apt-get -y install perl \
    build-essential \
    libxi-dev \
    libxmu-dev \
    freeglut3-dev \
    libgsl0-dev \
    libnetpbm10-dev \
    libplplot-dev \
    pgplot5 \
    gfortran \
    curl \
    libcairo2-dev

RUN curl -L http://cpanmin.us | perl - App::cpanminus

# INSTALL PERL MODULES - PRINSEQ LITE
RUN cpanm  Getopt::Long \
    Pod::Usage \
    File::Temp \
    Fcntl \
    Digest::MD5 \
    Cwd \
    List::Util

# INSTALL PERL MODULES - PRINSEQ GRAPH

RUN cpanm --force Text::SimpleTable

RUN cpanm JSON \
    Cairo \
    Statistics::PCA \
    MIME::Base64

# INSTALL PRINSEQ STANDALONE LITE
RUN wget https://sourceforge.net/projects/prinseq/files/standalone/prinseq-lite-0.20.4.tar.gz
RUN tar xf prinseq-lite-0.20.4.tar.gz && rm prinseq-lite-0.20.4.tar.gz

WORKDIR /NGStools/prinseq-lite-0.20.4/
RUN mv prinseq-lite.pl prinseq-lite && chmod +x prinseq-lite
RUN mv prinseq-graphs.pl prinseq-graphs && chmod +x prinseq-graphs
RUN mv prinseq-graphs-noPCA.pl prinseq-graphs-noPCA && chmod +x prinseq-graphs-noPCA

ENV PATH="/NGStools/prinseq-lite-0.20.4:$PATH"

WORKDIR /data