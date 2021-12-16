### Images
Docker can build images automatically by reading instructions from *Dockerfile*

*Dockerfile* ==> Docker build ==> image

#### Creating a dockerfile

- Specify a base image
- Run some commands to install additional programs
- Specify a command to run on container startup

A Dockerfile must start with a FROM instruction

FROM ubuntu
RUN apt-get update
RUN apt-get install -y nginx
COPY index.nginx-debian.html /var/www/html
CMD nginx -g 'daemon off;'

### FROM
The FROM instruction tells Docker which base you would like to use for your image.

### LABEL
The LABEL instruction can be used to add extra information to the image. This information can be anything from a version number to a description.
You can view the containers’ labels with the following docker inspect command.
`docker image inspect <Image ID>`

Alternatively, you can use the following command to filter just the labels:

`$ docker image inspect -f {{.Config.Labels}} <IMAGE_ID>`

`LABEL maintainer=”Pramod Naik”

LABEL description=”This example Dockerfile installs nginx.”`

### RUN
The RUN instruction is where we interact with our image to install software and run scripts, commands, and other tasks.

RUN apk add --update nginx && \

    rm -rf /var/cache/apk/* && \

    mkdir -p /tmp/nginx/

**The && operator to move on to the next command if the previous command was successful.
We are also using \, which allows us to split the command over multiple lines, making it even easier to read.**

### COPY vs ADD
COPY take in source and destination as local file or directory only.
The ADD instruction can also be used to add content from remote sources. 
ADD take in source and destination as local file or directory, url, tar file.


### EXPOSE
Informs docker that the container listens on the specified network port at runtime.
This indicates the person who runs the container about which ports are intented to be published. (using -p option)

### WORKDIR
Sets the working directory for any RUN,CMD, ENTRYPOINT,COPY and ADD instructions that follow it.

It can be used multiple times in *Dockerfile*

WORKDIR /root/demo
RUN touch file01.txt
CMD ["/bin/sh"]

The above snippet will set /root/demo as working directory and then run the RUN touch command in demo directory and run CMD command in demo directory


### ENV
This instruction sets the environment variable <key> to the <value>
The ENV instruction sets ENVs within the image both when it is built and when it is executed

ENV NGINX 1.2
RUN curl -SL http://example.com/web-%NGINX.tar.xz

We use -e , --env to set/overwrite envionment variables in container your are running.

docker run --env VAR1=value1 --env VAR2=value2

### Tag
Is used to tag the images

`docker build -t demo:v1`
`docker tag 30fb3 demo:v2`
`docker tag ubuntu:latest myubuntu:v1`


### COMMIT
A new image can be created from an existing container

`docker container commit CONTAINER-ID myimage01`

#### Change
Change option is used change specific attibutes of image.
`docker container commit --change='CMD [ash]' container-name`

- CMD, ENTRYPOINT, ENV, EXPOSE, LABEL, ONBUILD, USER, VOLUME, WORKDIR

### History
shows the layers of the image

`docker history nginx` 

### INSPECT
Allows us to see all the information associated with image
`docker image inspect nginx`

`docker images inspect nginx --format='{{.Id}}'`
`docker images inspect nginx --format='{{.ContainerConfig.Hostname}}'`

### PRUNE
Allows us to clean up unused and dangling images

Dangling images are those without tag and not referenced by any container

`docker image prune`
`docker image prune -a`

### Save and Load 
These command helps to transfer images.
first we save the image as tar at destination and then we load the image at destination

At Source:
`docker save image-name > image-name.tar`

At Destination:
`docker load < image-name.tar`