# Docker 

* Docker benefits - smaller footprint than virtual machine.
* Using containers can reduce the number of servers required.
* Orchestrators can be used to manage multiple container.
* Orchestrators are like kubernetes or openshift.
* Docker uses overlayFS filesystem.
* Docker uses host kernel.
* Docker provides an easy way to create, store and run container images.

## Virtual Machines vs. Containers.
* Containers are used for a single process or task, while virtual machine 
 may run multiple processes or tasks.
* Container boot times are much quicker than virtual machines.
* Docker security - Docker isolates containers from each other.
* Docker containers share the kernel of the host machine.
* Docker uses cgroup and namespace feature of the kernel.

## Docker basics
* Docker uses containers to run single process or a smaller group of process
to provide a service.
* Container image is required to start a container and these images can be held 
in an online library, called an image registry.
* To create a docker image you need a Dockerfile
* A base image is a tiny but functional operating system.
* Docker uses a layered filesystem so that you can add to a base image.

## Docker Application 
* Microservices - collection of loosely coupled services.
* Each microservice can be deployed without the need to deploy the whole application.
* Docker containers are ideal for microservices.
* Containers have small footprint.


## Basic Docker Commands.

```python
#docker run -dit debian
```
# d,i, t - Options in docker

```python
d --> dettach -- in the background
i --> interactive --> stdin and stdout.
t --> pseudo tty i.e. pseudo terminal associated with it.
```
## To show how many containers are running?

```python
#docker ps 

```
## Stop the docker using name

```python
#docker stop bea<tab>
```
## What images have been downloaded by a docker?

```python
#docker images
```
## How to inspect the docker images?

```python
#docker inspect <hash>
```
# how to see help in docker?

```python
#docker --help
#docker images --help
#docker image prune --help
```
## Container images

```python
#docker pull nginx
#docker images
#docker history nginx
#docker images --no-trunc
```
## Docker images tag 
```python
#docker images tag 
#docker tag --help
```
## Docker commands
```python

COPY - local to /var/www/html
EXPOSE 80 -> expose the TCP port number 80 i.e. http port number
CMD to run
RUN 
```
## Build the docker file
```python

#docker build -t mynginx
```
## Run the docker 
```python

#docker run -dit mynginx
#docker history mynginx
#docker images
#docker rmi <image name>
```
## Clean docker images

```python
#docker rmi -f <name of image>
#docker rmi --help

Dangling images.

#docker image prune

Remove both unused and dangling images
#docker system prune -a
```
## Check the docker occupied space.

```python

#docker system df
```

## Managing Container Images.
```python
#docker pull nginx
#docker images
#docker history nginx
#docker images --no-trunc
#docker images tag -> specific tag i.e. specific commit.
#docker tag --help
#docker tag nginx:latest nginx:myblog_stable
```
## Running the docker image
```python
#docker run -dit mynginx
#docker history mynginx
#docker images
```
## Deleteing the docker image 

```python

#docker rmi nginx:latest
#docker rm -f <name of image>
#docker rmi --help
#docker system prun -a # remove both unused and dangling images.
```
## How much disk space is used by docker?
``` python
#docker system df

```
## Docker running containers

``` python

#docker run -dit <image>

#docker run -dit --name=web debian --> giving name to the container.
#docker ps --> check running containers
#docker ps -l -> check latest container.
#docker stop web 
#docker rm web 
#docker ps -a
#docker start web
#docker stop web
```
## Restart the docker by its own.

``` python

#docker run -dit --restart=always --name mycontainer redis 
#docker inspect mycontainer | grep -A3 restartPolicy
#docker run --help | less
#docker stop mycontainer
#docker ps
#docker kill mycontainer
#docker system prune
#docker ps -a

```
## How to delete the container when exited.

``` python
#docker run --rm hello-world
#docker ps -a
```
## How to see the logs of the running docker container?


``` python

#docker logs -t <SHA> --> This shows logging with timestamp that's why -t is used.
#docker logs -f <container name>

ctrl +c --> to exit from viewing the logging.

#docker logs -tf <container name> 
```
## Searching the docker images from terminal


``` python

#docker pull jenkins/jenkins:lts
#docker search --help
#docker search --limit 5 apache --> this will ensure the search results are limited to 5 only.
#docker pull httpd:2-alpine 
#docker images
#docker system df 
#docker rmi <sha of jenkins> <sha of apache>
```
## Making containers available public


``` python

#docker run --name our_nginx -d -p 8080:80 nginx

8080 --> outside world i.e. the port exposed by the host machine.
80 --> inside port i.e. port in the docker container.

#docker ps 
# curl http://localhost:8080
```

