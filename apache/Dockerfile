FROM debian:jessie

MAINTAINER François LASSERRE <choiz@me.com>

RUN apt-get update && apt-get -y install apache2
RUN a2enmod proxy_fcgi

ADD 000-default.conf /etc/apache2/sites-available/
RUN a2ensite 000-default

EXPOSE 80

WORKDIR /var/www

CMD /usr/sbin/apache2ctl -D FOREGROUND