# Docker

## Links For Commands
- BUILD: https://docs.docker.com/reference/cli/docker/buildx/build/
- RUN: https://docs.docker.com/reference/cli/docker/container/run/
- EXEC: https://docs.docker.com/reference/cli/docker/container/exec/

## Docker Commands

| Description                           | Command                                                                              |
|---------------------------------------|--------------------------------------------------------------------------------------|
| List docker images                    | `docker images`                                                                      |
| List docker containers                | `docker ps -a -s` (-a = all, shows all containers stop or running. -s = size, shows the size of the container |
| To build the image                    | `docker build -t <IMAGE_NAME> .`  (-t = tag, to provide a name for the image)        |
| To run the image                      | `docker run -d --rm -it -p 80:8000 --name <CONTAINER_NAME> <IMAGE_NAME>`  (-d = detach, run container in background. --rm = remove when exit. -p = publish, publishes the ports. -i = interactive, Keep STDIN open even if not attached.   Ex: `docker run -it --name <CONTAINER_NAME> <IMAGE_NAME>`                       |
| To view the docker networks           | `docker network ls`                                                                  | 
| To execute commands in a container    | `docker exec -it <CONTAINER_NAME> <COMMAND>` (-it = interactive/tty)  Ex: `docker exec -it my_container bash` |

