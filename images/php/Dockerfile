FROM php:7.2-fpm

ARG DEBIAN_FRONTEND=noninteractive
ARG LC_ALL=C.UTF-8

RUN apt-get update

RUN apt-get install -y libmcrypt-dev

RUN pecl install mcrypt-1.0.1 && docker-php-ext-enable mcrypt
RUN docker-php-ext-install mbstring tokenizer mysqli pdo_mysql

RUN apt-get install -y zlib1g-dev
RUN apt-get install -y libz-dev libmemcached-dev

RUN curl -L -o /tmp/memcached.tar.gz "https://github.com/php-memcached-dev/php-memcached/archive/v3.0.4.tar.gz" \
    && mkdir -p /usr/src/php/ext/memcached \
    && tar -C /usr/src/php/ext/memcached -zxvf /tmp/memcached.tar.gz --strip 1 \
    && docker-php-ext-configure memcached \
    && docker-php-ext-install memcached \
    && rm /tmp/memcached.tar.gz
