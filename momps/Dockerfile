# DOCKERFILE for seqtk https://github.com/lh3/seqtk
FROM ubuntu:16.04
MAINTAINER Diogo N. Silva, diogosilva@medicina.ulisboa.pt

RUN apt-get update && apt-get -y install \
	bzip2 \
	gzip \
	git \
	bash \
	zip \
	wget
# git needs to be present to allow DB update

WORKDIR /NGStools

# INSTALL MINICONDA
RUN wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
RUN chmod +x Miniconda3-latest-Linux-x86_64.sh
RUN ./Miniconda3-latest-Linux-x86_64.sh -b -p /NGStools/miniconda
ENV PATH="/NGStools/miniconda/bin:$PATH"
# Configure channels for bioconda
RUN conda update -y -n base conda && conda config --add channels conda-forge && conda config --add channels defaults &&  conda config --add channels bioconda

RUN conda install -y blast bwa samtools picard freebayes perl ncurses

RUN git clone https://github.com/ODiogoSilva/mompS.git
RUN chmod +x /NGStools/mompS/momps.pl
ENV PATH="/NGStools/mompS:$PATH"

# Replace schema with custom one
RUN wget https://github.com/assemblerflow/docker-imgs/raw/master/momps/L_pneumophila_alleles.zip
RUN rm mompS/schema/* && unzip L_pneumophila_alleles.zip -d mompS/schema

# Replace config file
RUN rm mompS/config.txt && wget https://github.com/assemblerflow/docker-imgs/raw/master/momps/config.txt && mv config.txt mompS/

# Path issue with bwa fields
RUN sed -i 's/\\t/\\\\t/g' mompS/mompS_2_pipe.pl

WORKDIR /NGStools/mompS

