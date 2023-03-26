FROM php:8.1.15-fpm-alpine3.17

RUN apk update \
  && apk add --no-cache bash build-base curl gcc git nano nginx openssh libpq-dev musl-dev

RUN docker-php-ext-install pdo pdo_pgsql

## Composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php -r "if (hash_file('sha384', 'composer-setup.php') === '55ce33d7678c5a611085589f1f3ddf8b3c52d662cd01d4ba75c0ee0459970c2200a51f492d557530c71c15d8dba01eae') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"
RUN mv composer.phar /usr/local/bin/composer

## Phalcon
RUN wget https://codeload.github.com/phalcon/cphalcon/tar.gz/v5.1.4
RUN tar -xzf v5.1.4
RUN cd cphalcon-5.1.4/build
RUN ls -a
RUN ./install
RUN echo "extension=phalcon.so" >> /etc/php8/conf.d/30-phalcon.ini
