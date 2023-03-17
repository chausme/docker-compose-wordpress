# PHP 7.4

FROM php:7.4-apache AS php7.4

RUN docker-php-ext-install mysqli

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

COPY ./php.ini /usr/local/etc/php

RUN a2enmod rewrite

CMD ["apache2-foreground"]

# PHP 8.0

FROM php:8.0-apache AS php8.0

RUN docker-php-ext-install mysqli

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

COPY ./php.ini /usr/local/etc/php
COPY ./000-default.conf /etc/apache2/sites-available/
COPY ./other-vhosts-access-log.conf /etc/apache2/conf-available/

RUN a2enmod rewrite

CMD ["apache2-foreground"]

# PHP 8.1

FROM php:8.1-apache AS php8.1

RUN docker-php-ext-install mysqli

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

COPY ./php.ini /usr/local/etc/php
COPY ./000-default.conf /etc/apache2/sites-available/
COPY ./other-vhosts-access-log.conf /etc/apache2/conf-available/

RUN a2enmod rewrite

CMD ["apache2-foreground"]

# PHP 8.2

FROM php:8.2-apache AS php8.2

RUN docker-php-ext-install mysqli

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

COPY ./php.ini /usr/local/etc/php

RUN a2enmod rewrite

CMD ["apache2-foreground"]

