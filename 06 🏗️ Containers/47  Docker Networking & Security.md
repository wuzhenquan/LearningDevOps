### Docker Networking Basics

了解一下 `docker network <command>` 命令
`docker network` 可以直接查看这些 commands

##### `docker network ls` 
Each network gets a unique ID and NAME. Each network is also associated with a single driver. Notice that the "bridge" network and the "host" network have the same name as their respective drivers.


##### `docker network inspect <argument>`
`docker network inspect bridge` 执行后打印了下面这些 ⬇️  包括了 name, ID, drivers, connected containers 等等
```json
[
    {
        "Name": "bridge",
        "Id": "3a6f1ab034279b4437ebd12075f1f49cd28b4421d8e0c04fd0eb2b05c340ecd9",
        "Created": "2022-11-03T08:41:46.038948791Z",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": null,
            "Config": [
                {
                    "Subnet": "172.17.0.0/16",
                    
                    "Gateway": "172.17.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {},
        "Options": {
            "com.docker.network.bridge.default_bridge": "true",
            "com.docker.network.bridge.enable_icc": "true",
            "com.docker.network.bridge.enable_ip_masquerade": "true",
            "com.docker.network.bridge.host_binding_ipv4": "0.0.0.0",
            "com.docker.network.bridge.name": "docker0",
            "com.docker.network.driver.mtu": "1500"
        },
        "Labels": {}
    }
]
```



### Docker: Bridge Networking

Docker Desktop gives us a pre-built network called `bridge`. 
执行 `docker network list` 可以看到 the network called bridge is associated with the `bridge` driver. 同名但 not the same thing. Connected but not the same thing.

`docker network inspect bridge` 打印出来来其中的 `"Scope": "local"` 表示 bridge network is scoped locally。意思就是这个 network 只存在于 Docker host 中

All networks created with the bridge driver are based on a Linux bridge

### Connect a Container

默认情况下，所有新建的 containers will be connected to the bridge network.

让我们来验证下
1️⃣ `docker run -dt ubuntu sleep infinity` 执行后创建了一个 new container 并返回一个 container ID
	_`sleep` to keep the container running in the background_

2️⃣ `docker ps`
![[Pasted image 20221104141627.png]]

3️⃣ `docker network inspect bridge` 
have a container matching, but did not specify a network
![[Pasted image 20221104141709.png]]
![[Pasted image 20221104141734.png]]

4️⃣ `docker exec -it <container ID> bash` (执行 `docker ps` to get your `<container ID>`)
这个命令可以 dive into the container
![[Pasted image 20221104142026.png]]
	`apt-get update && apt-get install -y iputils-ping` 这个包可以让我们拥有 ping 的能力

5️⃣ ping 一下 ` ping -c5 www.90daysofdevops.com`
![[Pasted image 20221104142343.png]]

5️⃣ 关闭这个 container `docker stop <container ID>` 

### Configure NAT for external connectivity

启动一个 NGINX 并且 map port 8080 to port 80

1️⃣ `docker run --name web1 -d -p 8080:80 nginx`  to start a new container based on the official NGINX image

2️⃣ `docker ps` 
![[Pasted image 20221104145729.png]]
Take note of the **COMMAND** the container is running as well as the **PORT** mapping - `0.0.0.0:8080->80/tcp` maps port 8080 on all host interfaces to port 80 inside the web1 container. This port mapping is what effectively makes the container's web service accessible from external sources (via the Docker hosts IP address on port 8080).

3️⃣ IP address for our actual host, WSL 下执行 `ip addr`
![[Pasted image 20221104153302.png]]

4️⃣  浏览器访问这个⬆️ ip http://192.168.167.92:8080 看到下图 ⬇️ 表示 NGINX 可以 accessible 了
![[Pasted image 20221104153713.png]]

I have taken these instructions from this site from way back in 2017 DockerCon but they are still relevant today. However, the rest of the walkthrough goes into Docker Swarm and I am not going to be looking into that here. [Docker Networking - DockerCon 2017](https://github.com/docker/labs/tree/master/dockercon-us-2017/docker-networking) 

### Securing your containers

### Move away from root permission

### Private Registry

### Lean & Clean
Checking `docker image` is a great command to see the size of your images.
![[Pasted image 20221104160127.png]]


