A Docker image is
- a read-only template
- contains a set of instructions
- for creating a container

如何创建 docker image？create a Dockerfile

### What is a Dockerfile

➡️  [docker file example](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Containers/Dockerfile) 
- text file
- contains commands
- **instructions on how Docker will build your docker image**.

组成 docker image 的每个文件称为层。这些层由下往上构建，每个层都依赖于下方的层。层如果顺序合理，那么 docker images 生命周期管理效率会更高。
a live operational conatiner 和 source image 的唯一区别：创建 container 时会添加一个可写层，也可称为容器层。
[![](https://github.com/MichaelCade/90DaysOfDevOps/raw/main/Days/Images/Day45_Containers1.png)](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Images/Day45_Containers1.png)
像 Ubuntu image 这样的 docker image 称为 parent image，是构建所有其他 layers 的基础，为我们的 container environment 提供了基本模块

manifest.json contains
- a Docker image includes a manifest.json
- description of the Docker image
- comprises information(image tags, a digital signature, and details)

🌰例子1
```Dockerfile
#specify the basic image 语法➡️ `FROM <baseImageName>:<tag>`
From openjsk:11

#copy the jar file into the container. jar file 是 everything needed to run the application
Add target/*.jar app.jar

#执行命令`java -jar appname.jar`
ENTRYPOINT ["java", "-jar", "app.jar"] 
```

🌰例子2
```Dockerfile
From node:17-alpine

#makes a new directory
WORKDIR /app

#copy the source code into the new directory
COPY src/ .

#install the dependecies into the container
RUN npm install

CMD ["node", "app.js"]
```

### How to create a docker image

有两种方式创建 docker image
- spin up 一个 container 并且安装需要的软件和依赖后，执行 `docker commit container name` 去创建
	- quickest and most simple way
- 另外一种方式是通过 dockefile 去创建，这是目前在初学期间比较推荐的。
	- much easier lifecycle management
	- easy integration into CI and CD

##### 现在我们来使用 dockerfile 来创建一个 docker image

three-step: create the dockerfile ➡️ add the commands(🌰 [docker file example](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Containers/Dockerfile) )

⬇️ 最常用的几个 dockerfile statement: 
FROM | WORKDIR | RUN | COPY | ADD | ENTRYPOINT | CMD | EXPOST | LABEL

repository ➡️ how to build our first dockerfile ➡️ [Containers](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Containers) 

1. create a `.dockerignore` file
2. create a simple `Dockerfile` file
3. run `docker build -t 90daysofdevops:0.1`  (`docker build -t {{username}}/{{imagename}}:{{version}}`) 
	1. [![](https://github.com/MichaelCade/90DaysOfDevOps/raw/main/Days/Images/Day45_Containers3.png)](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Images/Day45_Containers3.png)
4. 在 Docker Desktop 的 containers 上查看
	1. [![](https://github.com/MichaelCade/90DaysOfDevOps/raw/main/Days/Images/Day45_Containers4.png)](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Images/Day45_Containers4.png)
5. Whilst in Docker Desktop there is also the ability to leverage the UI to do some more tasks with this new image.
	1. [![](https://github.com/MichaelCade/90DaysOfDevOps/raw/main/Days/Images/Day45_Containers5.png)](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Images/Day45_Containers5.png)
6. We can inspect our image, in doing so you see very much of the dockerfile and the lines of code that we wanted to run within our container.
	1. [![](https://github.com/MichaelCade/90DaysOfDevOps/raw/main/Days/Images/Day45_Containers6.png)](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Images/Day45_Containers6.png) 
7. If you are using the same `docker build` we ran earlier then this would not work either, you would need the build command to be `docker build -t {{username}}/{{imagename}}:{{version}}`
	1. 意思就是说之前的 `docker build -t 90daysofdevops:0.1` 是 push 不了的，要加 username 才能 push 上去，不信可以试试
	2. [![](https://github.com/MichaelCade/90DaysOfDevOps/raw/main/Days/Images/Day45_Containers7.png)](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Images/Day45_Containers7.png) 
9. Then if we go and take a look in our DockerHub repository you can see that we just pushed a new image. Now in Docker Desktop, we would be able to use that pull tab.
	1. [![](https://github.com/MichaelCade/90DaysOfDevOps/raw/main/Days/Images/Day45_Containers8.png)](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/Days/Images/Day45_Containers8.png) 