# docker

- [docker](#docker)
  - [list active containers](#list-active-containers)
  - [list all containers](#list-all-containers)
  - [interactive](#interactive)
  - [delete / delete force container](#delete--delete-force-container)
  - [bind mounts](#bind-mounts)
    - [risks](#risks)
    - [example with mongo](#example-with-mongo)
  - [create volumen](#create-volumen)
  - [listing volumens](#listing-volumens)
  - [mount volume (recommended)](#mount-volume-recommended)
  - [inspect all features of a container](#inspect-all-features-of-a-container)
  - [insert file in a container](#insert-file-in-a-container)
    - [create a file in a host machine](#create-a-file-in-a-host-machine)
    - [create a container](#create-a-container)
    - [enter to container and create a directory](#enter-to-container-and-create-a-directory)
    - [copy file with docker](#copy-file-with-docker)
    - [verifying the file](#verifying-the-file)
  - [extract directory from a container](#extract-directory-from-a-container)
  - [tmpfs : temporal filesystem](#tmpfs--temporal-filesystem)
  - [images](#images)
    - [listing images](#listing-images)
    - [download image](#download-image)
    - [delete/forced delete image](#deleteforced-delete-image)
    - [building an image](#building-an-image)
      - [create a custom image](#create-a-custom-image)
      - [run container](#run-container)
      - [login dockerhub](#login-dockerhub)
      - [verify login (if there are something, you are login)](#verify-login-if-there-are-something-you-are-login)
      - [retag a image to upload to repository](#retag-a-image-to-upload-to-repository)
      - [upload an image](#upload-an-image)
  - [network](#network)
    - [listing networks](#listing-networks)
    - [create network](#create-network)
    - [inspect](#inspect)
    - [add container to network](#add-container-to-network)


## list active containers
```docker ps```

## list all containers
```docker ps -a```

## interactive
i: interactive
t: open terminal

```docker -it <name of container>```

```docker exec -it <name of container> bash```

## delete / delete force container
```docker rm <name of container>```

```docker rm -f <name of container>```

## bind mounts
```docker run -d --name <name to container> -v <path in my machine>:<path dest> <name of container>```

### risks
Provide access to a portion of the host machine's disk.

### example with mongo
```docker run -d name db -v <path in my machine>:/data/db mongo```

## create volumen
```docker volume create <name of volume>```

## listing volumens
```docker volume ls```

## mount volume (recommended)
Asign a volume previously created of my host SO to a mongo container

```docker run -d --name db --mount src=<name of volume>,dst=/data/db mongo```

## inspect all features of a container
```docker inspect <name of container>```

## insert file in a container

### create a file in a host machine
```touch test.txt```

### create a container
```docker run -d --name copytest ubuntu tail -f /dev/null```

### enter to container and create a directory
```docker exec -it copytest bash```

```:/# mkdir testing```

```:/# exit```

### copy file with docker
```docker cp <name of file> <name of container>:<dest path>```

```docker cp prueba.txt copytest:/testing/test.txt```

### verifying the file
```docker exec -it copytest bash```

```:/# cd testing```

```:/# ll```

```:/# exit```

## extract directory from a container
It is not necessary that the container is running to execute ```docker copy```

```docker cp <name of container>:<path of directory> <name of new dest directory in my host>```

## tmpfs : temporal filesystem
They are used when we don't need persist data, it is located in memory and docker guarantees us that when the container dies, it will also disappear completely with all files inside.

## images

### listing images
```docker image ls```

### download image 
```docker pull <name or tag of image from hub.docker.com>```

### delete/forced delete image
```docker image rm <id of image>```

```docker image rm -f <id of image>```

### building an image

#### create a custom image
```docker build -t <base image>:<tag image name> <Dockerfile context>```

```docker -t ubuntu:my_image .```

#### run container
```docker run -it <image>:<image tag> <command>```

```docker run -it ubuntu:test bash```

#### login dockerhub
```docker login -u <username> -p <password>```

#### verify login (if there are something, you are login)
```cat ~/.docker/config.json```

#### retag a image to upload to repository
```docker tag <image>:<tag> <username>/<image>:<tag>```

```docker tag ubuntu:myubuntutag jagch/ubuntu:myubuntutag```

#### upload an image
```docker push <username>/<image>:<tag>```

## network

### listing networks
```docker network ls```

### create network
```docker network create --atachable mynet```

### inspect
```docker inspect mynet```

### add container to network
```docker run -d -name mydb mongo```

```docker network connect mynet mydb```











