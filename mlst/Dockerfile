#USE BLAST BINARIES FROM UMMIDOCK REPO
FROM ummidock/blast_binaries:2.9.0-binaries
MAINTAINER Diogo N Silva, diogosilva@medicina.ulisboa.pt

WORKDIR /NGStools/

RUN apt-get update && apt-get install -y \
	libmoo-perl \
	liblist-moreutils-perl \
	libjson-perl \
	libfile-slurp-perl \
	file \
	git \
    python3

# Add any2fasta dependency
RUN git clone https://github.com/tseemann/any2fasta.git
ENV PATH="/NGStools/any2fasta:${PATH}"

RUN git clone https://github.com/tseemann/mlst.git
ENV PATH="/NGStools/mlst/bin:${PATH}"

# apt only has perl version 5.22. Perl version 5.26 is technically not necessary. Removing the check to allow
# older perl version
RUN sed -i 's#use 5.26.0;##g' /NGStools/mlst/bin/mlst

