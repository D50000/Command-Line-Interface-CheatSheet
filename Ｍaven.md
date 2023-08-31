# =============== Ｍaven Command ===============

Detail:  
https://docs.docker.com/engine/reference/commandline/docker/

## General Commands

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
docker search [imageName] -f is-official=true
```

- Download the image

```shell
docker pull [imageName]
```

- List images in local

```shell
docker images
```

- Build Docker image, default will run the "Dockerfile".

```shell
docker build -t [imageName] . --no-cache
```

- Run a docker image and container's process will run up.

```shell
docker run [imageName]
```

- Mapping the host's storage path with docker container's storage path.

```shell
docker run -it -v /[hostPath]:/[containerPath] [imageName] /bin/bash
```

- Run the image and go in the container's terminal

```shell
docker run -it [imageName] /bin/bash
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
docker rmi [IMAGE ID]
```

- Mapping host's port to container's port.

```shell
docker run -p 8080:8080 [imageName]
```

- Exit but container keep alive  
  `ctrl + p` + `ctrl + q`

- Export/Import the Docker Image into a **.tar** (execute in host)

```shell
docker save -o [imageName.tar] [imageName]
docker load -i [imageName.tar]
```

- Export/Import the Docker container into a **.tar** (execute in container)

```shell
docker export [ContainerName] > [ContainerName.tar]
cat [ContainerName.tar] | docker import - [ImportContainerName.tar]
```

</details>
