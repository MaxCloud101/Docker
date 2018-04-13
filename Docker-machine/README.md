# Docker-machine
Docker-machine Tutorials and commands

Docker machine is a tool to provision Docker hosts and configure the engine in them.

Using the docker-machine command and specify the driver to use.

```
docker-machine create --driver <driver> <hostname>
```

In amazon ec2

```
docker-machine create --driver amazonec2 
	--amazonec2-access-key <AWS access key>
	--amazonec2-secret-key <AWS secret key>
	--amazonec2-vpc-id <VPC ID> testhost
```

To check docker-machine version

```
docker-machine version
```

To run and configure docker in virtual machine using virtualbox

```
docker-machine create -d virtualbox dockervirtual
```

To remove virtual machine

```
docker-machine rm dockervirtual
```

To get information about of virtual machine

```
docker-machine inspect dockervirtual 
```

To access to this virtual machine

```
docker-machine ssh dockervirtual
```

To connect the client of your host with the daemon of virtual machine

```
docker-machine config dockervirtual
docker $(docker-machine config dockervirtual) ps
```

For populating enviroment variables (For connect with daemon in other host)

```
docker-machine env dockervirtual
eval $(docker-machine env dockervirtual)
```

To check enviroment variables use ``` env |grep DOCKER ```

To restore enviroment variables

```
eval $(docker-machine env -u)
```

The keys are in ~/.docker/machine/machines/dockervirtual

To enter ussing ssh

```
docker-machine ip dockervirtual # return the ip of dockervirtual 
ssh -i ~/.docker/machine/machines/dockervirtual/id_rsa  docker@ip_dockervirtual
```





