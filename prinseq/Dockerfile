FROM ubuntu:16.04
MAINTAINER I Mendes <cimendes@medicina.ulisboa.pt>

WORKDIR /NGStools/

# INSTALL DEPENDENCIES
RUN apt-get update && apt-get -y install \
	bzip2 \
	gzip \
	wget \
	python3 \
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

# INSTALL MINICONDA
RUN wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
RUN chmod +x Miniconda3-latest-Linux-x86_64.sh
RUN ./Miniconda3-latest-Linux-x86_64.sh -b -p /NGStools/miniconda
ENV PATH="/NGStools/miniconda/bin:$PATH"
# Configure channels for bioconda
RUN conda config --add channels defaults && conda config --add channels conda-forge && conda config --add channels bioconda

# INSTALL PRINSEQ STANDALONE LITE
RUN conda install -c bioconda prinseq

WORKDIR /data
