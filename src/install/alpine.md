# alpine

## apk repository
```
vi /etc/apk/repositories

https://mirrors.aliyun.com/alpine/v3.10/main
https://mirrors.aliyun.com/alpine/v3.10/community
```

## service
```
apk add openrc
```

## use open rc
```
rc-status
rc-update
rc-service
```

## gcc compile
```
FROM scratch
ADD alpine.tar.gz /
RUN echo https://mirrors.aliyun.com/alpine/v3.10/main > /etc/apk/repositories \
    && echo https://mirrors.aliyun.com/alpine/v3.10/community >> /etc/apk/repositories \
    && apk --no-cache add gcc g++ make cmake clang zip unzip openrc xz wget curl git subversion
```
