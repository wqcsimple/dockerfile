# Shadowsocks

```shell

docker run -d --restart=always --name=ss \
        -e PASSWORD=whis.wang \
        -e SERVER_PORT=10001 \
        -p 10001:10001  \
        -e METHOD=aes-256-cfb \
        registry.cn-hangzhou.aliyuncs.com/whis/shadowsocks:1.0.5
```