FROM php:7.2.6-fpm

LABEL maintainer="Adam Brown"

COPY . /srv/app/
COPY .docker/php/php.ini /usr/local/etc/php/php.ini
COPY .docker/php/opcache.ini /usr/local/etc/php/conf.d/opcache.ini
COPY .docker/php/xdebug-dev.ini /usr/local/etc/php/conf.d/xdebug-dev.ini

RUN docker-php-ext-install pdo_mysql opcache \
    && pecl install xdebug-2.6.0 \
    && docker-php-ext-enable xdebug \
    && apt-get update && apt-get install nano

# @todo: HACK to avoid Xdebug in Prod - see _sitefiles/TODO.md, use Custom CMD to check ENV
RUN cp -R /usr/local/etc/php/conf.d \
    /usr/local/etc/php/conf.d-dev \
    && rm -f /usr/local/etc/php/conf.d/*-dev.ini \
    && rm -f /usr/local/etc/php/conf.d/*xdebug.ini

WORKDIR /srv/app/

RUN chown -R www-data:www-data /srv/app
