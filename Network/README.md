# Docker Network
Docker Network Tutorials and commands

# Docker Introduction

Run application in random port

```
docker run -d -P app
```
The command ``` docker network ``` it allows us to interact with docker network and containers inside. The subcommands are:

```
docker network create
docker network connect
docker network ls
docker network rm
docker network disconnect
docker netwoek inspect
```

Use the flag ```--net``` to specify a network when a container is created

Use the flag ```--link``` to connect with other containers by name

Docker0 is the network interface created by Dockerin your host machine, to check network interfaces use ```ip a```

If you run ```docker network ls``` you will see the list of networks, where will you have: 

1 bridge: connects the interfaces of the containers with the local machine, is the default network when you create a container

``` docker run -it ubuntu bash ```

2 host: to share the network with the local machine

``` docker run -it --net=host ubuntu bash ```

You can create two types of networks

- Bridge: Equal to the network docker0 (the network used by default in Docker)

- Overlay: Allows to display containers in different physical hosts and that they communicate directly

To create a network

```docker network create --driver=bridge mi_red ```

The following containers are created by default in the bridge network that exists by default

```
docker run -it --name redis ubuntu bash

docker run -it --link redis ubuntu bash
```

After creating the second container I could ping with the name: ping redis

In / etc / hosts, are the ips of the containers associated with the bridge network, only works in the default network

For other networks docker uses an internal DNS in /etc/resolv.conf

To run containers in the new network

```
docker run -it --name redis --net=mi_red ubuntu bash

docker run -it --link redis --net=mi_red ubuntu bash
```
You can have isolated networks and could connect a container to two networks. As in the following example

```
docker run -it --name container1 ubuntu bash # red default

docker run -it --name container3 --net=mi_red ubuntu bash # red mi_red

docker run -it --name container2 --net=mi_red ubuntu bash # red with both networks

docker network connect bridge container2
```

To see the containers in the networks

```
docker network inspect bridge

docker network inspect mi_red
```

To run app and expose containers to an external network

```
docker run -d --name redis redis
docker run -d -P 80:5000 --link redis app
```
