FROM php:8.4-fpm-alpine

# System dependencies
RUN apk add --no-cache \
    bash \
    curl \
    git \
    unzip \
    zip \
    icu-dev \
    oniguruma-dev \
    libzip-dev \
    mysql-client \
    nodejs \
    npm \
    supervisor \
    freetype-dev \
    libpng-dev \
    libjpeg-turbo-dev \
    libwebp-dev \
    zlib-dev \
    imagemagick \
    imagemagick-dev \
    linux-headers

# Configure GD
RUN docker-php-ext-configure gd \
    --with-freetype \
    --with-jpeg \
    --with-webp

# Install PHP extensions
RUN docker-php-ext-install -j$(nproc) \
    pdo \
    pdo_mysql \
    mbstring \
    intl \
    zip \
    bcmath \
    pcntl \
    gd \
    opcache \
    exif \
    sockets

# Redis and Imagick extensions
RUN apk add --no-cache --virtual .build-deps $PHPIZE_DEPS \
    && pecl install redis imagick \
    && docker-php-ext-enable redis imagick \
    && apk del .build-deps

# Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

# PHP configuration
# COPY php.ini /usr/local/etc/php/php.ini

# Git safe directory
RUN git config --global --add safe.directory /var/www

WORKDIR /var/www

EXPOSE 9000

CMD ["php-fpm"]