FROM python:alpine3.11

ARG SOFTWARE="samtools"
ARG VERSION=1.9
LABEL container.base.image="python:alpine3.11"
LABEL software.name=${SOFTWARE}
LABEL software.version=${VERSION}
LABEL software.description="Utilities for the Sequence Alignment/Map (SAM/BAM/CRAM) formats"
LABEL software.website="http://www.htslib.org"
LABEL software.documentation="http://www.htslib.org/doc/samtools.html"
LABEL software.license="MIT/Expat"
LABEL tags="index, faidx, mpileup"

USER root

# update registries and install necessary utils
RUN apk update && apk upgrade \
	&& apk add unzip \
	gcc \
	make \
	ncurses-dev \
	libc-dev \
	zlib-dev \
	bzip2-dev \
	xz-dev \
	curl-dev
# RUN pip install boto3 awscli

# install samtools
RUN wget -O /samtools-${VERSION}.tar.bz2 \
  https://github.com/samtools/samtools/releases/download/${VERSION}/samtools-${VERSION}.tar.bz2 && \
  tar xvjf /samtools-${VERSION}.tar.bz2

RUN cd /samtools-${VERSION} && make && make install

# Clean up
RUN apk del && \
	rm /samtools-${VERSION}.tar.bz2

# Create a group and user
RUN addgroup -S samtools && adduser -S sonofsam -G samtools

# Tell docker that all future commands should run as the appuser user
USER sonofsam

