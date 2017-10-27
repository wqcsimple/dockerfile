# PHP Redis Admin


## usage
```shell
docker run -d --restart=always \
        --name=pra \
        -p 8082:80 \
        --link redis:redis \
        registry.cn-hangzhou.aliyuncs.com/whis/phpredisadmin:latest
```


## 编写上线脚本 boot_pra.sh