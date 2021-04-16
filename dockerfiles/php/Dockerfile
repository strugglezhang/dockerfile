FROM php:7.4-fpm

ENV REDIS_VERSION 3.1.3
ENV MEMCACHE_VERSION 3.1.5

RUN mkdir -p /usr/src/php/ext/redis \
    && curl -L https://github.com/phpredis/phpredis/archive/${REDIS_VERSION}.tar.gz | tar xvz -C /usr/src/php/ext/redis --strip 1 \
    && echo 'redis' >> /usr/src/php-available-exts \
    && docker-php-ext-install redis \
    && docker-php-ext-install pdo \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install bcmath \
    && apt-get update \
    && apt-get install -y libmemcached-dev zlib1g-dev \
    && pecl install memcached-${MEMCACHE_VERSION} \
    && docker-php-ext-enable memcached

EXPOSE 9001

WORKDIR /home/data
