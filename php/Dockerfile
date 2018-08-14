FROM php:7.2-fpm

RUN apt-get update \
  && apt-get install -y --no-install-recommends \
    curl \
    libmemcached-dev \
    libz-dev \
    libpq-dev \
    libjpeg-dev \
#    libpng12-dev \
    libfreetype6-dev \
    libssl-dev \
    libmcrypt-dev

#RUN docker-php-ext-install mcrypt \
  # Install the PHP pdo_mysql extention
RUN docker-php-ext-install pdo_mysql \
  # Install the PHP pdo_pgsql extention
  && docker-php-ext-install pdo_pgsql \
  # Install the PHP gd library
  && docker-php-ext-configure gd \
    --enable-gd-native-ttf \
    --with-jpeg-dir=/usr/lib \
    --with-freetype-dir=/usr/include/freetype2 && \
    docker-php-ext-install gd && \
    pecl install xdebug && \
    docker-php-ext-enable xdebug

RUN echo "xdebug.remote_enable=1" >> /usr/local/etc/php/php.ini

COPY ./ini/error.ini /usr/local/etc/php/conf.d/error.ini
COPY ./ini/core.ini /usr/local/etc/php/conf.d/core.ini
COPY ./ini/date.ini /usr/local/etc/php/conf.d/date.ini

EXPOSE 9000
