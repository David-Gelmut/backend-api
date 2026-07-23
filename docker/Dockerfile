FROM php:8.3-fpm-alpine

# Установка системных зависимостей и инструментов сборки
RUN apk add --no-cache \
    bash \
    curl \
    libpng-dev \
    libxml2-dev \
    zip \
    unzip \
    git \
    linux-headers

# Установка PHP расширений (включая pdo_mysql, bcmath и sockets для RabbitMQ)
RUN docker-php-ext-install pdo_mysql bcmath gd sockets

# Установка Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

WORKDIR /var/www

# Настройка прав для Laravel (оптимизировано под Docker)
RUN chown -R www-data:www-data /var/www

USER www-data

EXPOSE 9001
CMD ["php-fpm"]
