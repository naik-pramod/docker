### Docker Networking
Docker networking system is pluggable, using drivers.

There are several drivers available by default, and provides core networking functionality.

- bridge
 The default network driver. 
 Bridge networks are usually used when your applications run in standalone containers that need to communicate.
User-defined bridge networks are best when you need multiple containers to communicate on the same Docker host.

- host 
 For standalone containers, remove network isolation between the container and the Docker host, and use the host’s networking directly. 
Host networks are best when the network stack should not be isolated from the Docker host, but you want other aspects of the container to be isolated.

- overlay
Overlay networks connect multiple Docker daemons together and enable swarm services to communicate with each other. You can also use overlay networks to facilitate communication between a swarm service and a standalone container, or between two standalone containers on different Docker daemons. This strategy removes the need to do OS-level routing between these containers.
Overlay networks are best when you need containers running on different Docker hosts to communicate, or when multiple applications work together using swarm services.

- macvlan
Macvlan networks allow you to assign a MAC address to a container, making it appear as a physical device on your network. The Docker daemon routes traffic to containers by their MAC addresses.

Macvlan networks are best when you are migrating from a VM setup or need your containers to look like physical hosts on your network, each with a unique MAC address.

- none
For this container, disable all networking. Usually used in conjunction with a custom network driver
