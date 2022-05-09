FROM php:8.1.6RC1-fpm-alpine3.14
RUN apk add zlib-dev libpng-dev libjpeg-turbo-dev
RUN docker-php-ext-configure gd --with-jpeg=/usr/include/ && docker-php-ext-install gd
RUN docker-php-ext-install pdo pdo_mysql