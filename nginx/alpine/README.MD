# Nginx Alipine:3.4

### usage
```
docker run --name web \
    -d --restart=always \
    -p 9001:80 \
    -p 9002:443 \
    -v /opt/app/nginx/web:/opt/htdocs \
    -v /opt/log/nginx:/var/log/nginx \
    registry.cn-hangzhou.aliyuncs.com/whis/nginx-alpine:1.0.1
```