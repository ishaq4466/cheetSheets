# Docker Cheetsheet 

## Cmds related to CONTAINERS AND IMAGES
```
docker ps -a
docker ps -q -n 1 # getting the first container id
docker run -p 4000:80 -d hello-node:1.0
mapping pod 4000 of local host with port 80 of container 
-d: run container in background

docker run -p 4001:80 -d --name container2 $IMG_NAME

docker log -f container1

docker rmi -f image-name

docker image inspect <image-name>

docker ps -q (Running containers id)

docker rm -f $(docker ps -a -q)
docker rmi -f $(docker images -q)

docker inspect $INSTANCE_ID # return a low level description of docker object



docker start centos1
docker ps
docker exec -it centos2 /bin/bash

docker commit --autor smatbuddy --message my-custome <container-name> <image-name>
docker tag <image-name> <tag-name>
# for custom-centos7:1.2 image
docker run -idt -v /sys/fs/cgroup:/sys/fs/cgroup:ro --cap-add SYS_ADMIN --name centos1 smartbuddy/custom-centos7:1.2
#remove /var/run/nologin file for ssh 

# Creating a replication of a container
docker commit container_name newimgname # Will craete snapshot
docker run container_name newimg


```

## Cmds related to STACKS and SERVICE

```
docker swarm init 
docker stack deploy -c docker-compose.yml getstartedlab<stack name>
docker stack ls
docker stack rm getstarted<stackname>
docker stack logs <stackname> -->Getting the logs for a particular stack

docker service ls
docker service logs serviceName<getstarted_web>
docker service ps <service-name> -->shows the task for one or more service

docker swarm leave --force

```

## Cmds for SWARM 
```
docker-machine create --driver virtualbox myvm1
docker-machine ls
docker swarm init 
docker node ls
docker stack deploy -c docker-compose.yaml stack1
docker stack ls
docker swarm leave --force
```

### Getting the instance IP addr 
```
$ docker inspect --format='{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' $INSTANCE_ID
```

### List all the binding ports
```
$ docker inspect --format='{{range $p, $conf := .NetworkSettings.Ports}} {{$p}} -> {{(index $conf 0).HostPort}} {{end}}' $INSTANCE_ID
```


