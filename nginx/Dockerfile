FROM nginx:1.18.0-alpine

MAINTAINER qiyunhai

LABEL maintainer="qiyunhai <156457917@qq.com>"

RUN sed -i 's/dl-cdn.alpinelinux.org/dl-cdn.alpinelinux.org/g' /etc/apk/repositories && \
    apk update \
    # 更改时区
    && apk add -U tzdata && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
