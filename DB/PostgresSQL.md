# Using PostgreSQL Database

## Docker Commands to pull and run

```bash
docker pull postgres:12
docker run--name psqltest-e POSTGRES_PASSWORD=secret -e POSTGRES_USER=dev \
 -e POSTGRES_DB=dev -d postgres:12
 docker ps
 #Get IP address for use
 docker inspect -f'{{. NetworkSettings. IPAddress}}' psqltest
 ```

 After running, `docker exec -it psqltest psql --user dev`, tables, etc can be created.

 BETTER WAY for providing passworeds and such, create init.sql and .env under config and use docker-compose:

### .env file (put in .gitignore, do NOT check in)

 ```BASH
POSTGRES_USER=dev
POSTGRES_PASSWORD=secret
POSTGRES_DB=dev
 ```

### init.sql file

```BASH
create table post (
    id serial unique not null,
    title varchar(128),
    content text,
    primary key (id)
);
insert into post (title, content) values (
    'Hello Docker Compose with PostgreSQL',
    'This is my first Post using Docker Compose with PostgreSQL'
);
```

### docker-compose.yaml

```YAML
version: '3'

services:
    postgres:
        image: postgres:12
        restart: on-failure:5
        ports:
            - 5432:5432
        volumes:
            - ./db_data:/var/lib/postgresql/data
            - ./config/init.sql:/docker-entrypoint-initdb.d/10-init.sql
        env_file:
            - config/.env
```

```BASH
docker-compose up -d
# Get runing containers
docker ps [-a]
docker inspect <contaier-id>

## Getting help on volumes
docker volume--help
docker volume create myvol
docker volume ls
docker volume inspect myvol
docker volume rm myvol

# Moun commands, Target below is volume name inside docker
docker run -itd --name voltest --mount source=myvol,target=/vol alpine
docker exec -it voltest sh
docker run -itd --name vol2test -v myvol:/vol alpine 
cd /vol/
ls
```

To stop everything quitely:
`docker stop $(docker ps -aq)`

Run using example GO Code:
`go run main.go`

[Docker PostgresSQL Page](https://hub.docker.com/_/postgres)
[Youtube tutorial](https://www.youtube.com/watch?v=Zl300YjrobA)
[Code from Beginner Tutorial](https://github.com/NerdCademyDev/docker)
