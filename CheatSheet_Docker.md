# Docker Cheat Sheet
Quick reference for common docker commands.

## Docker Images
### List docker images
```
docker images
```

### Build docker image from standard Dockerfile
```
docker build --tag <image_name>:<tag_name> .
```

### Rebuild docker image
Use `--no-cache` option to do a complete rebuild
```
docker build --no-cache --tag <image_name>:<tag_name> .
```

### Pass arguments while building image
```
docker build --build-arg DEMO_MODE=0 --tag <image_name>:<tag_name> .
```

## Docker Containers

### Create a container
Create a container from an image. Options: -p = port mapping, --detach = run in background)
```
docker run -p <host-port>:<container-port> --detach --name <container-name> <image-name>:<tag-name>
```
### List running containers
```
docker ps
```

### List all containers
```
docker ps -a
```

### Connect to a running container
```
docker exec -it <container name> /bin/bash
```

### Copy files from container to local disk
```
docker cp <containerId>:/file/path/within/container /host/path/target
```

### Copy files local disk to from container
```
docker cp /host/path/target <containerId>:/file/path/within/container
```

### export/save image to gzip file
```
docker save my-image:my-tag | gzip -c > my_image_my_tag.gz
```

### import image from gzip file
```
docker load < my_image_my_tag.gz
```

## Docker Compose
### Build image using docker-compose
```
docker-compose build
```

### Build force image using docker-compose
```
docker-compose build --no-cache
```

### Start container and dependent containers using docker-compose
```
docker-compose up
```

### Stop container and dependent containers using docker-compose
```
docker-compose down
```

## Docker Networks
List all networks a container belongs to
```
docker inspect -f '{{range $key, $value := .NetworkSettings.Networks}}{{$key}} {{end}}' [container]
```

List all containers belonging to a network by name
```
docker network inspect -f '{{range .Containers}}{{.Name}} {{end}}' [network]
```

Attach a running container to a network
```
docker network connect [network] [container]
```

## Docker and PostgreSQL database
The following commands assume that you are running PostgreSQL database in a container named `postgres-db`

### Export data from PostgreSQL database into a file
```
docker exec -i postgres-db pg_dump -U postgres -W postgres > /path/to/db_dump.sql
```

### Import data into PostgreSQL database from a dump file
```
cat your_dump.sql | docker exec -i postgres-db psql -U postgres
```

### Connect to PostgreSQL database on docker container
First, log into the container running PostgreSQL database:
```
docker exec -it postgres-db bash
```

Then run the following command to login to PostgreSQL database:
```
psql -h localhost -p 5432 -U postgres -W
```
