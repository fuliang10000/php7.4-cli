FROM php:7.1-fpm

#解压扩展目录
RUN docker-php-source extract
RUN apt-get update
RUN apt-get install -y \
    libfreetype6-dev \
    libtool \
    libjpeg62-turbo-dev \
    libpng-dev \
    libzip-dev \
    libmcrypt-dev \
    openssl \
    libssl-dev \
    bzip2 \
    libbz2-dev \
    libxml2 \
    git
#安装扩展
RUN docker-php-ext-install -j$(nproc) iconv
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/
RUN docker-php-ext-install -j$(nproc) gd
RUN docker-php-ext-install -j$(nproc) bcmath
RUN docker-php-ext-install -j$(nproc) pdo
RUN docker-php-ext-install -j$(nproc) mbstring
RUN docker-php-ext-install -j$(nproc) pdo_mysql
RUN docker-php-ext-install -j$(nproc) opcache
RUN docker-php-ext-install -j$(nproc) mysqli
RUN docker-php-ext-install -j$(nproc) zip
RUN docker-php-ext-install -j$(nproc) pcntl
RUN docker-php-ext-install -j$(nproc) tokenizer
RUN docker-php-ext-install -j$(nproc) sockets
RUN docker-php-ext-install -j$(nproc) bz2
RUN pecl channel-update pecl.php.net
RUN pecl install igbinary-2.0.1 && docker-php-ext-enable igbinary
RUN pecl install mcrypt-1.0.0 && docker-php-ext-enable mcrypt
RUN pecl install redis-5.0.0 && docker-php-ext-enable redis
RUN pecl install mongodb-1.5.1 && docker-php-ext-enable mongodb
RUN pecl install xhprof-2.1.3 && docker-php-ext-enable xhprof
RUN pecl install xdebug-2.9.8 && docker-php-ext-enable xdebug
#删除解压的扩展
RUN rm -rf /tmp/pear
RUN docker-php-source delete

RUN cp /usr/local/etc/php/php.ini-development /usr/local/etc/php/php.ini
RUN php -v

# 安装composer
RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/bin/composer
RUN composer --version
# 设置国内镜像
#RUN composer config -g repo.packagist composer https://packagist.phpcomposer.com
RUN composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/
# 设置环境变量
RUN echo 'export PATH="$PATH:/root/.composer/vendor/bin"' > /etc/profile
RUN export PATH=$PATH:/root/.composer/vendor/bin

WORKDIR /var/www/starlink
