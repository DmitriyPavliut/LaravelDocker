FROM php:8.3-fpm AS php-base

WORKDIR /var/www/logistic

RUN apt-get update \
  && apt-get install -y build-essential zlib1g-dev default-mysql-client curl gnupg procps vim git unzip libzip-dev libpq-dev \
  && docker-php-ext-install zip pdo pdo_mysql pdo_pgsql pgsql


RUN pecl install xdebug-3.3.0 && docker-php-ext-enable xdebug

COPY docker/php/conf.d/* $PHP_INI_DIR/conf.d

RUN curl -fsSL https://deb.nodesource.com/setup_22.x | bash - \
    && apt-get install -y nodejs
RUN npm install npm@latest -g
RUN npm install yarn -g

CMD ["php-fpm"]

FROM composer:latest AS composer
WORKDIR /var/www/logistic
ENTRYPOINT ["composer", "--ignore-platform-reqs"]

FROM php-base

WORKDIR /var/www/logistic

COPY --from=composer /usr/bin/composer /usr/bin/composer
