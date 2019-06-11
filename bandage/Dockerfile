FROM linuxbrew/linuxbrew:latest
LABEL maintainer="sjackan@gmail.com" name="flowcraft/bandage:0.8.1"

RUN sudo apt-get update \
	&& sudo apt-get install -y --no-install-recommends unzip \
		libfontconfig1 libgl1 libx11-6 libx11-xcb1 libxcb-glx0 \
	&& sudo rm -r /var/lib/apt/lists/* \
	&& curl -LO https://github.com/rrwick/Bandage/releases/download/v0.8.1/Bandage_Ubuntu_static_v0_8_1.zip \
	&& unzip Bandage_Ubuntu_static_v0_8_1.zip \
	&& sudo apt-get autoremove -y --purge unzip \
	&& rm Bandage_Ubuntu_static_v0_8_1.zip \
	&& sudo mv Bandage /usr/local/bin/ \
	&& Bandage --version \
	&& brew install blast \
	&& rm -r $(brew --cache)

WORKDIR /NGStools
