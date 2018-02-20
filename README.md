# Docker
Docker Tutorials and commands


## Installation script
```
get.docker.com
```
Enable our user to use docker
```
sudo usermod -aG docker ubuntu
```
Check correct installation
```
docker info
```
```
docker version
```

## Pull images
```
docker pull ubuntu
```
Pull image with tag
```
docker pull ubuntu:14.04
```

## Show images

```
docker images
```

## Show containers
```
docker ps
```
Show all containers 
```
docker ps -a
```
Show all containers with full id
```
docker ps -a --no-trunc
```
Filter containers 
```
docker ps -a --filter="exited=0"
```
Show containers ids only
```
docker ps -a -q 
```

## Run containers
```
docker run ubuntu
```
```
docker run ubuntu echo "hola max"
```
```
docker run ubuntu ps -efa
```
Run with interactive bash session
```
docker run -it ubuntu bash
```
Note: Exit from interactive session without stop container CTRL + PQ

Run container assign a name
```
docker run --name marcos ubuntu
```
Run container as daemon
```
docker run -d ubuntu ping -c 10 www.google.com
```

## Remove containers
```
docker rm marcos
```
Remove all containers
```
docker rm $(docker ps -a -q)
```
Remove container in execution
```
docker rm -f container_id
```

## Start, Stop, Pause, Kill, Attach, Exec
To restart container
```
docker start container_id
```
To restart and attach to caontainer
```
docker start -a container_id
```
To stop container
```
docker stop container_id
```
To pause container
```
docker pause container_id
```
To unpause container
```
docker unpause container_id
```
To kill running container
```
docker kill marcos
```
To return a running container of where get out with CTRL + PQ
```
docker attach container_id
```
To enter a container as a second door
```
docker exec -ti b916 basg
```

## Inspect containers
```
docker inspect container_id
```
```
docker inspect container_id | grep MacAddress
```

## Show logs
Check logs from container
```
docker logs container_id
```
Check logs from container in real time
```
docker logs -f container_id
``` 

## Example
To run Tomcat
```
docker run -P -d tomcat
```

## Create image
1 Create image from commit in the containers

2 Crea image from Dockerfile

3 Import Tar file to Docker with the image

## Create image from commit

Check changes in container
```
docker diff container_id
```
Create image from commit
```
docker commit container_id image_name
```

# Docker volumes

List volumes
```
docker volume ls
```
List volumes ids
```
docker volume ls -q
```
Create a volume
```
docker volume create --name volumen_name
```
Run container ataching the volume (volumen name:volumen path in container)
```
docker run -ti -v volumen_name:/volumen_path ubuntu bash
```
Inspect volume
```
docker volume inspect volumen_name
```
Remove volumen
```
delete volume rm volume_name
```
Run container with volume in absolute path
```
docker run -ti -v /home/max/ubuntu:/prueba ubuntu bash
