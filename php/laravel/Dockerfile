FROM php:8.3.6-fpm-alpine

RUN docker-php-ext-install pdo pdo_mysql mysqli && \
    docker-php-ext-enable pdo pdo_mysql mysqli && \
    php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer && \
    apk update && \
    apk upgrade && \
    apk add bash

WORKDIR /app

COPY composer.json composer.lock /app/

RUN composer install

COPY . /app

USER www-data

EXPOSE 8000

CMD ["php", "artisan", "serve", "--host=0.0.0.0", "--port=8000"]