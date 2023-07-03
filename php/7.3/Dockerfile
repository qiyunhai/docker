FROM php:7.3-fpm-alpine

MAINTAINER qiyunhai

LABEL maintainer="qiyunhai <156457917@qq.com>"

RUN sed -i 's/dl-cdn.alpinelinux.org/dl-cdn.alpinelinux.org/g' /etc/apk/repositories && \
    apk update && apk add --no-cache \
        gcc g++ make libffi-dev openssl-dev libzip-dev zip unzip composer \
        freetype freetype-dev libpng libpng-dev libjpeg-turbo libjpeg-turbo-dev \
    # 更改时区
    && apk add -U tzdata && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    # 清除apk缓存
    && rm -rf /var/cache/apk/* \
    # 创建扩展目录
    && mkdir -p /usr/src/php/ext/ \
    # 进入软件保存目录
    && cd /usr/local \
    # 下载redis扩展
    && wget https://pecl.php.net/get/redis-5.3.7.tgz \
    && tar -zxvf redis-5.3.7.tgz \
    && mv redis-5.3.7 /usr/src/php/ext/redis \
    && rm -rf /usr/local/redis-5.3.7.tgz \
    # 下载swoole扩展
    && wget https://pecl.php.net/get/swoole-4.8.13.tgz \
    && tar -zxvf swoole-4.8.13.tgz \
    && mv swoole-4.8.13 /usr/src/php/ext/swoole \
    && rm -rf /usr/local/swoole-4.8.13.tgz \
    # 配置gd
    && docker-php-ext-configure gd \
        --with-freetype-dir=/usr/include/ \
        --with-jpeg-dir=/usr/include/ \
    # 安装扩展
    && docker-php-ext-install \
        gd \
        pdo_mysql \
        mysqli \
        sockets \
        zip \
        exif \
        bcmath \
        pcntl \
        opcache \
        redis \
        swoole \
    # php.ini
    && cp "/usr/local/etc/php/php.ini-production" "/usr/local/etc/php/php.ini"
