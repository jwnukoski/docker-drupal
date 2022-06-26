# Required
FROM php:8.1.6RC1-fpm-alpine3.14
RUN apk add zlib-dev libpng-dev libjpeg-turbo-dev
RUN docker-php-ext-configure gd --with-jpeg=/usr/include/ && docker-php-ext-install gd
RUN docker-php-ext-install pdo pdo_mysql opcache

# Composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"
RUN mv composer.phar /usr/local/bin/composer

# Drush
RUN apk add git
RUN git clone https://github.com/drush-ops/drush.git /usr/local/src/drush
RUN composer i --working-dir=/usr/local/src/drush
RUN ln -s /usr/local/src/drush/drush /usr/bin/drush