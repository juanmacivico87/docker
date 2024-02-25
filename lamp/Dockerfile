FROM php:8.1-apache

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get install -y \
    libxml2-dev \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libzip-dev \
    libicu-dev \
    libxslt1-dev \
    libssl-dev \
    libcurl4-openssl-dev \
    libonig-dev \
    wget \
    unzip

RUN docker-php-ext-configure gd --with-freetype --with-jpeg
RUN docker-php-ext-install -j$(nproc) gd mysqli opcache soap zip intl xsl pdo pdo_mysql

RUN pecl install -o -f xdebug
RUN pecl install channel://pecl.php.net/xmlrpc-1.0.0RC3  xmlrpc

RUN docker-php-ext-enable xdebug
RUN docker-php-ext-enable xmlrpc

RUN apt-get clean && rm -rf /var/lib/apt/lists/*

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

COPY ./app/ /var/www/html/
COPY ./resources/apache/apache2.conf /etc/apache2/apache2.conf
COPY ./resources/apache/vhost.conf /etc/apache2/sites-available/vhost.conf
COPY ./resources/apache/php-xdebug.ini /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

RUN a2enmod rewrite