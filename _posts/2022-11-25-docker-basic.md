---
title: "Docker Basics"
date: 2022-11-25
categories:
  - tool
  - devops
  - docker
classes: wide
excerpt: This blog keep note basic use cases of docker.
---

All the information written here for `linux` based operating system specially `ubuntu`

## Installation
- Ubuntu default

```
sudo apt install docker.io
```
- Latest docker

```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

- run docker without sudo

```
sudo usermod -aG docker $USER
# logout and login again
```

## Basic commands
- list docker images

```
sudo docker images
```

- remove a docker images

```
# one image
docker image rm image_name/image_id
# multiple image
docker image rm [image_id, image_id]
```

- run a docker image

```
docker run image_name/image_id
```

- list all docker running container

```
docker container ls 
```

- kill a running docker container

```
docker container kill container_id
```

- pull a docker image

you can pull any docker image from [docker hub](https://hub.docker.com/) or docker file. You will several builtin docker image docker hub according to your need.

```
# pull ubuntu from hub

docker pull ubuntu

# it will pull latest ubuntu from hub
```

- run docker with terminal

```
docker run -it image_id bash
```

- run docker with mounting local path

```
# runnning pytorch container with mounting local path

docker run --runtime=nvidia --rm -v /home/sagor/demo/:/home/sagor -it pytorch/pytorch:1.7.0-cuda11.0-cudnn8-devel  bash
```
