# Docker

## Links For Commands
- BUILD: https://docs.docker.com/reference/cli/docker/buildx/build/
- RUN: https://docs.docker.com/reference/cli/docker/container/run/

## Docker Commands

| Description                           | Command                                                                              |
|---------------------------------------|--------------------------------------------------------------------------------------|
| To build the image                    | docker build -t <IMAGE_NAME> .  (-t = tag, to provide a name for the image)                 |
| To run the image                      | docker run -d --rm -i -p 80:8000 --name <CONTAINER_NAME> <IMAGE_NAME>  (-d = detach, run container in background. --rm = remove when exit. -p = publish, publishes the ports. -i = interactive, Keep STDIN open even if not attached               |

