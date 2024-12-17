FROM php:8.2-fpm

RUN apt-get update && apt-get install -y \
    git \
    unzip \
    libpq-dev \
    libzip-dev \
    zlib1g-dev \
    && docker-php-ext-install pdo pdo_pgsql zip

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/app

COPY ./../../app .

RUN composer install --no-dev --optimize-autoloader

RUN chown -R www-data:www-data /var/www/app

EXPOSE 9000

CMD ["php-fpm"]