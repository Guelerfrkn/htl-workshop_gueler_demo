FROM php:8.4-apache

RUN a2enmod rewrite

# Install PHP Extension Postgresql
RUN apt-get update && apt-get install -y libpq-dev \
&& docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
&& docker-php-ext-install pdo pdo_pgsql pgsql

# Configure PHP to log errors to stderr
RUN { \
    echo "log_errors = On"; \
    echo "display_errors = Off"; \
    echo "error_log = /proc/self/fd/2"; \
} > /usr/local/etc/php/conf.d/docker-logging.ini

WORKDIR /var/www/html

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

COPY ./docker/development/apache/default.conf /etc/apache2/sites-available/000-default.conf

EXPOSE 80
