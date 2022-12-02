FROM php:7.4.33-apache

# Install PHP extensions
RUN apt-get update && apt-get install -y \
    openssl \
    zip \
    unzip \
    git \
    libicu-dev \
    libpq-dev \
    libmcrypt-dev \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng-dev \
    libxrender1 \
    libxext6 \
    libfontconfig \
    libfontconfig1 \
    libx11-dev \
    libjpeg62 \
    libxtst6 \
    libonig-dev \
    libzip-dev \
    wget \
    build-essential \
    libssl-dev \
    libxrender-dev \
    gdebi \
    unzip \
    nano \
    mariadb-client \
    && rm -r /var/lib/apt/lists/* \
    && docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd \
    && docker-php-ext-install \
    intl \
    mbstring \
    pcntl \
    pdo_mysql \
    pdo_pgsql \
    pgsql \
    zip \
    opcache \
    gd

# Install Xdebug
# RUN curl -fsSL 'https://xdebug.org/files/xdebug-2.4.0.tgz' -o xdebug.tar.gz \
#     && mkdir -p xdebug \
#     && tar -xf xdebug.tar.gz -C xdebug --strip-components=1 \
#     && rm xdebug.tar.gz \
#     && ( \
#     cd xdebug \
#     && phpize \
#     && ./configure --enable-xdebug \
#     && make -j$(nproc) \
#     && make install \
#     ) \
#     && rm -r xdebug \
#     && docker-php-ext-enable xdebug

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer

# Put apache config for Laravel
COPY apache2-laravel.conf /etc/apache2/sites-available/laravel.conf
RUN a2dissite 000-default.conf && a2ensite laravel.conf && a2enmod rewrite

# Change uid and gid of apache to docker user uid/gid
RUN usermod -u 1000 www-data && groupmod -g 1000 www-data

WORKDIR /var/www/html
