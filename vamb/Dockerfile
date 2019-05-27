FROM ubuntu:16.04
MAINTAINER I Mendes <cimendes@medicina.ulisboa.pt>

WORKDIR /NGStools/

# INSTALL DEPENDENCIES
RUN apt-get update && apt-get -y install \
	git \
	wget \
	unzip \
	bzip2

# INSTALL MINICONDA python 3 version
RUN wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
RUN chmod +x Miniconda3-latest-Linux-x86_64.sh
RUN ./Miniconda3-latest-Linux-x86_64.sh -b -p /NGStools/miniconda
ENV PATH="/NGStools/miniconda/bin:$PATH"
# Configure channels for bioconda
RUN conda config --add channels defaults && conda config --add channels conda-forge && conda config --add channels bioconda

# INSTALL PYTHON DEPENDENCIES
RUN conda update --yes conda && conda install numpy pysam

# Avoid undefined symbol error with conda
RUN conda install pytorch cuda80 -c soumith

# INSTALL VAMB
RUN wget https://github.com/RasmussenLab/vamb/archive/v1.0.1.zip
RUN unzip v1.0.1.zip && rm v1.0.1.zip
RUN mv vamb-1.0.1/ vamb/

ENV PATH="/NGStools/vamb:$PATH"



