FROM php:7.4-fpm

COPY ./docker/php/php.ini /usr/local/etc/php/php.ini

RUN apt-get update \
  && apt-get install -y libzip-dev zlib1g-dev libicu-dev libonig-dev unzip locales \
  && docker-php-ext-install zip pdo_mysql

#Composer install
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1

ENV COMPOSER_HOME /composer

ENV PATH $PATH:/composer/vendor/bin

WORKDIR /app

