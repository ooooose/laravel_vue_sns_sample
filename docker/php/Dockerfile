FROM php:7.4.1-fpm

# COPY php.ini
COPY ./docker/php/php.ini /usr/local/etc/php/php.ini

# Composer install
COPY --from=composer:2.0 /usr/bin/composer /usr/bin/composer

# install Node.js
COPY --from=node:15.14 /usr/local/bin /usr/local/bin
COPY --from=node:15.14 /usr/local/lib /usr/local/lib

RUN apt-get update && \
    apt-get -y install \
    git unzip libzip-dev libicu-dev libonig-dev vim && \
    docker-php-ext-install intl pdo_mysql zip bcmath

WORKDIR /var/www/html
