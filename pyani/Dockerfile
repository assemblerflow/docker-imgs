FROM python:3
MAINTAINER Bruno Goncalves <bfgoncalves@medicina.ulisboa.pt>

RUN apt-get update && apt-get install -y \
			       ncbi-blast+ \
			       mummer \
			       && \
    pip3 install --upgrade pip && \
    pip3 install pyani

WORKDIR /fasta_dir
