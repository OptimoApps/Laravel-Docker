FROM php:8.0.2-fpm-alpine

MAINTAINER satz<sathish.thi@gmail.com>

RUN apk add --no-cache --virtual .build-deps \
    $PHPIZE_DEPS \
    curl-dev \
    imagemagick-dev \
    libtool \
    libxml2-dev \
    postgresql-dev \
    sqlite-dev \
    oniguruma-dev

# Install production dependencies
RUN apk add --no-cache \
    bash \
    curl \
    g++ \
    gcc \
    git \
    libintl \
    icu \
    icu-dev \
    libwebp-dev \
    libc-dev \
    libpng-dev \
    make \
    mysql-client \
    openssh-client \
    postgresql-libs \
    imagemagick \
    rsync \
    libzip-dev \
    zlib-dev \
    libmcrypt-dev

# Install PECL and PEAR extensions
RUN pecl install \
    redis

# Install and enable php extensions
RUN docker-php-ext-enable \
    redis

RUN docker-php-ext-install \
    intl \
    curl \
    exif \
    iconv \
    # pdo \
    pdo_mysql \
    mbstring \
    pdo_pgsql \
    pdo_sqlite \
    pcntl \
    tokenizer \
    xml \
    gd \
    bcmath \
    zip

# Install composer
ENV PATH ./vendor/bin:/composer/vendor/bin:$PATH
ENV COMPOSER_ALLOW_SUPERUSER 1
RUN curl -s https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin/ --filename=composer

# Cleanup dev dependencies
RUN apk del -f .build-deps

ADD config/* /usr/local/etc/php/conf.d/

WORKDIR /var/www
