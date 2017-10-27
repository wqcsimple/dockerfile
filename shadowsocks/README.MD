# docker shadowsocks-libev

### Description
默认绑定本地地址 127.0.0.1 端口 5291

### usage
```
git clone https://code.aliyun.com/whis/shadowsocks.git
cd shadowsocks
```

`docker build .`

build 完成后

`docker tag <existing-image> centos:shadowsocks-3.0.5` 给镜像打个tag

```
docker run -d --restart=always --name=ss  \
    -e PASSWORD=whis.wang \
    -e SERVER_PORT=10001 \
    -p 10001:10001  \
    -e METHOD=aes-256-cfb \
    centos:shadowsocks-3.0.5
```

需要修改其中的3个port


### aliyun usage
`docker pull registry.cn-hangzhou.aliyuncs.com/whis/shadowsocks`
```shell
修改其中端口号 加密方法 密码
docker run -d --restart=always --name=ss \
        -e PASSWORD=whis.wang \
        -e SERVER_PORT=10001 \
        -p 10001:10001  \
        -e METHOD=aes-256-cfb \
        registry.cn-hangzhou.aliyuncs.com/whis/shadowsocks


修改本地端口

docker run -d --restart=always --name=ss \
        -e PASSWORD=whis.wang \
        -e SERVER_PORT=10001 \
        -p 10001:10001  \
        -e METHOD=aes-256-cfb \
        registry.cn-hangzhou.aliyuncs.com/whis/shadowsocks:latest

```