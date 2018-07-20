FROM flowcraft/bowtie2_samtools:1.0.0-1
MAINTAINER I Mendes, cimendesa@medicina.ulisboa.pt

RUN apt-get update && apt-get -y install \
	python-pip \
	python-dev \
	build-essential \
	mercurial

RUN pip install biopython==1.63 pysam>=0.11.1

RUN hg clone https://bitbucket.org/CibioCM/metamlst

ENV PATH="/NGStools/metamlst:$PATH"

WORKDIR index

RUN metamlst-index.py -i metamlstDB_2017 /NGStools/metamlst/metamlstDB_2017.db

ENV PATH="/NGStools/index:$PATH"

WORKDIR /data
