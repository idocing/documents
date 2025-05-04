# config

## edit config
> /etc/docker/daemon.json
```json
{
  "registry-mirrors": [
    "https://docker.1ms.run",
    "https://docker.xuanyuan.me"
  ]
}
```

## restart docker
```bash
systemctl daemon-reload
systemctl restart docker
```

## temporary
```
dockerd --registry-mirror=https://docker.1ms.run
```