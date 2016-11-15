FROM debian:jessie

MAINTAINER François LASSERRE <choiz@me.com>

ENV DEBIAN_FRONTEND noninteractive

# Update distrib and setup apt-utils & curl
RUN apt-get update -y && apt-get install -y apt-utils curl

# Add dotdeb
RUN curl https://www.dotdeb.org/dotdeb.gpg -Lso dotdeb.gpg && apt-key add dotdeb.gpg \
    && echo deb http://packages.dotdeb.org jessie all >> /etc/apt/sources.list \
    && echo deb-src http://packages.dotdeb.org jessie all >> /etc/apt/sources.list

# Add timezone
RUN echo "Europe/Paris" > /etc/timezone \
    && dpkg-reconfigure -f noninteractive tzdata

# Update apt repositories
RUN apt-get update -y \
    && apt-get upgrade -y
