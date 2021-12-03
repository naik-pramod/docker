## Docker Components

- The Docker Client and Server
- Docker Images
- Registries
- Docker Containers

![Docker Architecture](/images/DockerArch.PNG "Docker Architecture")

Docker has a client-server architecture.
It has two binaries, the Docker server provided via the dockerd binary and the
docker binary, that acts as a client. As a client, the docker binary passes requests
to the Docker daemon, and then
processes those requests when they are returned.