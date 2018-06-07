FROM ubuntu:16.04
MAINTAINER Inês Mendes <cimendes@medicina.ulisboa.pt>

WORKDIR /NGStools/

RUN apt-get update

# Dependencies
RUN apt-get install -y git python2.7 python-dev python-pip wget unzip bats awscli curl zlib1g-dev libbz2-dev \
    liblzma-dev libcurl4-openssl-dev libssl1.0.0 libssl-dev libtbb-dev g++ && pip install -U pandas==0.20.3 \
    biopython==1.70 numpy==1.13.1 scipy==0.19.1 awscli==1.11.146 boto3==1.4.7 pysam==0.13

# HMMER
RUN wget http://eddylab.org/software/hmmer3/3.1b2/hmmer-3.1b2-linux-intel-x86_64.tar.gz && tar xf hmmer-3.1b2-linux-intel-x86_64.tar.gz && rm hmmer-3.1b2-linux-intel-x86_64.tar.gz

# vsearch
RUN wget https://github.com/torognes/vsearch/releases/download/v2.4.3/vsearch-2.4.3-linux-x86_64.tar.gz && tar xf vsearch-2.4.3-linux-x86_64.tar.gz && rm vsearch-2.4.3-linux-x86_64.tar.gz

# Samtools
RUN wget https://github.com/samtools/samtools/releases/download/1.4/samtools-1.4.tar.bz2 && tar xf samtools-1.4.tar.bz2 && rm samtools-1.4.tar.bz2

# MIDAS
RUN wget https://github.com/snayfach/MIDAS/archive/v1.3.2.tar.gz && \
	tar xzf v1.3.2.tar.gz && \
	python MIDAS-1.3.2/setup.py install && \
    rm /NGStools/MIDAS-1.3.2/bin/Linux/samtools && \
	rm /NGStools/MIDAS-1.3.2/bin/Linux/bowtie2*

# Samtools
RUN wget https://github.com/samtools/samtools/releases/download/1.4/samtools-1.4.tar.bz2 && \
	tar xf samtools-1.4.tar.bz2 && \
	cd samtools-1.4 && \
	./configure --without-curses && \
	make && \
	make install && \
	rm /usr/local/bin/samtools && \
	ln -s /NGStools/samtools-1.4/samtools /NGStools/MIDAS-1.3.2/bin/Linux/ && \
	ln -s /NGStools/samtools-1.4/samtools /usr/local/bin/ && \
	rm /NGStools/samtools-1.4.tar.bz2

# Bowtie
RUN wget https://sourceforge.net/projects/bowtie-bio/files/bowtie2/2.3.2/bowtie2-2.3.2-linux-x86_64.zip && \
	unzip bowtie2-2.3.2-linux-x86_64.zip && \
	rm bowtie2-2.3.2-linux-x86_64.zip && \
	cd bowtie2-2.3.2 && \
	ln -s /NGStools/bowtie2-2.3.2/bowtie2* /NGStools/MIDAS-1.3.2/bin/Linux/ && \
	ln -s /NGStools/bowtie2-2.3.2/bowtie2* /usr/local/bin/

ENV PYTHONPATH="/NGStools/MIDAS-1.3.2"
ENV PATH="/NGStools/MIDAS-1.3.2/scripts:/NGStools/hmmer-3.1b2-linux-intel-x86_64/binaries:/NGStools/vsearch-2.4.3-linux-x86_64/bin:${PATH}"

# Clean
RUN apt-get remove -y git python-pip wget && apt-get autoclean -y

WORKDIR /data/
