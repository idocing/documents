# debian

## base
```
FROM irepoing/debian:10

ENV DEBIAN_FRONTEND=noninteractive

RUN apt update -y \
&& apt install -y tzdata less curl wget telnet vim zip unzip git \
&& \cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
&& apt autoremove \
&& apt autoclean \
&& apt clean

CMD ["bash"]
```