FROM ubuntu:16.04
MAINTAINER I Mendes <cimendes@medicina.ulisboa.pt>

WORKDIR /NGStools/

# INSTALL DEPENDENCIES
RUN apt-get update && apt-get -y install \
	python \
	python-pip \
	wget \
	zip \
	mercurial

RUN pip install --upgrade pip
RUN pip install numpy matplotlib scipy biopython

WORKDIR /NGStools/

# INSTALL BOWTIE
RUN wget https://sourceforge.net/projects/bowtie-bio/files/bowtie2/2.2.9/bowtie2-2.2.9-linux-x86_64.zip && unzip bowtie2-2.2.9-linux-x86_64.zip && rm bowtie2-2.2.9-linux-x86_64.zip
ENV PATH="/NGStools/bowtie2-2.2.9:$PATH"

#CLONE METAPHIAN2
RUN  hg clone https://bitbucket.org/biobakery/metaphlan2
ENV PATH="/NGStools/metaphlan2:$PATH"
ENV PATH="/NGStools/metaphlan2/utils:$PATH"

WORKDIR /NGStools/metaphlan2/
RUN metaphlan2.py --install
RUN export mpa_dir="/NGStools/metaphlan2/metaphlan_databases/"

