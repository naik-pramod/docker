## Docker Commands

### Docker Command Syntax
`docker [OPTIONS] COMMAND [arg..]`

Common COMMAND : run, build,rm,start, stop..

Docker expects us to run commands as below
`docker category child-command`

`docker image ls`

### Running our first container

`docker run -p 3636:80 -dt nginx`


-d flag to tell Docker to detach the container to the background

Output
![Docker Run Command](/images/runOutput.PNG "Docker Run Command")

`docker run` = `docker create` + `docker start`

run is combination of creating a container from image and then starting the container 

### List the Running containers
`docker ps`

### List the all containers 
`docker ps -a`

### List the all images 
`docker images`

### Running Container in detached(in background) mode 
`docker run -p 3639:80 -d nginx`

-p indicates port; 3639 is host port and 80 is container port
-d indicates detached mode

### Stop the running containers
`docker stop nginx`

### Remove all stopped containers
`docker rm $(docker ps -a -q)`

This is a combination of 2 commands.
(docker ps -a -q) gives the IDs of containers
docker rm removes the container. 

### Storage of Docker Containers
`docker system df`

### -it
`docker container exec -i -t nginx-test /bin/bash`
The -i flag is shorthand for --interactive, which instructs Docker to keep stdin open so that we can send commands to the process. The -t flag is short for –tty and allocates a pseudo-TTY to the session.
 
 ### pause and unpause
 `docker container pause nginx1`

  `docker container unpause nginx1`

### stop and remove
`docker container stop redis`

`docker container rm redis`

### List Volumes
`docker volume ls`

### Inspect Volume
`docker volume inspect redis_data`