## Using volume i.e. -v command


``` python

#mkdir webPages
#cd WebPages
#echo 'Hi from inside the container!' > index.html
-v -> volume for sharing files.
#cd ..
#docker run -p 8080:80 --name another_nginx -v ${PWD}/webPages:/user/h/nginxhtml:ro -d nginx
```
## Entering into the container by running the container in the foreground.

In order to run the container in the foreground, don't pass the option -d i.e. dettach mode. If we 
don't run in the dettach mode then the container will run in the foreground.

## exec command 

``` python 

#docker run -it --name apache httpd /bin/bash
#docker ps
```
## Connecting to the existing running container i.e. in the dettached mode - most useful.

``` python 

#docker run -dit --name second_apache httpd /bin/bash
#docker ps 

#docker exec -it <container_id> /bin/bash
# exit

#docker run -dit --name execution httpd
#docker exec -d execution touch /root/hello
#docker exec -it execution bash
#docker exec -it execution ls /root
#docker exec -it execution bash 
```
## How to see the running processes inside the docker?

``` python
#docker top <container id/name>
```
## Docker logging 
``` python
#docker run -dit --name busylogs -p 8080:8080 -p 50000:50000 jenkins/jenkins:lts
Here first jenkins is the userid i.e. jenkins 
next jenkins is the image name i.e. jenkins
lts is the long term support.
#docker logs busylogs
#docker logs -t busylogs --> to see the logs with time stamp
#docker logs -f busylogs --> to see the upcoming logs i.e just like tail -f /var/log/messages
#docker logs -tf busylogs --> timestamp as well as log tailing.
```
## Checking it.

Open the web-browser go to http:<IP Address>:8080/login. You will see the Jenkins login page.
When you have seen the above docker logs, it will display the random password assigned to this 
jenkins machine. Use the password obtained from the docker logs to login in the Jenkins machine.

``` python
#docker logs -t --since 2011-11-11 busylogs
#grep -i docker /var/log/syslog
#journalctl -n 25
#journalctl --no-pager -u docker.service -n 25
```
## Registries in Docker 
Docker hub is the default registery. Registries store images. A repository is a collection 
of images. Each image is stored as a tag. 

## Building docker images with Dockerfiles

``` python
FROM  -- sets the base iamge.
CMD   -- Sets the command to be executed when running the image. It can also be used to set 
the default arguments to the ENTRYPOINT instruction.
RUN - Executes a command to help build your image.
EXPOSE - Opens up networking ports.
VOLUME - Sets a disk share.
COPY - Copies files into your image from the local disk.
LABEL - Adds metadata to an image in a key-value pair format. 
ENV - Sets an environment.
ENTRYPOINT - Determines which executable runs when the container starts.
Use CMD to pass options to the executable.
```
## Docker file example

``` python
FROM debian:latest
LABEL maintainer="Shreyas Joshi"
ENTRYPOINT ["/bin/ping"]
CMD ["www.docker.com"]
```
## Build the docker image 

``` python
#docker build -t shreyasjoshi15/dockerping:latest <path to dockerfile>
```
## Push your docker image to docker hub

``` python

#docker login
#docker push shreyasjoshi15/dockerping:latest
#docker run shreyasjoshi15/dockerping:latest 
#docker run shreyasjoshi15/dockerping google.com
```
## Override the dockerfile name using -f

``` python
#docker build -t shreyasjoshi15/dockerping -f <dockerfileName>
```

## Docker volumes
Images are small, portable and disposable. We add only the packages that are required to provide the
intended service in the image. It's best to be able to discard a container without worrying 
about losing important data. To persist or save data generated by the container, use a volume.
Also, volume can be shared between multiple containers.

``` python

#docker volume --help
create
inspect
ls 
prune
rm

#docker volume ls 
#docker volume inspect <volumeName>
#docker volume create <volumeName>

```
## Docker volume example

``` python
#docker volume create localvolume
#docker volume inspect localvolume
echo "This file exists" > /var/lib/docker/volumes/localvolume/_data/file.txt
#docker run -d --name mountvolume --mount src=localvolume,dst=/data httpd
The abbreviation of source("src") and destination("dst") was used. Also, you can use
target instead of destination.

Attach to the "mountvolume" container.
#docker exect -it mountvolume /bin/bash
#df -h 
#cat /data/file.txt 

```
## Run a container with an Ephemeral Volume

``` python 

#docker run -d --name tempvolume --mount type=tmpfs,dst=/tmpdata httpd
#docker inspect tempvolume | grep Mounts -A 10
```
