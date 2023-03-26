FROM php:8.1.15-fpm-alpine3.17

RUN apk add --no-cache --virtual .build-deps \
        autoconf \
        g++ \
        make \
        pcre-dev \
        postgresql-dev \
        zlib-dev \
    && git clone --depth=1 -b v5.1.4 "git://github.com/phalcon/cphalcon.git" \
    && cd cphalcon/build \
    && ./install \
    && docker-php-ext-enable phalcon \
    && apk del .build-deps
