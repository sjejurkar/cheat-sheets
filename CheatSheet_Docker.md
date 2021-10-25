# Docker Cheatsheet
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
### List running containers
```
docker ps
```

### list all containers
```
docker ps -a
```

### connect to a running container
```
docker exec -it <container name> /bin/bash
```


### Copy files from container to local disk
```
docker cp <containerId>:/file/path/within/container /host/path/target
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