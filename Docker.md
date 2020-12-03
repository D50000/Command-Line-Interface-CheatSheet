# ===============  Docker Command  ===============  
Detail:  
https://docs.docker.com/engine/reference/commandline/docker/


## Commands
<details>
<summary>view subjects</summary>

- Install Docker package
```shell
yum install -y docker
```

- Start Docker service
```shell
systemctl start docker
```

- Auto start Docker when reboot
```shell
systemctl enable docker
```

- Version check
```shell
docker -v
```

- Search the Docker image name from Docker hub
```shell
docker search [ubuntu] -f is-official=true
```

- Download the image
```shell
docker pull [ubuntu]
```

- List images in local
```shell
docker images
```

- Build Docker image, default will run the "Dockerfile".
```shell
docker build -t [imageName] . --no-cache
```

- Run a docker container
```shell
docker run [hello-world]
```

- Run the image and go in the container's terminal
```shell
docker run -it [ubuntu] /bin/bash
```

- Check all the Docker services
```shell
docker ps -a
```

- Enter the running container
```shell
docker exec [containerID] /bin/bash
```

- Exit and close the container
```shell
exit
```

- Remove the container/image.
```shell
docker rm -f [ContainerName]
docker rmi [imageName]
```

- Mapping host's port to container's port.
```shell
docker run -p 8080:8080 [imageName]
```

- Exit but container keep alive  
```ctrl + p``` + ```ctrl + q```

- Export/Import the Docker Image into a **.tar**
```shell
docker save -o [name2.tar] name1
docker load -i [name2.tar]
```

</details>


## Docker File
```
FROM centos:7    # Docker Image name
MAINTAINER jack    # Docker autor

RUN yum install -y wget    # linux command
RUN cd /

ADD jdk-8u152-linux-x64.tar.gz /    # Add the file to the image. (Same with Dockerfile folder)
RUN wget http://apache.stu.edu.tw/tomcat/tomcat-7/v7.0.82/bin/apache-tomcat-7.0.82.tar.gz
RUN tar zxvf apache-tomcat-7.0.82.tar.gz    # Untar the file.

ENV JAVA_HOME=/jdk1.8.0_152    # Set up ENV $PATH for container
ENV PATH=$PATH:/jdk1.8.0_152/bin

CMD ["/apache-tomcat-7.0.82/bin/catalina.sh", "run"]    # Docker run will start this service
```