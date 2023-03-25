# work from ubuntu 18.04 base image
FROM ubuntu:18.04

# set the environment variables
ARG SOFTWARE="samtools"
ARG VERSION=1.9
LABEL software.name=${SOFTWARE}
LABEL software.version=${VERSION}
LABEL software.description="Utilities for the Sequence Alignment/Map (SAM/BAM/CRAM) formats"
LABEL software.website="http://www.htslib.org"
LABEL software.documentation="http://www.htslib.org/doc/samtools.html"
LABEL software.license="MIT/Expat"

USER root

# run update and install necessary utils and upgrade pip
RUN apt-get update -y && apt-get install -y \
	build-essential \
	curl \
	unzip \
	bzip2 \
	zlib1g-dev \
	libncurses5-dev \
	libncursesw5-dev \
	libnss-sss \
	libbz2-dev \
	liblzma-dev \
	libhdf5-dev \
	glpk-utils \
	python-pip \
	libpng-dev \
	libfreetype6-dev \
	libfreetype6 \
	pkg-config \
	coinor-cbc \
	wget \
	gcc \
	g++ \
	make \
	zlib1g-dev \
	unzip \
	git \
	cmake \
	autoconf \
	pigz \
	python3-pip \
	coreutils \
	tcsh \
	gawk

# set woring dir
WORKDIR /usr/local/bin/

# Install samtools
ADD https://github.com/samtools/samtools/releases/download/${VERSION}/samtools-${VERSION}.tar.bz2 /usr/local/bin/

RUN tar -xjf /usr/local/bin/samtools-${VERSION}.tar.bz2 -C /usr/local/bin/ && \
	cd /usr/local/bin/samtools-${VERSION}/ && make && make install

# Clean up
RUN apt-get autoclean -y && apt-get clean -y && \
	rm /usr/local/bin/samtools-${VERSION}.tar.bz2

# Add a user
RUN useradd -ms /bin/bash sonofsam
USER sonofsam

WORKDIR /home/
