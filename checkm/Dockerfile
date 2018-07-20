FROM ubuntu:16.04
MAINTAINER I Mendes <cimendes@medicina.ulisboa.pt>

WORKDIR /NGStools/

# Dependencies
RUN apt-get update && apt-get upgrade -y perl && apt-get install -y python python-pip git wget zip

# Prodigal
RUN git clone https://github.com/hyattpd/Prodigal.git
WORKDIR /NGStools/Prodigal
RUN make install
ENV PATH="/NGStools/Prodigal:$PATH"

WORKDIR /NGStools/

# HMMER
RUN apt install -y hmmer

# PPLACER
RUN wget https://github.com/matsen/pplacer/releases/download/v1.1.alpha19/pplacer-linux-v1.1.alpha19.zip
RUN unzip pplacer-linux-v1.1.alpha19.zip && rm pplacer-linux-v1.1.alpha19.zip
ENV PATH="/NGStools/pplacer-Linux-v1.1.alpha19:$PATH"

# CHECKM
RUN pip install numpy
RUN pip install checkm-genome

# CHECKM DATA FOLDER
WORKDIR /NGStools/checkM_data
RUN wget https://data.ace.uq.edu.au/public/CheckM_databases/checkm_data_2015_01_16.tar.gz
RUN tar xf checkm_data_2015_01_16.tar.gz && rm checkm_data_2015_01_16.tar.gz
RUN echo "/NGStools/checkM_data/" | checkm data setRoot "/NGStools/checkM_data/"

WORKDIR /NGStools/