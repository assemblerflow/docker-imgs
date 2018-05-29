# DOCKERFILE for true coverage
FROM ummidock/rematch:3.2.0-2
MAINTAINER Diogo N. Silva, diogosilva@medicina.ulisboa.pt

WORKDIR /NGStools

RUN git clone https://github.com/B-UMMI/INNUca.git && cd INNUca && \
	git checkout tags/v3.2 && cd .. && \
	mkdir true_coverage && \
	mv INNUca/modules/trueCoverage_rematch true_coverage/data && \
	mv INNUca/modules/trueCoverage_rematch.py true_coverage/ && \
	mv INNUca/modules/utils.py true_coverage/ && \
	chmod +x true_coverage/trueCoverage_rematch.py && \
	rm -rf INNUca

WORKDIR /data/

ENV PATH="/NGStools/true_coverage/:$PATH"

