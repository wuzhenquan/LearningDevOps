
Docker compose: allows you to run more complex apps over multiple containers.

walkthrough 从 [Docker QuickStart sample apps (Quickstart: Compose and WordPress)](https://docs.docker.com/samples/wordpress/). 而来的

这个 walkthrough 打算
-   Use Docker compose to bring up **WordPress** and **a separate MySQL** instance.
-   Use a YAML file which will be called `docker-compose.yml`
-   Build the project
-   Configure WordPress via a Browser
-   Shutdown and Clean up

### Install Docker Compose

安装了 Docker Desktop 就已经安装了 Docker Compose
执行 `docker-componse` 确认是否已经安装

### Docker-Compose.yml (YAML)

YAML is a data **serialization** language
make it a viable replacement for languages like JSON.

used for
- configuration files
- data is being stored or transmitted

⬇️ `docker-compose.yml` file
```yml
version: "3.9"

services:
  DB:
    image: mysql:5.7
    volumes:
      - db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: somewordpress
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress

  wordpress:
    depends_on:
      - db
    image: wordpress:latest
    volumes:
      - wordpress_data:/var/www/html
    ports:
      - "8000:80"
    restart: always
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
      WORDPRESS_DB_NAME: wordpress
volumes:
  db_data: {}
  wordpress_data: {}
```

### Build the project

用这个 respository 做 walkthrough ➡️ [my-wordpress](https://github.com/docker/awesome-compose/tree/master/official-documentation-samples/wordpress) 

1. `mkdir my-wordpress && cd my-wordpress && touch docker-compose.yml` 
2. 将 [my-wordpress](https://github.com/docker/awesome-compose/tree/master/official-documentation-samples/wordpress) 中的 yml 内容复制过来
3. 在 `my-wordpress` 目录下运行 `docker-compose up -d` 
	1. `-d` means detached mode, 意思就是 the Run command is or will be in the background
4. run `docker ps` command
	1. 能看到两个 containers 在 running：WordPress and MySQL
	2. ![[Pasted image 20221104105004.png]]
	3. [![](https://github.com/MichaelCade/90DaysOfDevOps/raw/main/Days/Images/Day46_Containers3.png)](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Images/Day46_Containers3.png) 
5. 验证 WordPress 是否在 up and running 了, 浏览器访问 ➡️  http://localhost:80
7. 可以看到在 Docker Desktop 里的 volumes tab 有两个 volumes，WordPress 和 DB

### Clean Up or not 

`docker-compose down` bring down containers, but will leave our volumes in place.
	`docker-compose down --volumes` 会 destory volumes

`docker-compose up -d` have application back up and running.
![[Pasted image 20221104104312.png]]

浏览器访问 `http://localhost:8000` 可以看到之前创建的数据还在




