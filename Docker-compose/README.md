# Docker Compose
Docker Compose Tutorials and commands

We will use docker-compose to start our application.

The command up
 - Build the image for each service
 - Create and initialize containers

Docker-compose automatically starts the containers that must be started first

Containers can run in the background as a daemon (using -d flag)

The names of the created containers will have the format ``` <project> _ <service> _ <number> ```
  
Other actions you can perform: logs / start / stop / restart / pull / rm

Check original example in: github.com/platzi/platzidocker

To build docker-compose go to the file direction where is docker-compose.yml and run:
```
docker-compose build
```
To run docker-compose run this command:
```
docker-compose up
```
To run containers as daemons
```
docker-compose up -d
```
To check logs and check log of container
```
docker-compose logs
docker-compose logs web
```
To delete all containers and delete one container
```
docker-compose rm
docker-compose rm web
```
To stop and remove all containers
```
docker-compose down
```
To check help
```
docker-compose help
```
To list containers
```
docker-compose ps
```
To run containers with diferent file name
```
docker-compose -f compose.yml ps
```
To scaling services help
```
docker-compose scale --help 
```
To scale a number of containers
```
docker-compose scale web=4
```
To running load balancer and recreate
```
docker-compose up -d --force-recreate --no-debs lb	
```



