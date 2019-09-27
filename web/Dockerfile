FROM php:7.1.20-apache

COPY ./sources.list.stretch /etc/apt/sources.list


RUN apt-get update \
	&& apt-get install -y libxml2-dev libzip-dev libgmp-dev \
    && chown -R www-data:www-data /var/www/html \
    && docker-php-ext-install zip soap pdo_mysql mysqli gmp mbstring


# mysqldump
RUN apt-get install -y mysql-client


# supervisor
RUN apt-get install -y supervisor

RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
RUN sed -ri -e 's!/var/www/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf
