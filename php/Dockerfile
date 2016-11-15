FROM debian:jessie

MAINTAINER François LASSERRE <choiz@me.com>

RUN apt-get update \
    && echo "deb http://packages.dotdeb.org jessie all\n\
deb-src http://packages.dotdeb.org jessie all" >> /etc/apt/sources.list \
    && curl -L https://www.dotdeb.org/dotdeb.gpg -o dotdeb.gpg && apt-key add dotdeb.gpg \
    && apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y php7.0-curl \
        php7.0-intl \
        php7.0-fpm \
        php7.0-mcrypt \
        php7.0-mysql \
        php7.0-xdebug \
        iproute2

COPY config/etc/php/7.0/fpm/php-fpm.conf /etc/php/7.0/fpm/php-fpm.conf
COPY config/etc/php/7.0/fpm/pool.d/www.conf /etc/php/7.0/fpm/pool.d/www.conf
COPY config/etc/php/7.0/mods-available/php-custom.ini /etc/php/7.0/mods-available/php-custom.ini

RUN ln -s /etc/php/7.0/mods-available/php-custom.ini /etc/php/7.0/fpm/conf.d/php-custom.ini \
    && ln -s /etc/php/7.0/mods-available/php-custom.ini /etc/php/7.0/cli/conf.d/php-custom.ini

WORKDIR /var/www

EXPOSE 9000

RUN service php7.0-fpm start

CMD php-fpm7.0 -F
