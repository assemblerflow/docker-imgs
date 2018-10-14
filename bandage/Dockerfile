FROM ubuntu:bionic
LABEL maintainer="sjackan@gmail.com" name="flowcraft/bandage:0.8.1"

RUN apt-get update \
	&& apt-get install -y --no-install-recommends ca-certificates curl unzip \
		libfontconfig1 libgl1 libx11-6 libx11-xcb1 libxcb-glx0 \
	&& rm -rf /var/lib/apt/lists/* \
	&& curl -LO https://github.com/rrwick/Bandage/releases/download/v0.8.1/Bandage_Ubuntu_static_v0_8_1.zip \
	&& unzip Bandage_Ubuntu_static_v0_8_1.zip \
	&& apt-get autoremove -y --purge ca-certificates curl unzip \
	&& rm -f Bandage_Ubuntu_static_v0_8_1.zip \
	&& mv Bandage /usr/local/bin/ \
	&& Bandage --version

WORKDIR /NGStools
