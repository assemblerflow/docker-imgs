FROM ubuntu:16.04
MAINTAINER I Mendes <cimendes@medicina.ulisboa.pt>

RUN apt-get update && apt-get -y install \
	wget \
	build-essential \
	libgsl0-dev \
	libgomp1 \
	git \
	zip \
	unzip

WORKDIR /NGStools

# INSTALL MINICONDA
RUN wget https://repo.continuum.io/miniconda/Miniconda2-latest-Linux-x86_64.sh
RUN chmod +x Miniconda2-latest-Linux-x86_64.sh
RUN ./Miniconda2-latest-Linux-x86_64.sh -b -p /NGStools/miniconda
ENV PATH="/NGStools/miniconda/bin:$PATH"
# Configure channels for bioconda
RUN conda config --add channels defaults && conda config --add channels conda-forge && conda config --add channels bioconda

# INSTALL DEPENDENCIES
# Samtools 0.1.19
RUN apt-get install -qq samtools

# Bowtie2.1.0
RUN apt-get install -qq bowtie2

# Parallel 20130622-1
RUN apt-get install -qq parallel

# Install R
RUN apt-get install -qq r-base

# Install R packages
RUN RREPO='"http://cran.rstudio.com/"';\
    printf "install.packages(\"ggplot2\", repo=$RREPO)\ninstall.packages(\"reshape\",repo=$RREPO)\ninstall.packages(\"gplots\",repo=$RREPO)\ninstall.packages(\"ellipse\",repo=$RREPO)\ninstall.packages(\"grid\",repo=$RREPO)\ninstall.packages(\"getopt\",repo=$RREPO)" > dep.R;\
    Rscript dep.R

# INSTALL CONCOCT AND PYTHON DEPENDENCIES TRHOUGH CONDA
RUN conda update --yes conda && conda install concoct



