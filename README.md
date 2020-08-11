# sftp-docker-image
This image can alternatively be pulled from [Docker hub](https://hub.docker.com/r/imprime/sftp) 

## Overview

The image is a low memory blueprint allowing you to setup an sftp server container on your local server. The docker image is built on a lightweight Linux distro i.e **alpine 3.12** running **OpenSSH**.

## How to build the image

While in the alpine folder(using the terminal), run:
```
docker image build -t <any_fancy_image_name_of_your_choice_here> . 
```

## Usage 
The container runs with a default user: **foo** and the default password: **pass** will be used to connect to the container via ssh in a terminal or via an sftp client like FileZilla.

```
docker run -d -p 9990:22 <the_fancy_image_name_you_chose_here>
```

#### Run  container with read/write permissions

```
docker run -it --privileged -d -p 5050:22 <the_fancy_image_name_you_chose_here>
```

## ssh example

`ssh foo@localhost -p 9990`

