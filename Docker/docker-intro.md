# Docker

## Docker Flow

1. Image -> file that contains just the bare minimum operating system
2. Running Container
3. Stopped Container -> container exists, but process exited

## Docker Commands

```docker run -ti <image-name> <command (bash)>```
--rm remove container upon completion
-d start container and leave it running the background
-t terminal
-i interactive
turn an image into a running container

---

```docker ps -al (--format $FORMAT)```
-a all containers
-l last-run container
--format changes the output text format
look at running images 

---

```docker commit <container> <new-image-name>```
creates an image from a container

---

```docker rmi <image-name>```
remove an image from your computer

---

```docker tag <image-name> <new-image-name>```
change the name of a docker image

---

```docker images```
list all docker images on your computer

---

```docker attach <container-name>```
attach to a detached container

---

```ctrl-p ctrl-q```
detach from current container but leave it running

---

```docker exec -ti```
run a process in a container that is already running

---

```docker logs <container-name>```
check what the output from a running container is

---

```docker kill <container-name>```
stop a running container

```docker rm <container-name>```
removing containers

---

## Docker Networking

```docker run -p 1200:1200 --name <custom-name>```
-p port
--name give the container a custom name
exposes port 1200 from container to port 1200 to host

---

```host.docker.internal```
ip address of host computer within a container

--- 

```docker port <container-name>```
checks which ports are open on a container

---

```docker network ls```
check all docker networks

---

```docker network create <network-name>```
create a new network

---

```docker run -rm -ti --net <network-name> --name <container-name>```
starts a new container and connect it to a network

---

```docker network connect  <network-name> <container-name>```
connect a container to a network

### Legacy Linking
One way connections between servers (hostee can connect, but host cannot), all environment variables of the host are shared

```docker run -e <env-var>=<env-value> --link <container-to-link>```
runs a container that is linked to another container

### Volumes

1. persistent: exist between the host and the container

```docker run -v <host-path>:<location-path-on-container> <image> <command>```
create a persistent volume

2. ephemeral volumes: only exist between containers

```docker run -v <container-volume> <image> <command>```
creates a volume only in a container

---

```docker run --volumes-from <container-from> <image> <command>```
connects to a volume within a container

## Dockerfiles
small programs that describe how to build a docker image
* each line takes an image from the previous line and creates a new image
  
EXAMPLE:
```
FROM alpine
RUN echo "building a new image"
CMD echo "created a new container"
```

```docker build -t <image-name> <dockerfile-location>```
building from a dockerfile

FROM: what image you start running from (should be the first statement)
```FROM ubuntu```

---

MAINTAINER: who is the author of the file
```MAINTAINER first-name last-name email```

---

RUN: runs the command line, waits for it to finish, and saves the result
```RUN unzip install.zip /install/```

---

ADD: adds local files, will auto compress zipped files

```ADD run.sh /run.sh```
```ADD project.tar.gz /here/``` 

---

ENV: sets environment variables
```ENV DB_LINK=123.342.123.2```
```ENV DB_PORT=1200```

---

ENTRYPOINT: specifies the start of the command to run (you can add arguments to ls for example)
```ENTRYPOINT ls```

---

CMD: whole command to run, can be replaced if someone adds a custom command to docker run after image name
```CMD echo "hello"```

---

EXPOSE: what ports to expose, same as -p 1200:1200
```EXPOSE 8080```

---

VOLUME: defines shared volumes, avoid using persistent folders due to local computer dependency
1. persistent (host)
    ```VOLUME ["/shared-data" "/container/path"]```
2. ephemeral 
    ```VOLUME ["/shared-data"]```

---

WORKDIR: sets the directory the container starts in
```WORKDIR /install/```

---

USER: which user is running the container

```USER arthur```
```USER 1000```

---

Shell vs. Exec for commands
1. shell
    nano test.txt

2. exec -> command, parameter -> apparently faster 
    ["bin/nano", "test.txt"] 
