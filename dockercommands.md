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

