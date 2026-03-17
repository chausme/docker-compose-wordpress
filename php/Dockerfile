ARG PHP_VERSION=8.3
FROM php:${PHP_VERSION}-apache

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

RUN set -eux; \
    apt-get update; \
    apt-get install -y --no-install-recommends \
        libjpeg62-turbo-dev \
        libpng-dev \
        libwebp-dev \
        libxpm-dev \
        libfreetype6-dev \
        libzip-dev; \
    rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-configure gd \
    --with-freetype \
    --with-jpeg \
    --with-webp \
    --with-xpm

RUN docker-php-ext-install -j"$(nproc)" mysqli gd zip

RUN a2enmod rewrite

COPY ./php.ini /usr/local/etc/php/php.ini
COPY ./000-default.conf /etc/apache2/sites-available/000-default.conf
COPY ./other-vhosts-access-log.conf /etc/apache2/conf-available/other-vhosts-access-log.conf

CMD ["apache2-foreground"]