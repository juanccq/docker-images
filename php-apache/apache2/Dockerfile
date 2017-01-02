FROM php:5.4-apache

# Install modules
RUN apt-get update \
    && docker-php-ext-install json pdo pdo_mysql mysql mysqli mbstring 
#    opcache

# Install mcrypt extension
RUN apt-get install -y libmcrypt-dev \
    && docker-php-ext-install mcrypt

# Install intl extension
RUN apt-get install -y libicu-dev \
    && docker-php-ext-install intl

# Install gd extension
RUN apt-get install -y libfreetype6-dev libgd-dev libjpeg62-turbo-dev  libpng12-dev \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd

# Install curl extension
RUN apt-get install -y libcurl4-openssl-dev \
    && docker-php-ext-install curl

# Install imagick  extension
RUN apt-get install -y libmagickwand-dev --no-install-recommends && rm -rf /var/lib/apt/lists/* \
    && pecl install imagick \
    && docker-php-ext-enable imagick

# Enable and configure xdebug
#RUN pecl install xdebug
#RUN docker-php-ext-enable xdebug
#RUN echo "xdebug.max_nesting_level = 400" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini; \
#	echo "xdebug.remote_enable = 1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini; \
#	echo "xdebug.remote_connect_back = 1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini; \
#	echo "xdebug.extended_info = 1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini; \
#	echo "xdebug.idekey = 'PHPSTORM'" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini;

RUN echo "[Date]" >> /usr/local/etc/php/conf.d/docker-php-ext-gas.ini; \
        echo "date.timezone = America/La_Paz" >> /usr/local/etc/php/conf.d/docker-php-ext-gas.ini;

# Install zip extension
RUN apt-get update && apt-get install -y zlib1g-dev \
    && docker-php-ext-install zip

RUN a2enmod rewrite