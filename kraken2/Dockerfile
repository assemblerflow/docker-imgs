FROM ubuntu:16.04
MAINTAINER I Mendes <cimendes@medicina.ulisboa.pt>

WORKDIR /NGStools/

# INSTALL DEPENDENCIES
RUN apt-get update && apt-get -y install \
	bzip2 \
	gzip \
	python \
	python3 \
	wget

RUN apt-get -y install rsync

WORKDIR /NGStools

# INSTALL MINICONDA
RUN wget https://repo.continuum.io/miniconda/Miniconda2-latest-Linux-x86_64.sh
RUN chmod +x Miniconda2-latest-Linux-x86_64.sh
RUN ./Miniconda2-latest-Linux-x86_64.sh -b -p /NGStools/miniconda
ENV PATH="/NGStools/miniconda/bin:$PATH"
# Configure channels for bioconda
RUN conda config --add channels defaults && conda config --add channels conda-forge && \
    conda config --add channels bioconda

# INSTALL kraken
RUN conda install -c bioconda kraken2

WORKDIR /kraken_db

# minikraken DB kraken2 - refseq bacteria, archaea, and viral libraries
RUN wget ftp://ftp.ccb.jhu.edu/pub/data/kraken2_dbs/minikraken2_v1_8GB_201904_UPDATE.tgz && \
    tar xf minikraken2_v1_8GB_201904_UPDATE.tgz && rm minikraken2_v1_8GB_201904_UPDATE.tgz

ENV KRAKEN2_DB_PATH="/kraken_db:${KRAKEN2_DB_PATH}"

WORKDIR /data/