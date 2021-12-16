
### Run Container

we launched the most basic container of all, the hello-world container, using the following command:
`docker container run hello-world`

### List Containers
`docker container ls -a`

### Run Container with name
`docker container run -d --name nginx-test -p 8080:80 nginx`
-d ==> detached
--name ==> Name the container
-p ==> map host port to container port. 8080: host port, 80: container port
 