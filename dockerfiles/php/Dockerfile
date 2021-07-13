FROM php:7.4-fpm

ENV REDIS_VERSION 3.1.3
ENV MEMCACHE_VERSION 3.1.5

RUN sed -i "s@http://deb.debian.org@http://mirrors.aliyun.com@g" /etc/apt/sources.list
RUN cat /etc/apt/sources.list
RUN apt-get update

RUN mkdir -p /usr/src/php/ext/redis \
    && docker-php-ext-install pdo \
    && docker-php-ext-install pdo_mysql \
    && apt-get install -y libmemcached-dev \
    && apt-get install -y libpng-dev \
    && apt-get install -y zlib1g-dev \
    && apt-get install -y libzip-dev \
    # && pecl install memcached-${MEMCACHE_VERSION} \
    && docker-php-ext-configure zip  \
    && docker-php-ext-install zip \
    && docker-php-ext-install bcmath \ 
    && docker-php-ext-install gd \ 
    && docker-php-ext-install mysqli \
    && curl -L https://github.com/phpredis/phpredis/archive/${REDIS_VERSION}.tar.gz | tar xvz -C /usr/src/php/ext/redis --strip 1 \
    && echo 'redis' >> /usr/src/php-available-exts \
    && docker-php-ext-install redis 


EXPOSE 9001

WORKDIR /home/data
