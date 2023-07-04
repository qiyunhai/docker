FROM php:5.6-fpm-alpine

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
    # php.ini
    && cp "/usr/local/etc/php/php.ini-production" "/usr/local/etc/php/php.ini"
