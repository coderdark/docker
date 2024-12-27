# Docker

## Links For Commands
- DOCKERFILE: https://docs.docker.com/reference/dockerfile/
- BUILD: https://docs.docker.com/reference/cli/docker/buildx/build/
- RUN: https://docs.docker.com/reference/cli/docker/container/run/
- EXEC: https://docs.docker.com/reference/cli/docker/container/exec/
- IMAGE REPOSITORY: https://hub.docker.com/search?q=&type=image
- STOP VS KILL CONTAINERS: https://www.baeldung.com/ops/docker-stop-vs-kill

## Linux Commands
`echo $SHELL` to find out the shell your system is using

## Shells For OSes
+ alpine3.21  `/bin/sh` - `docker exec -it container_name /bin/sh`
+ ubuntu `bash` - `docker exec -it container_name bash`
+ debian `bash` - `docker exec -it container_name bash`
+ centos `bash` - `docker exec -it container_name bash`
+ fedora `bash` - `docker exec -it container_name bash`

## Docker Commands

| Description                           | Command                                                                              |
|---------------------------------------|--------------------------------------------------------------------------------------|
| Help                                  | `docker -h` or `docker image -h` or `docker container -h`                            |
| List docker images                    | `docker images` or `docker image ls`                                                 |
| List docker containers                | `docker ps -a -s` (-a = all, shows all containers stop or running. -s = size, shows the size of the container |
| To build the image                    | `docker build -t <IMAGE_NAME> .`  (-t = tag, to provide a name for the image)        |
| To run the image                      | `docker run -d --rm -it --name <CONTAINER_NAME> <IMAGE_NAME>` or `docker run -d --rm -it -p 80:8000 --name <CONTAINER_NAME> <IMAGE_NAME>`  (-d = detach, run container in background. --rm = remove when exit. -p = publish, publishes the ports. -i = interactive, Keep STDIN open even if not attached.   Ex: `docker run -it --name <CONTAINER_NAME> <IMAGE_NAME>`                       |
| To view the docker networks           | `docker network ls`                                                                  | 
| To execute commands in a container    | `docker exec -it <CONTAINER_NAME> <COMMAND>` (-it = interactive/tty)  Ex: `docker exec -it my_container bash` or `docker exec -it my_container /bin/sh` |
| Pull image                            | `docker image pull <IMAGE_NAME>`                                                     |
| Remove image                          | `docker image rm <IMAGE_NAME>`                                                       |
| Prune ALL unused images               | `docker image prune`                                                                 |
| Kills container  (SIGKILL)            | `docker kill <CONTAINER_NAME>` or `docker container kill <CONTAINER_NAME>`           |
| Stop container   (SIGTERM)            | `docker stop <CONTAINER_NAME>` or `docker container stop <CONTAINER_NAME>`           |
| Start container                       | `docker start <CONTAINER_NAME>` or `docker container start <CONTAINER_NAME>`         |
| Restart container                     | `docker restart <CONTAINER_NAME>` or `docker container restart <CONTAINER_NAME>`     |
| Remove container                      | `docker rm <CONTAINER_NAME>` or `docker container rm <CONTAINER_NAME>`               |
| Prune ALL stopped containers          | `docker container prune`                                                             |

## Examples
#### ExpressJS Setup with 1 Step
This example only has an index.js with the expressjs code to run a simple server.  No static content.

```javascript
#Build and run step
ARG ALPINE_VERSION=3.21

FROM node:20-alpine${ALPINE_VERSION}      #The image that will be used
WORKDIR /app                              #The working directory where all your content is saved/copied
COPY package*.json ./                     #Copying the package.json and also the index.js.  There is a .dockerignore that ommits the other files.
COPY index.js ./
RUN npm i                                 #Run the install command to install all dependencies of the package.json
CMD ["npm", "start"]                      #Run this command before the container runs
```
#### Vite Setup with 2 Steps
This example has all static files created by vite build command and serve by nginx.

```javascript
#Build

FROM node:20 AS build_step
WORKDIR /app
COPY package.json .
COPY package-lock.json .
RUN npm ci
COPY . .
RUN npm run build

#Run Production
FROM nginx:alpine AS production
COPY --from=BUILD_STEP /app/dist /usr/share/nginx/html
```
