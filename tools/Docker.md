# Getting started with Docker

A docker is a containers platform which helps us to build, run, test and deploy our code faster.

##### Pulling an image
##### Start a container
##### Attaching to a running container
```docker exec -it <containerId> [program]```

##### Information about a container
```docker inspect [containerId | containerName]```


```
docker pull <name>[:tag]
docker images
docker logs [containerId | containerName]
docker container prune -f
docker run [-d] alpine ping www.google.com
docker rm 
docker stop
docker logs [--since 5s] [containerId | containerName]
docker run -d -p hostPort:containerPort nginx
docker start [containerId | containerName]
docker build 
docker build -t my-image:1.0 .

docker network ls
```