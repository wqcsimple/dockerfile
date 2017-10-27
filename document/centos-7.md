# Centos docker config


## mysql
```
安装mysql
docker run -d --restart=always \
    --name mysql \
    -e MYSQL_ROOT_PASSWORD=root  \
    -v /opt/data/mysql:/var/lib/mysql \
    -p 3306:3306 \
    mysql:5.7

备份mysql
docker exec mysql sh -c 'exec mysqldump --all-databases -uroot -p"$MYSQL_ROOT_PASSWORD"' > /opt/backup/mysql/all-databases.sql
```

## phpmyadmin

```
docker run --name phpmyadmin -d --link mysql:db -p 8080:80 phpmyadmin/phpmyadmin   安装phpmyadmin
phpmyadmin 配置文件
docker run -d --restart=always \
    --name phpmyadmin  \
    --link mysql:db \
    -p 8080:80  \
    -v /opt/data/phpmyadmin/config.user.inc.php:/etc/phpmyadmin/config.user.inc.php \
    phpmyadmin/phpmyadmin
```

## Mongodb

参考文档 [https://hub.docker.com/r/library/mongo/](https://hub.docker.com/r/library/mongo/)
```
配置mongodb
docker run -d --restart=always --name mongodb -v /opt/data/mongodb/db:/data/db -p 27017:27017 -d mongo
```




docker run -d --restart=always \
        --name=$docker_container \
        -p $port \
        --add-host=$host1 \
        --add-host=$host2 \
        --add-host=$host3  \
        --link redis:redis \
        --link mysql:db    \
        -v $volume \
        $docker_image

