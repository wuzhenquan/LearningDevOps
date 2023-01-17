
Container toolchain: Docker, [CRI-O](https://cri-o.io/), [Podman](http://podman.io/), [LXC](https://linuxcontainers.org/), and others.

Docker
- a software framework
- 🏗️ building container
- 🏃🏻 running container
- 👨🏻‍💼 managing container
- referring to the docker project overall, which is a platform for devs and admins to develop, ship and run applications.

### Docker Engine

-   A server with a long-running daemon process dockerd.
-   APIs specify interfaces that programs can use to talk to and instruct the Docker daemon.
-   A command line interface (CLI) client docker.
⬆️ [Docker Engine Overview](https://docs.docker.com/engine/) 

### Docker Desktop

- native OS application
- build, debug, package, ship Dockerized application

### Docker Compose

being able to use a single file and command to spin up your application.

### Docker Hub

除了是 a registry to host docker images，还有 automation、integrated into Github、security scanning的功能。

### Docker Image
- is a **file** used to **execute** code in a docker container.
- defines the structure of a docker container. 
- is a buleprint for creating a docker contanier. 

所有的 docker image 都是通过 base image 构建的，这些 base image 可以是
- an image of a runtime environment, e.g java, node.
- an image of a operating system e.g ubuntu.

The most popular way of creating a docker image is through a [[#Dockerfile]] 

## Installing Docker Desktop
https://docs.docker.com/desktop/install/mac-install/ 