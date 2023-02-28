FROM php:8.1-apache

RUN docker-php-ext-install mysqli

RUN apt-get update \
    && apt-get install -y dos2unix wget git zip unzip

RUN apt-get update && apt-get install -y libpng-dev
RUN apt-get install -y \
    libwebp-dev \
    libjpeg62-turbo-dev \
    libpng-dev libxpm-dev \
    libfreetype6-dev \
    libzip-dev

RUN docker-php-ext-configure gd \
    --with-webp \
    --with-jpeg \
    --with-xpm \
    --with-freetype

RUN docker-php-ext-install gd

RUN apt-get install -y \
    libxml2-dev

RUN docker-php-ext-install simplexml zip

COPY config.php /var/www

COPY php.ini /usr/local/etc/php
RUN a2enmod rewrite

CMD apache2-foreground
