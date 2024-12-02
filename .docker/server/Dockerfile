FROM php:8.4.1-apache

RUN apt update -y; \
    apt install zip unzip nano ssh git -y

ENV PORT __SERVER_PORT_INTERNAL__

RUN sed -i 's/Listen 80/Listen __SERVER_PORT_INTERNAL__/' /etc/apache2/ports.conf; \
    sed -i 's/*:80/*:__SERVER_PORT_INTERNAL__/' /etc/apache2/sites-available/000-default.conf

ENV APACHE_DOCUMENT_ROOT /var/www/html/public

RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf; \
    sed -ri -e 's!/var/www/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf

RUN a2enmod rewrite headers deflate

ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

RUN chmod +x /usr/local/bin/install-php-extensions; \
    install-php-extensions gd imagick intl pdo_mysql xdebug zip

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer; \
    composer config --global process-timeout 10000
