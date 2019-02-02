FROM php:7.0-apache

RUN apt-get update && \
    apt-get install -y \
        zlib1g-dev libpng-dev
RUN docker-php-ext-install pdo pdo_mysql mysqli zip gd
RUN apt update
RUN apt install -y apache2-utils
RUN a2enmod rewrite