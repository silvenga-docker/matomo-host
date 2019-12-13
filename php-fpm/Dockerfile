FROM php:7-fpm-alpine

RUN set -xe \
    && apk upgrade --no-cache \
    && apk add --no-cache --virtual build-dependencies \
    curl-dev \
    libpng-dev \
    freetype-dev \
    libjpeg-turbo-dev \
    libxml2-dev \
    oniguruma-dev \
    && docker-php-ext-install -j$(nproc) \
    pdo \
    pdo_mysql \
    curl \
    gd \
    mysqli \
    xml \
    mbstring \
    && apk del build-dependencies \
    && apk add --no-cache \
    curl \
    libpng \
    freetype \
    libjpeg-turbo \
    libxml2 \
    oniguruma

EXPOSE 9000
