FROM arm64v8/php:8.2-fpm-alpine

# Install dependencies for aarch64 architecture
RUN apk add --no-cache \
    libpng-dev libjpeg-turbo-dev libfreetype-dev autoconf make g++ \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install gd pdo pdo_mysql mbstring intl zip opcache

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --disable-tls && \
    mv composer.phar /usr/local/bin/composer

# Install APCu extension
RUN pecl install apcu && docker-php-ext-enable apcu

# Set working directory
WORKDIR /var/www
