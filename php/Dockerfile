FROM php:7.0-fpm

RUN apt-get update && apt-get install -y git \
	libmemcached-dev \
	libmemcached11 \
	wget \
    	libmemcached-dev \
    	libfreetype6-dev \
    	libjpeg62-turbo-dev \
    	libmcrypt-dev \
    	libpng12-dev \
    	imagemagick \
	&& docker-php-ext-install pdo \
	&& docker-php-ext-install mbstring \
	&& docker-php-ext-install pdo_mysql \
	&& docker-php-ext-install mysqli \
	&& docker-php-ext-install opcache \
	&& docker-php-ext-install gd

RUN git clone https://github.com/websupport-sk/pecl-memcache.git \
	&& cd pecl-memcache \
	&& git checkout -b php7 origin/php7 \
	&& phpize \
	&& ./configure \
	&& make \
	&& make install \
	&& docker-php-ext-enable memcache

COPY ./conf/php.ini /usr/local/etc/php/
COPY ./conf/www.conf /usr/local/etc/php-fpm.d/www.conf

# Fix fucking permissions
RUN usermod -u 1000 www-data && usermod -g staff www-data
CMD ["php-fpm"]
