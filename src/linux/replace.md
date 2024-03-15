# replace sources

## debian replace sources.list

### huawei
```
sed -i 's/deb.debian.org/mirrors.huaweicloud.com/g' /etc/apt/sources.list
sed -i 's/security.debian.org/mirrors.huaweicloud.com/g' /etc/apt/sources.list
```

### aliyun
```
sed -i 's/deb.debian.org/mirrors.aliyun.com/g' /etc/apt/sources.list
sed -i 's/security.debian.org/mirrors.aliyun.com/g' /etc/apt/sources.list
```

### tencent
```
sed -i 's/deb.debian.org/mirrors.cloud.tencent.com/g' /etc/apt/sources.list
sed -i 's/security.debian.org/mirrors.cloud.tencent.com/g' /etc/apt/sources.list
```

### debian buster (/etc/apt/sources.list)
```
deb http://mirrors.huaweicloud.com/debian buster main
deb http://mirrors.huaweicloud.com/debian buster-updates main
deb http://mirrors.huaweicloud.com/debian-security buster/updates main
```


## ubuntu replace sources.list
```
sed -i 's/archive.ubuntu.com/mirrors.huaweicloud.com/g' /etc/apt/sources.list
sed -i 's/security.ubuntu.com/mirrors.huaweicloud.com/g' /etc/apt/sources.list
```

### ubuntu focal (/etc/apt/sources.list)
```
deb http://mirrors.huaweicloud.com/ubuntu/ focal main restricted universe multiverse
deb http://mirrors.huaweicloud.com/ubuntu/ focal-security main restricted universe multiverse
deb http://mirrors.huaweicloud.com/ubuntu/ focal-updates main restricted universe multiverse
deb http://mirrors.huaweicloud.com/ubuntu/ focal-proposed main restricted universe multiverse
deb http://mirrors.huaweicloud.com/ubuntu/ focal-backports main restricted universe multiverse
```
