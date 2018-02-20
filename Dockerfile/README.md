# Dockerfile
Dockerfile Tutorials and commands

## Building images
To build an image you must use the following command
```
Docker build -t image_name .
```
To rebuild an image ignoring other images
```
Docker build --no-cache -t image_name .
```
To check history of an image
```
Docker history image_name
```

## Dockerfile components

### CMD
This command will be executed when the container is started (User format Shell or Exec (Json array) ). Example:
```
FROM ubuntu
CMD ping -c 2 www.google.com
CMD ["ping","-c","2","www.google.com"]
```
### ENTRYPOINT 
This is for interactive command in the moment of throw a container. Example:
```
FROM ubuntu
ENTRYPOINT ["ping"]
```
To create this image and run the container we will use the following commands
```
docker build -t image_name
```
```
docker run image_name -c 2 www.google.com
```
We can mixed this commands. Example:
```
FROM ubuntu
CMD ["-c","2","www.google.com"]
ENTRYPOINT ["ping"]
```
### COPY
Copy files from our host to the container
```
FROM ubuntu
COPY source/path destination/path
```

### EXPOSE
Expose the ports of the container
```
FROM ubuntu
EXPOSE 5000
```
To run this image we use the follow commands:
```
docker run -d -P image_name
```
Using flag -d as a daemon and flag -P to expose a port.

### WORKDIR
Specify a work environment, the commands are executed on this directory
```
FROM ubuntu
WORKDIR /path
```

### ADD

get files from a url or decompress tar files into container

```
FROM ubuntu
ADD http://cdn.meme.am/instances/66627195.jpg /tmp/img.jpg
```

### ENV
To indicate environment variables
```
FROM ubuntu
ENV TERM xterm-256color
```

### LABEL
To tag container
```
FROM ubuntu
LABEL key value
```

### Upload to DockerHub
Tag the image withe dockerhub_username/image_name
```
docker tag add username/image_name
```
Pushe the image in DockerHub
```
docker push username/image_name
```
