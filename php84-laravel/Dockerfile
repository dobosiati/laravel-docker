FROM php:8.4-fpm-alpine

# System dependencies
RUN apk add --no-cache \
    bash \
    curl \
    git \
    unzip \
    zip \
    shadow \
    icu-dev \
    oniguruma-dev \
    libzip-dev \
    mysql-client \
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

# Node
COPY --from=node:20-alpine /usr/local /usr/local

# PHP configuration
# COPY php.ini /usr/local/etc/php/php.ini

# Git safe directory
RUN git config --global --add safe.directory /var/www

# Install pnpm
RUN npm install -g pnpm

# For permission issues
ARG UID=1000
ARG GID=1000
RUN deluser www-data || true && \
    addgroup -g ${GID} www-data && \
    adduser -D -u ${UID} -G www-data www-data

WORKDIR /var/www

EXPOSE 9000

CMD ["php-fpm"]