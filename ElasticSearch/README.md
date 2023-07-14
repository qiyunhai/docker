### ElasticSearch v8.8.1
> 本来想写基于alpine来着，奈何版本太旧，所以本次使用的最新版``2023/07/04``

#### 注意
- ik分词器需要进入到容器内安装，安装完成后需重启容器
- > 安装命令 elasticsearch-plugin install file:///usr/share/elasticsearch/tmp/elasticsearch-analysis-ik-8.8.1.zip
- 用户：``elasticsearch``
- 用户组：``elk`` 已经对工作目录赋予了基本权限

#### 待更新
- 后面单独打包成镜像解决手动安装插件问题