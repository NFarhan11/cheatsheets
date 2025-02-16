# Docker

### Docker Main Resource: IMAGES, CONTAINERS, VOLUMES, NETWORKS

## Basic Commands

|    Command     | Description                     |
| :------------: | :------------------------------ |
| docker version | Show Docker version             |
|  docker info   | Display system-wide information |
|  docker help   | Get help on a command           |

## IMAGE & CONTAINER

- a list of `layers` forms an `image`.
- an `image` is a blueprint for a `container`.
- `container commit` not usually used, instead use Dockerfile.
- a Dockerfile creates an `image`.

### Layers & Image Management

|                              Command                              | Description                        |
| :---------------------------------------------------------------: | :--------------------------------- |
|                           docker images                           | List available images              |
|                       docker pull `<image>`                       | Download an image from Docker Hub  |
|                    docker build -t `<name>` .                     | Build an image from a Dockerfile   |
|                       docker rmi `<image>`                        | Remove an image                    |
|                 docker tag `<image>` `<new-name>`                 | Tag an image                       |
|                       docker push `<image>`                       | Push an image to a registry        |
| docker container commit -m "message" `<base-image>` `<new-image>` | Create new image from a container. |
|                  docker image history `<image>`                   | Shows all layers of the image.     |

### Container Management

|                           Command                            | Description                                             |
| :----------------------------------------------------------: | :------------------------------------------------------ |
|                          docker ps                           | List running containers                                 |
|                         docker ps -a                         | List all containers                                     |
|                  docker start `<container>`                  | Start a stopped container                               |
|                  docker stop `<container>`                   | Stop a running container                                |
|                 docker restart `<container>`                 | Restart a container                                     |
|                   docker rm `<container>`                    | Remove a container                                      |
|                  docker logs `<container>`                   | View container logs                                     |
|                 docker inspect `<container>`                 | View detailed information                               |
|              docker exec -it `<container>` bash              | Enter a running container                               |
|          docker cp `<container-path>`:`<host-path>`          | Copy files from container                               |
| docker run -d -p 8080:80 --name `<container_name>` `<image>` | Run a container in detached mode                        |
|      docker run -dt --name `<container_name>` `<image>`      | Run a container in detached mode (`t` -> stays running) |
|                  docker run --rm `<image>`                   | Run and remove container after exit                     |
|   docker run -v `<host-path>`:`<container-path>` `<image>`   | Mount a volume                                          |
|              docker run -e VAR=value `<image>`               | Set environment variables                               |
|             docker run --network=host `<image>`              | Use host network                                        |

### Overriding Container Defaults

|   Flag    | Description                                            |
| :-------: | :----------------------------------------------------- |
| --network | Override default network `bridge` with custom network. |
|    -e     | Set ENV variables.                                     |
|    -v     | Set volume.                                            |
|  --cpus   | Specifies CPU quota for the container.                 |
| --memory  | Specifies memory limit for the container.              |

### Dockerfile Example

```dockerile
# Use base image
FROM node:18

# Set working directory
WORKDIR /app

# Copy files and install dependencies
COPY package.json .
RUN npm install

# Copy application files
COPY . .

# Expose port
EXPOSE 3000

# Start application
CMD ["node", "server.js"]
```

### Dockerfile Common Instruction

|            Instruction            | Description                                                                                                                           |
| :-------------------------------: | :------------------------------------------------------------------------------------------------------------------------------------ |
|          FROM `<image>`           | specifies the base image that the build will extend.                                                                                  |
|         WORKDIR `<path>`          | this instruction specifies the "working directory" or the path in the image where files will be copied and commands will be executed. |
| COPY `<host-path>` `<image-path>` | this instruction tells the builder to copy files from the host and put them into the container image.                                 |
|          RUN `<command>`          | this instruction tells the builder to run the specified command.                                                                      |
|      ENV `<name>` `<value>`       | this instruction sets an environment variable that a running container will use.                                                      |
|      EXPOSE `<port-number>`       | this instruction sets configuration on the image that indicates a port the image would like to expose.                                |
|       USER `<user-or-uid>`        | this instruction sets the default user for all subsequent instructions.                                                               |
|  CMD ["`<command>`", "`<arg1>`"]  | this instruction sets the default command a container using this image will run.                                                      |

## Docker Volumes

|             Command              | Description      |
| :------------------------------: | :--------------- |
|         docker volume ls         | List volumes     |
| docker volume create `<volume>`  | Create a volume  |
|   docker volume rm `<volume>`    | Remove a volume  |
| docker volume inspect `<volume>` | Inspect a volume |

## Docker Networks

|                       Command                       | Description                    |
| :-------------------------------------------------: | :----------------------------- |
|                  docker network ls                  | List networks                  |
|          docker network create `<network>`          | Create a network               |
|            docker network rm `<network>`            | Remove a network               |
|         docker network inspect `<network>`          | Inspect a network              |
|  docker network connect `<network>` `<container>`   | Connect container to a network |
| docker network disconnect `<network>` `<container>` | Disconnect container           |

## Docker Compose

|            Command            | Description                                  |
| :---------------------------: | :------------------------------------------- |
|     docker-compose up -d      | Start services in detached mode              |
|      docker-compose down      | Stop and remove containers                   |
| docker-compose down --volumes | Stop and remove containers including volumes |
|       docker-compose ps       | List running services                        |
|      docker-compose logs      | View logs                                    |
|    docker-compose restart     | Restart all services                         |

## Prune Unused Resources

|        Command         | Description                                |
| :--------------------: | :----------------------------------------- |
| docker system prune -a | Remove unused containers, images, networks |
|  docker volume prune   | Remove unused volumes                      |
|   docker image prune   | Remove dangling images                     |

## Debugging & Logs

|           Command            | Description                               |
| :--------------------------: | :---------------------------------------- |
| docker logs -f `<container>` | Follow logs                               |
|  docker stats `<container>`  | View real-time resource usage             |
|   docker top `<container>`   | Show running processes inside a container |
|        docker events         | Show real-time Docker events              |
