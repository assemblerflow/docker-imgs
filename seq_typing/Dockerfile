# DOCKERFILE for seq_typing https://github.com/B-UMMI/seq_typing
FROM ummidock/rematch:3.3.0-1
MAINTAINER I Mendes, cimendes@medicina.ulisboa.pt

RUN apt-get update && apt-get -y install \
	python3-pip && pip3 install setuptools

WORKDIR /NGStools

# BLAST
RUN wget ftp://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/2.6.0/ncbi-blast-2.6.0+-x64-linux.tar.gz && tar xf ncbi-blast-2.6.0+-x64-linux.tar.gz && rm ncbi-blast-2.6.0+-x64-linux.tar.gz
ENV PATH="/NGStools/ncbi-blast-2.6.0+/bin:$PATH"

# Seq_Typing
RUN git clone https://github.com/B-UMMI/seq_typing.git
RUN cd seq_typing && \
    python3 setup.py install

WORKDIR /data/

