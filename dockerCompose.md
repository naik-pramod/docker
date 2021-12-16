### Docker Compose
Docker Compose uses a YAML file, typically named docker-compose.yml, to define what your multi-container application should look like.

version: "3.7"
services:
    redis:
        image: redis:alpine
        volumes:
           - redis_data:/data
        restart: always
    mobycounter:
        depends_on:
            - redis
        image: russmckendrick/moby-counter
        ports:
            - "8080:80"
        restart: always
volumes:
    redis_data:

    To launch our application, we simply change to the folder that contains your docker-compose.yml file and run the following:

`docker-compose up`


### Docker Compose YAML file

It takes the following format:

version: "3.7"

services:

----> container name:

--------> container options

------------> sub options

----> container name:

--------> container options

------------> sub options


### Container Structure

![docker-compose-project-structure](/images/docker-compose-project-structure.PNG "docker-compose-project-structure")
