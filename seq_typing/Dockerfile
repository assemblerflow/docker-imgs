# DOCKERFILE for seq_typing https://github.com/B-UMMI/seq_typing
FROM ummidock/rematch:3.3.0-1
MAINTAINER Diogo N. Silva, diogosilva@medicina.ulisboa.pt

RUN apt-get update && apt-get -y install \
	python3-pip

WORKDIR /NGStools

RUN git clone https://github.com/B-UMMI/seq_typing.git
RUN pip3 install future biopython
ENV PATH="/NGStools/seq_typing:$PATH"

RUN chmod -R o+wr /NGStools/

RUN wget ftp://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/2.6.0/ncbi-blast-2.6.0+-x64-linux.tar.gz && tar xf ncbi-blast-2.6.0+-x64-linux.tar.gz && rm ncbi-blast-2.6.0+-x64-linux.tar.gz

ENV PATH="/NGStools/ncbi-blast-2.6.0+/bin:$PATH"

WORKDIR /data/

