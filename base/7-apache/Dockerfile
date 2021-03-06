# Acquia Lightning Docker Container
FROM php:7-apache
MAINTAINER John Kennedy <john.kennedy@acquia.com>

RUN a2enmod rewrite

# Memory Limit
RUN echo "memory_limit=256M" > $PHP_INI_DIR/conf.d/memory-limit.ini

# Time Zone
RUN echo "date.timezone=America/New_York" > $PHP_INI_DIR/conf.d/date_timezone.ini

# Packages
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y \
  libfreetype6-dev \
  libjpeg62-turbo-dev \
  libmcrypt-dev \
  libpng12-dev \
  libbz2-dev \
  php-pear \
  curl \
  git \
  unzip \
  && docker-php-ext-install mcrypt zip bz2 bcmath pdo_mysql mysqli mbstring opcache \
  && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
  && docker-php-ext-install gd

# Environmental Variables
ENV COMPOSER_HOME /root/composer

# Add global binary directory to path
ENV PATH $COMPOSER_HOME/vendor/bin:$PATH

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
  composer config -g github-oauth.github.com b920a503e5bb62ee4f4bcfeb1dfc76bad0706a2c
