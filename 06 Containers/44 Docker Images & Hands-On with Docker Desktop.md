A Docker image is a **file** used to **execute** code in a Docker container.
Docker images act as **a set of instructions** to build a Docker container, like a template.
Docker images also act as the **starting point** when using Docker.

### Exploring Docker Desktop

##### 运行我的第一个 docker 命令

```shell
docker run -d -p 80:80 docker/getting-started
```

因为是第一次运行这个命令，所以日志里会提示 `Ubable to find image 'docker/getting-started:latest' locally `，于是 docker 会去下载这个 image 并给出下载成功的提示文字 `Status: Downloaded newer image for docker/getting-started:latest`

这时候你会发现 docker GUI 里的 Containers tab 里能看到已经有了对应的 running container.
![[Pasted image 20221101120139.png]]

这时候你会发现 docker GUI 里的 Images tab 里能看到已经有对应的 an in-use image called docker/getting-started
![[Pasted image 20221101120035.png]]

##### 运行第二个

```shell
docker run -d -p 80:80 docker/getting-started
```

这次我们之间在命令行运行

```
docker run hello-world
```

打印如下(这个 container 就是为了打印这些😂 )

```console
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

> However, if we go and look in Docker Desktop now we have no running containers but we do have an exited container that used the hello-world message, meaning it came up, delivered the message and then is terminated.

##### 运行第三个

```shell
docker run -it ubuntu bash
```

⬆️ 会运行一个a containerised version of Ubuntu well not a full copy of the Operating system.
⬆️ 这时候就是一个 ubuntu 运行时了，但是 `ip addr`、 `curl`、`wget`、`git` 都是不行的（因为知识迷你版 ubuntu），但是我们可以安装 software 比如 `apt update` ➡️  `apt-get install pinta` 