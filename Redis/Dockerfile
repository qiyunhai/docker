FROM redis:7.0.11-alpine

MAINTAINER qiyunhai

LABEL maintainer="qiyunhai <156457917@qq.com>"

RUN sed -i 's/dl-cdn.alpinelinux.org/dl-cdn.alpinelinux.org/g' /etc/apk/repositories && \
    apk update \
    # 更改时区
    && apk add -U tzdata && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    # 创建存放配置文件夹
    && mkdir /home/redis/conf \
    && cd /home/redis/conf \
    # 下载源码包
    && wget https://download.redis.io/redis-stable.tar.gz \
    # 获取配置文件
    && tar -zxvf redis-stable.tar.gz \
    && cp redis-stable/redis.conf /home/redis/conf/ \
    && rm -rf redis-stable*
