FROM php:7.3-fpm-alpine

WORKDIR /var/www

RUN apk update && apk add \
    build-base \
    freetype-dev \
    zip \
    jpegoptim optipng pngquant gifsicle \
    vim \
    unzip \
    git \
    curl \
    libzip-dev \
    libpng-dev \
    libjpeg-turbo-dev \
    freetype-dev && \ 
    docker-php-ext-install zip pdo_mysql mbstring exif pcntl && \
    docker-php-ext-configure gd --with-gd --with-freetype-dir=/usr/include/ \
    --with-jpeg-dir=/usr/include/ \
    --with-png-dir=/usr/include/ && \
    docker-php-ext-install gd

COPY ./config/php/local.ini /usr/local/etc/php/conf.d/local.ini

RUN addgroup -g 1000 -S www && \
    adduser -u 1000 -S www -G www

USER www

COPY --chown=www:www . /var/www/

EXPOSE 9000