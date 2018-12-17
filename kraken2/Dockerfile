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
RUN conda install -c bioconda kraken2

WORKDIR /kraken_db

# minikraken DB kraken2 - refseq bacteria, archaea, and viral libraries
RUN mkdir minikraken2_v1_8GB/ && cd minikraken2_v1_8GB/ && wget https://ccb.jhu.edu/software/kraken2/dl/minikraken2_v1_8GB.tgz && tar xf minikraken2_v1_8GB.tgz && rm minikraken2_v1_8GB.tgz

ENV KRAKEN2_DB_PATH="/kraken_db:${KRAKEN2_DB_PATH}"

WORKDIR /data/