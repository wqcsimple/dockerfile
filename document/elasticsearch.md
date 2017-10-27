# Elastic Search

```
docker run -d \
    --name=es \
    -p 9200:9200 \
    -e "ES_JAVA_OPTS=-Xmx1024m -Xms512m" \
    elasticsearch
```

```
docker run -d --restart=always  \
    --name=search \
    -p 9200:9200    \
    -v /opt/data/elasticsearch/data:/usr/share/elasticsearch/data  \
    -v /opt/data/elasticsearch/config:/usr/share/elasticsearch/config \
    elasticsearch:2.4.5
```

```
docker exec -it search /etc/init.d/elasticsearch restart 重启

docker exec -it search bin/plugin install mobz/elasticsearch-head   安装插件

docker exec -it search bin/elasticsearch -h 查看帮助
```