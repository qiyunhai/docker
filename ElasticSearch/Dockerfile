FROM docker.elastic.co/elasticsearch/elasticsearch:8.8.1

MAINTAINER qiyunhai

LABEL maintainer="qiyunhai <156457917@qq.com>"

# 拷贝配置
COPY ./volume/config /usr/share/elasticsearch/config

# 拷贝插件
COPY ./plugin/elasticsearch-analysis-ik-8.8.1.zip /usr/share/elasticsearch/tmp/elasticsearch-analysis-ik-8.8.1.zip

# 切换到root用户获取所有权限
USER root

# 给elasticsearch一个有权限的用户组
RUN groupadd elk \
    && usermod -G elk elasticsearch \
    && chown -R elasticsearch:elk /usr/share/elasticsearch

# 安装IK分词器,需要输入y进行确认安装
#RUN elasticsearch-plugin install file:///usr/share/elasticsearch/tmp/elasticsearch-analysis-ik-8.8.1.zip

# 切换回用户elasticsearch
USER elasticsearch

# 暴露Elasticsearch端口
EXPOSE 9200 9300