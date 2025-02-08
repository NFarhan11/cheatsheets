# Docker

## Command

`docker pull [IMAGE]`

- download image from cloud.

`docker images`

- lists all images on system.

`docker rmi [IMAGE]`

- removes image from system.

`docker ps -a`

- list all ran containers.

`docker run [IMAGE]`

- find [IMAGE], load up container, and runs cmd in that container.

`docker run -it [IMAGE] bash`

- attach to container's shell (interactive tty).
- `bash` for open shell inside container with no interactive default command.

`docker run [IMAGE] --rm`

- deletes a container once exited, good or one off docker runs.

`docker run -d -P --name [IMAGE]`

- `d` detach terminal
- `P` publish all exposed ports
- `name` assign name to container

`docker run -p <host_port>:<container_port> [IMAGE]`

- run container and map ports.

`docker rm [CONTAINER]`

- delete container.

`docker rm $(docker ps -a -q -f status=exited)`

- delete all containers that have `exited` status.

`docker container prune`

- deletes all exited status. (Recommended).

`docker port [CONTAINER]`

- lists port mappings.

`docker exec [CONTAINER]`

- execute commands in running container.

## USUAL CMD

`docker run -dt --name [container_name] [IMAGE]`

- run container and detach while running.

`docker exec -it [container_name] bash`

- enter container shell.

`docker stop [container_name]`

- stop running container.

`docker start [container_name]`

- start existing stopped container.

`docker stats`

- checks resources usage.

## Terminology

Detached Mode

- Terminal separate from container.

## Build Image

### Dockerfile

```
FROM [BASE_IMAGE]

WORKDIR [app_directory]

COPY . .

RUN [DEPENDENCIES]

EXPOSE [PORTS]

CMD [APP_RUN_CMD]
```

`docker build -t [name:tag] [Dockerfile_location]`

- build docker image from Dockerfile. Use `.` for current location

## Docker Compose

- tool for define and run multi-container Docker apps easy way.
- `docker-compose.yml` is the config file.

`docker-compose up -d`
