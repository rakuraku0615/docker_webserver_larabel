FROM php:7.4.15-fpm-buster

LABEL maintainer="Masayoshi Yoshino"

SHELL ["/bin/bash", "-oeux", "pipefail", "-c"]

ENV COMPOSER_ALLOW_SUPERUSER=1 \
  COMPOSER_HOME=/composer

# timezone
ARG TZ=Asia/Tokyo

COPY --from=composer:1.10 /usr/bin/composer /usr/bin/composer
COPY ./php.ini /usr/local/etc/php/php.ini

RUN apt-get update && \
  apt-get -y install git unzip libzip-dev libicu-dev libonig-dev && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/* && \
  echo ${TZ} > /etc/timezone && \
  pecl install xdebug && \
  cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime && \
  git clone https://github.com/phpredis/phpredis.git /usr/src/php/ext/redis && \
  docker-php-ext-install intl pdo_mysql mbstring zip bcmath redis && \
  docker-php-ext-enable xdebug

WORKDIR /work
