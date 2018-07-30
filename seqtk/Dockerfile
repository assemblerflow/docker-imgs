# DOCKERFILE for seqtk https://github.com/lh3/seqtk
FROM ubuntu:16.04
MAINTAINER Diogo N. Silva, diogosilva@medicina.ulisboa.pt

RUN apt-get update && apt-get -y install \
	bzip2 \
	pigz \
	gzip \
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

# INSTALL abricate
RUN conda install -y seqtk
#RUN mkdir -p /NGStools/miniconda3/db/Virulence_finder && cp virulencefinder_db/sequences /NGStools/miniconda3/db/Virulence_finder

WORKDIR /data/ 
