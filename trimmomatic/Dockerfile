# DOCKERFILE for trimmomatic 
FROM ubuntu:16.04
MAINTAINER Inês Mendes, cimendes@medicina.ulisboa.pt

RUN apt-get update && apt-get -y install \
    openjdk-8-jre \
	python3 \
    unzip

ADD http://www.usadellab.org/cms/uploads/supplementary/Trimmomatic/Trimmomatic-0.39.zip /NGStools/

WORKDIR /NGStools

RUN unzip Trimmomatic-0.39.zip
WORKDIR /NGStools/Trimmomatic-0.39

RUN mv trimmomatic-0.39.jar trimmomatic.jar
