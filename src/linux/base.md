# base image

## debian 10
```
FROM scratch

ADD debian-rootfs.tar.xz /

CMD ["bash"]
```

## debian base
```
FROM irepoing/debian:10

RUN apt update -y && apt install -y procps less curl wget telnet vim zip unzip git net-tools lsof tcpdump strace traceroute \
    && apt install -y tzdata && \cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && apt autoremove && apt autoclean && apt clean

CMD ["bash"]
```

## ubuntu base
```
FROM irepoing/ubuntu:20

ENV DEBIAN_FRONTEND=noninteractive

RUN apt update -y && apt install -y procps less curl wget telnet vim zip unzip git net-tools lsof tcpdump strace traceroute \
    && apt install -y tzdata && \cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && apt autoremove && apt autoclean && apt clean

CMD ["bash"]
```