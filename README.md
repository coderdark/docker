# Docker

## Links For Commands
- DOCKERFILE: https://docs.docker.com/reference/dockerfile/
- BUILD: https://docs.docker.com/reference/cli/docker/buildx/build/
- RUN: https://docs.docker.com/reference/cli/docker/container/run/
- EXEC: https://docs.docker.com/reference/cli/docker/container/exec/
- IMAGE REPOSITORY: https://hub.docker.com/search?q=&type=image

## Linux Commands
`echo $SHELL` to find out the shell your system is using

## Shells For OSes
+ alpine3.21  `/bin/sh` - `docker exec -it container_name /bin/sh`
+ ubuntu `bash` - `docker exec -it container_name bash`
+ debian `bash` - `docker exec -it container_name bash`
+ centos `bash` - `docker exec -it container_name bash`

## Docker Commands

| Description                           | Command                                                                              |
|---------------------------------------|--------------------------------------------------------------------------------------|
| Help                                  | `docker -h` or `docker image -h` or `docker container -h`                            |
| List docker images                    | `docker images` or `docker image ls`                                                 |
| List docker containers                | `docker ps -a -s` (-a = all, shows all containers stop or running. -s = size, shows the size of the container |
| To build the image                    | `docker build -t <IMAGE_NAME> .`  (-t = tag, to provide a name for the image)        |
| To run the image                      | `docker run -d --rm -it -p 80:8000 --name <CONTAINER_NAME> <IMAGE_NAME>`  (-d = detach, run container in background. --rm = remove when exit. -p = publish, publishes the ports. -i = interactive, Keep STDIN open even if not attached.   Ex: `docker run -it --name <CONTAINER_NAME> <IMAGE_NAME>`                       |
| To view the docker networks           | `docker network ls`                                                                  | 
| To execute commands in a container    | `docker exec -it <CONTAINER_NAME> <COMMAND>` (-it = interactive/tty)  Ex: `docker exec -it my_container bash` or `docker exec -it my_container /bin/sh` |
| Pull image                            | `docker image pull <IMAGE_NAME>`                                                     |
| Remove image                          | `docker image rm <IMAGE_NAME>`                                                       |
| Prune ALL unused images               | `docker image prune`                                                                 |
| Stop container                        | `docker container stop <CONTAINER_NAME>`                                             |
| Start container                       | `docker container start <CONTAINER_NAME>`                                            |
| Restart container                     | `docker container restart <CONTAINER_NAME>`                                          |
| Remove container                      | `docker container rm <CONTAINER_NAME>`                                               |
| Prune ALL stopped containers          | `docker container prune`                                                             |

