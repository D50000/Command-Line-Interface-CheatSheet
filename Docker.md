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

- Run the image and go in the container's terminal
```shell
docker run -it [ubuntu] /bin/bash
```

- Check all the Docker services
```shell
docker ps -a
```

- Exit and close the container
```shell
exit
```

- Exit but container keep alive
```ctrl + p``` + ```ctrl + q```

- Run a docker container
```shell
docker run [hello-world]
```
</details>


## Docker File
<details>
<summary>view subjects</summary>

</details>