QuickRef
docker build -t docker-java .
docker run. EX: docker run -p 27017:27017 -d  mongo
     [-d (detached) | -it (interactive)]
     [--name web]
     [-p 80(external):8080(container)] <docker-image>[:<version>]  (will pull if needed)
     [/bin/bash] (starts container and runs bash) CTL-P,Q exit w/o shutting down
     [-v /my/own/datadir:/data/db]. <== Way to store local data
docker ps (see running and stopped) [-a]
docker images (see images) { -q —no-trunc}
docker history <image> gives history/layers
docker image pull
docker run -it ubuntu. (Download and run, then Interactive Terminal )    
docker logs -f 01442b77cc07

docker start <container>
docker stop <container> | $(docker ps -aq) <== stops all docker containers running

docker rm <container> | $(docker ps -aq) <== removes all docker containers running
docker rmi <images> | $(docker ps -aq) <== removes all docker containers running
docker info

Docker Container:
docker container run alpine app add —no-cache python
docker container ls -l —format ‘table {{.ID}}\t{{Image}}\t{{.Command}}’
docker container ls -l —format \
   ‘table {{.Repository}}\t{{Tag}}\t{{.ID}}\t{{.Size}}\t{{Image}}\t{{.Command}}’ 
docker container commit -m “Add Python” <image id> my-image:1.0

LOGIN DOCKER REPOSITORY
docker login -u svc4riotest1  https://stlpartifact01.rgare.net:4443
docker login -u "$DEPLOY_USER" -p "$DOCKER_PASSWORD" stlpartifact01.rgare.net:4443

docker pull stlpartifact01.rgare.net:4443/claims-services:hash-deployment-proj
docker inspect stlpartifact01.rgare.net:4443/claims-services:hash-deployment-proj

Swarm
Engine port: 2375
Secure Engine port: 2376
Warm port: 2377
cluster = swarm
Manager nodes maintain swarm. * recommend 3 or 5, Raft Consensus Algorithm: Distributed State Store

?? docker service create -name web-fe --replicas 5 ...
docker swarm init --advertise-addr xxx.xx.xx.xx:2377 --listen-addr xxx.xx.xx.xx:2377 
docker swarm join-token manager
docker swarm join ...
docker node ls <== only run on docker manager
docker node promote <id>
docker service <create | ls | ps | inspect | update | rm>
docker service scale psight1=7 (scale the running containers to 7) >> Short cut to: docker service update -- replicas= 10 psight1
docker service inspect --pretty psight2   

docker service create --update-parallelism 2 --update-delay 10m
docker service update -image nigelpoulton/tu-demo:v2 --update-parallelism 2 --update-delay 10s
docker service ps psight2 | grep :v2
sudo docker service ls

Clear Containers
sudo docker service scale acf-claims-perf_acfServices=0
sudo docker service scale 4blsfko9be0k=3

Kubernetes

Install on Ubuntu
wget -q0- https://get.docker.com/ | sh
real world: sudo usermod -aG docker vagrant OR sudo usermod -aG docker your-user

Websites:
https://hub.docker.com 
https://get.docker.com/


SHELLING INTO CONTAINER
docker exec -it <container name> sh
Ip -a

HOUSEKEEPING
docker kill $(docker ps -q). <== Kill all running docker containers
docker rm $(docker ps -a -q) <== Delete all Stopped Docker Containers
docker rmi $(docker images -q -f dangling=true)  <== Delete untagged (dangling images)
docker rmi ($docker images -q).  <== Delete all Images
docker volume rm $(docker volume ls -f dangling=true -q). <== remove all dangling volumes
    Does not remove files from host system in shared volumes

EXAMPLES
docker run -d --hostname guru-rabbit --name some-rabbit -p 8080:15672 -p 5671:5671 -p 5672:5672 rabbitmq:3-management
docker run -d centos tail -f /dev/null. <== Start and run CentOS keep up as it runs a command.
docker exec -it <container name> bash
docker exec -it <container name> sh
