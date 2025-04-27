FROM php:8.2-fpm

RUN apt-get update && apt-get install -y \
    libzip-dev unzip \
    && docker-php-ext-install pdo pdo_mysql zip

# Install Node.js
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - \
    && apt-get install -y nodejs


COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

WORKDIR /var/www

COPY ./app /var/www

RUN chown -R www-data:www-data /var/www

EXPOSE 9000
