FROM php:7.4-fpm

RUN apt-get update && apt-get install -y wget curl git unzip libjudydebian1 libjudy-dev \
    && pecl install xdebug-2.8.1 \
    && docker-php-ext-enable xdebug \ 
    && docker-php-ext-install pcntl \
    && pecl install memprof \
    && docker-php-ext-enable memprof

ENV PHP_INI_DIR /usr/local/etc/php/

#php-meminfo 
RUN curl -L -o /tmp/php74_support.tar.gz https://github.com/vudaltsov/php-meminfo/archive/php74_support.tar.gz \
    && tar zxpf /tmp/php74_support.tar.gz -C /tmp \
    && rm -r /tmp/php74_support.tar.gz \
    && cd /tmp/php-meminfo-php74_support/extension/php7/ && phpize && ./configure --enable-meminfo && make && make install \
    && rm -rf /tmp/* \
    && printf "extension=meminfo.so\n" > $PHP_INI_DIR/conf.d/meminfo.ini	

ADD ./php.ini /usr/local/etc/php/php.ini

RUN wget https://getcomposer.org/installer -O - -q \
    | php -- --install-dir=/bin --filename=composer --quiet

WORKDIR /var/www/symfony

