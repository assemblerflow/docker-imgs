# DOCKERFILE for seq_typing https://github.com/B-UMMI/seq_typing
FROM ummidock/rematch:3.3.0-1
MAINTAINER C I Mendes, cimendes@medicina.ulisboa.pt

RUN apt-get update && apt-get -y install \
	python3-pip \
	wget \
	zip

WORKDIR /NGStools

RUN wget ftp://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/2.6.0/ncbi-blast-2.6.0+-x64-linux.tar.gz && tar xf ncbi-blast-2.6.0+-x64-linux.tar.gz && rm ncbi-blast-2.6.0+-x64-linux.tar.gz

ENV PATH="/NGStools/ncbi-blast-2.6.0+/bin:$PATH"

RUN git clone https://github.com/B-UMMI/seq_typing.git -b assemblies
RUN pip3 install future
ENV PATH="/NGStools/seq_typing:$PATH"

RUN chmod -R o+wr /NGStools/

# Reference File

WORKDIR /dengue_DB

RUN wget https://github.com/assemblerflow/docker-imgs/files/2306260/GenotypesDENV_14-05-18.problematic_sequences_corrected.fasta.corrected.fasta.iupac_removed.fasta.zip
RUN unzip GenotypesDENV_14-05-18.problematic_sequences_corrected.fasta.corrected.fasta.iupac_removed.fasta.zip

RUN seq_typing.py blast -f GenotypesDENV_14-05-18.problematic_sequences_corrected.fasta.corrected.fasta.iupac_removed.fasta -t nucl -o blast_db/

WORKDIR /data/