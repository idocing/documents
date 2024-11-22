# postgresql docker

## create container
```
docker pull postgres

docker run --name pg -d -e POSTGRES_PASSWORD=123456 -p 5432:5432 postgres
```