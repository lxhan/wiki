# Docker

## Basic commands to run a new container 
- Pull postgres image
```sh
docker pull postgres:alpine
```
- Run postgres in docker container
```sh
docker run --name postgres-test -e POSTGRES_PASSWORD=password -d -p 5432:5432 postgres:alpine
```

- Show all processes
```sh
docker ps -a
```

- Start/stop container
```sh
docker start container_id
docker stop container_id
```

- Remove container
```sh
docker rm --force container_id
```

- Execute commands in container 
```sh
docker exec -it container_id bash 
```
