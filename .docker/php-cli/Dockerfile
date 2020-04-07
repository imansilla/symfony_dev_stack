FROM php:7.3.15-cli-alpine

LABEL maintainer="ivan@mansillahub.ar"

ARG project_name

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

RUN apk add --update --no-cache \
    shadow \
    icu-dev \
    libzip-dev \
    git

RUN docker-php-ext-install -j$(nproc) \
    pdo_mysql \
    intl \ 
    zip

RUN rm -rf /var/cache/apk/* && rm -rf /tmp/*

RUN usermod -u 1000 www-data

WORKDIR /var/www/html/$project_name