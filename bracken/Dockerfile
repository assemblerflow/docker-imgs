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

WORKDIR /NGStools

# INSTALL MINICONDA
RUN wget https://repo.continuum.io/miniconda/Miniconda2-latest-Linux-x86_64.sh
RUN chmod +x Miniconda2-latest-Linux-x86_64.sh
RUN ./Miniconda2-latest-Linux-x86_64.sh -b -p /NGStools/miniconda
ENV PATH="/NGStools/miniconda/bin:$PATH"
# Configure channels for bioconda
RUN conda config --add channels defaults && conda config --add channels conda-forge && conda config --add channels bioconda

# INSTALL kraken
RUN conda install -c bioconda bracken

WORKDIR /braken_db

# minikraken DB kraken2 v1 - refseq bacteria, archaea, and viral libraries
RUN mkdir minikraken2_v1_8GB/ && cd minikraken2_v1_8GB/

RUN wget https://ccb.jhu.edu/software/bracken/dl/minikraken2_v1/database100mers.kmer_distrib
RUN wget https://ccb.jhu.edu/software/bracken/dl/minikraken2_v1/database150mers.kmer_distrib
RUN wget https://ccb.jhu.edu/software/bracken/dl/minikraken2_v1/database200mers.kmer_distrib

WORKDIR /data/