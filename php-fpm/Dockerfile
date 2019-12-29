FROM php:7.3-fpm-alpine

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
    opcache \
    pdo \
    pdo_mysql \
    curl \
    mysqli \
    xml \
    mbstring \
    && docker-php-ext-configure gd \
    --with-gd \
    --with-freetype-dir=/usr/include/ \
    --with-png-dir=/usr/include/ \
    --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && apk del build-dependencies \
    && apk add --no-cache \
    curl \
    libpng \
    freetype \
    libjpeg-turbo \
    libxml2 \
    oniguruma

RUN set -xe \
    && apk --no-cache add libmaxminddb-dev \
    && curl -fsSL 'https://github.com/maxmind/MaxMind-DB-Reader-php/archive/v1.5.1.tar.gz' -o maxmind.tar.gz \
    && mkdir -p /tmp/maxmind \
    && tar -xf maxmind.tar.gz -C /tmp/maxmind --strip-components=1 \
    && rm maxmind.tar.gz \
    && docker-php-ext-configure /tmp/maxmind/ext \
    && docker-php-ext-install /tmp/maxmind/ext  \
    && rm -r /tmp/maxmind \
    && apk del libmaxminddb-dev \
    && apk --no-cache add libmaxminddb

RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"

EXPOSE 9000
