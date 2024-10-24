FROM php:8.2-fpm-alpine

# Install required dependencies
RUN apk add --no-cache \
    libpng-dev libjpeg-turbo-dev libfreetype-dev \
    && docker-php-ext-install pdo pdo_mysql mbstring gd intl zip opcache

# Set locales (optional)
RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen && \
    echo "fr_FR.UTF-8 UTF-8" >> /etc/locale.gen && \
    locale-gen

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --disable-tls && \
   mv composer.phar /usr/local/bin/composer

# Install additional PHP extensions
RUN pecl install apcu && docker-php-ext-enable apcu

# Set working directory
WORKDIR /var/www
