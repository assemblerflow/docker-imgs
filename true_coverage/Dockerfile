# DOCKERFILE for true coverage
FROM flowcraft/rematch:4.0.1-1
MAINTAINER Diogo N. Silva, diogosilva@medicina.ulisboa.pt

WORKDIR /NGStools

RUN git clone https://github.com/B-UMMI/INNUca.git && \
	mkdir true_coverage && \
	mv INNUca/modules/trueCoverage_rematch true_coverage/data && \
	mv INNUca/modules/trueCoverage_rematch.py true_coverage/ && \
	mv INNUca/modules/utils.py true_coverage/ && \
	chmod +x true_coverage/trueCoverage_rematch.py && \
	rm -rf INNUca

WORKDIR /data/

ENV PATH="/NGStools/true_coverage/:$PATH"

