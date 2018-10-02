FROM ubuntu:16.04
MAINTAINER I Mendes <cimendes@medicina.ulisboa.pt>

WORKDIR /NGStools/

# INSTALL DEPENDENCIES
RUN apt-get update && apt-get -y install \
    wget \
    bzip2 \
    curl \
    make

RUN wget https://github.com/marbl/Krona/releases/download/v2.7/KronaTools-2.7.tar

RUN tar xf KronaTools-2.7.tar && rm KronaTools-2.7.tar

WORKDIR /NGStools/KronaTools-2.7/

RUN ./install.pl --prefix /NGStools/KronaTools-2.7/

RUN ./updateTaxonomy.sh

ENV PATH="/NGStools/KronaTools-2.7/bin:$PATH"

WORKDIR /data/


