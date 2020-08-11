# sftp-docker-image
This image can alternatively be pulled from [Docker hub](https://hub.docker.com/r/imprime/sftp) 

## Overview

The image is a low memory blueprint allowing you to setup an sftp server container on your local server. The docker image is built on a lightweight Linux distro i.e [alpine 3.12](https://github.com/alpinelinux/docker-alpine/blob/90788e211ec6d5df183d79d6cb02e068b258d198/x86_64/Dockerfile) running [OpenSSH](https://www.openssh.com/).

## Motivation
In the event that you might be writing a program which requires you to send and receive files to and from an sftp server that hasn't been set up yet, this docker image provides the means to quickly setup a simulation of that server which you can use to test if your implementation works while you wait for the real server to be ready.

## Code Style
[![Dockerfile Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)

## Prerequisites

* [Docker Engine](https://docs.docker.com/engine/install/)

## How to build the image

While in the alpine folder(using the terminal), run:
```
docker image build -t <any_fancy_image_name_of_your_choice_here> . 
```

## Usage

The container runs with a default user: **foo** and the default password: **pass** which will be used to connect to the container via ssh in a terminal or via an sftp client like FileZilla. However, you can change this by modifying the line below to suit your preference. **N.B:** The format is username:password 

```
RUN echo 'foo:pass' | chpasswd
```
You can then run the container using the following command taking care to specify the local port of your  choice e.g 9990

```
docker run -d -p 9990:22 <the_fancy_image_name_you_chose_here>
```

#### Run  container with read/write permissions

You might realise that you cannot create new files on the container that you are running. To fix that you need to run the container in privileged mode so that you can have the necessary permissions to read, write and delete files in the container at will. To accomplish that run the following command specifying the port of your choice.

```
docker run -it --privileged -d -p 5050:22 <the_fancy_image_name_you_chose_here>
```

## ssh example

You can aso connect to your sftp server using the ssh command as follows: 

```
ssh foo@localhost -p 9990
```

