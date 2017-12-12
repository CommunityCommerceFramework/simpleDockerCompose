FROM php:7.0-fpm

RUN apt-get update && apt-get install -y --no-install-recommends vim mysql-client libtidy-dev librecode-dev libpspell-dev libreadline-gplv2-dev libedit-dev libedit2 libcurl4-openssl-dev libmagickwand-dev libmagickcore-dev libxml2-dev libicu-dev libfreetype6-dev libjpeg62-turbo-dev libmcrypt-dev libpng12-dev && \
    docker-php-ext-install -j$(nproc) exif mbstring bcmath json pspell readline recode xmlrpc tidy curl iconv mcrypt opcache calendar hash pdo pdo_mysql xml simplexml intl soap zip sockets && \
    docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && \
    docker-php-ext-install -j$(nproc) gd && \
    pecl install xdebug-2.5.5 && \
    pecl install imagick-3.4.3 && \
    pecl install redis-3.1.2 && \
    pecl install igbinary-2.0.4 && \
    docker-php-ext-enable imagick redis igbinary && \
    apt-get clean && apt-get --yes --quiet autoremove --purge && \
    rm -rf  /var/lib/apt/lists/* /tmp/* /var/tmp/* \
            /usr/share/doc/* /usr/share/groff/* /usr/share/info/* /usr/share/linda/* \
            /usr/share/lintian/* /usr/share/locale/* /usr/share/man/*

# install ioncube loader
#RUN cd /tmp \
#	&& curl -o ioncube.tar.gz http://downloads3.ioncube.com/loader_downloads/ioncube_loaders_lin_x86-64.tar.gz \
#    && tar -xvvzf ioncube.tar.gz \
#    && mv ioncube/ioncube_loader_lin_7.0.so /usr/local/lib/php/extensions/* \
#    && rm -Rf ioncube.tar.gz ioncube

# enable iocube loader
#RUN echo "zend_extension=/usr/local/lib/php/extensions/no-debug-non-zts-20151012/ioncube_loader_lin_7.0.so" > /usr/local/etc/php/conf.d/00_docker-php-ext-ioncube_loader_lin_7.0.ini

COPY "config/*.ini" "$PHP_INI_DIR/conf.d/"

WORKDIR /var/www
