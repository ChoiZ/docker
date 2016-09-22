FROM debian:jessie

MAINTAINER François LASSERRE <choiz@me.com>

RUN apt-get update && apt-get -y install openjdk-7-jre \
        openjdk-7-jdk \
        wget

RUN wget -q -O - https://jenkins-ci.org/debian/jenkins-ci.org.key | apt-key add -

RUN echo 'deb http://pkg.jenkins-ci.org/debian binary/' > /etc/apt/sources.list.d/jenkins.list

RUN apt-get update && apt-get -y install jenkins \
        git

EXPOSE 8080

CMD service jenkins start -F