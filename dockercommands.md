## Docker Commands

### Docker Command Syntax
`docker [OPTIONS] COMMAND [arg..]`

Common COMMAND : run, build,rm,start, stop..

### Running our first container

`docker run -p 3636:80 -dt nginx`


-d flag to tell Docker to detach the container to the background

Output
![Docker Run Command](/images/runOutput.PNG "Docker Run Command")


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
$(docker ps -a -q) gives the IDs of containers
docker rm removes the container

### Storage of Docker Containers

`docker system df`