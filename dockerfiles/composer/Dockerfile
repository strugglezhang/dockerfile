FROM composer:1.10.17


RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories
RUN cp /usr/local/etc/php/php.ini-development /usr/local/etc/php/php-cli.ini
RUN pear config-set php_ini /usr/local/etc/php/php-cli.ini


RUN apk add make \
    && apk add gcc musl-dev g++ zlib-dev \
    && apk add libmemcached-dev \
    && apk add autoconf \
    && pecl install memcached \
    && pecl install redis \
    && docker-php-ext-install pdo \
    && docker-php-ext-install sockets \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install bcmath \
    && docker-php-ext-install mysqli \
    && pecl install swoole \
    && apk add --no-cache rabbitmq-c \
    && apk add --no-cache rabbitmq-c-dev \
    && pecl install amqp \
    && apk del autoconf \
    && apk del autoconf make\
    && apk del autoconf gcc

WORKDIR /app