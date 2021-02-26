# Docker 

* Docker benefits - smaller footprint than virtual machine.
* Using containers can reduce the number of servers required.
* Orchestrators can be used to manage multiple container.
* Orchestrators are like kubernetes or openshift.
* Docker uses overlayFS filesystem.
* Docker uses host kernel.
* Docker provides an easy way to create, store and run container images.

# Virtual Machines vs. Containers.
* Containers are used for a single process or task, while virtual machine 
 may run multiple processes or tasks.
* Container boot times are much quicker than virtual machines.
* Docker security - Docker isolates containers from each other.
* Docker containers share the kernel of the host machine.
* Docker uses cgroup and namespace feature of the kernel.

# Docker basics
* Docker uses containers to run single process or a smaller group of process
to provide a service.
* Container image is required to start a container and these images can be held 
in an online library, called an image registry.
* To create a docker image you need a Dockerfile
* A base image is a tiny but functional operating system.
* Docker uses a layered filesystem so that you can add to a base image.

# Docker Application 
* Microservices - collection of loosely coupled services.
* Each microservice can be deployed without the need to deploy the whole application.
* Docker containers are ideal for microservices.
* Containers have small footprint.


# Basic Docker Commands.

```python
#docker run -dit debian
```
# d,i, t - Options in docker

```python
d --> dettach -- in the background
i --> interactive --> stdin and stdout.
t --> pseudo tty i.e. pseudo terminal associated with it.
```
# To show how many containers are running?

```python
#docker ps 

```
# Stop the docker using name

```python
#docker stop bea<tab>
```
# What images have been downloaded by a docker?

```python
#docker images
```
# How to inspect the docker images?

```python
#docker inspect <hash>
```
# how to see help in docker?

```python
#docker --help
#docker images --help
#docker image prune --help
```
# Container images

```python
#docker pull nginx
#docker images
#docker history nginx
#docker images --no-trunc
```
# Docker images tag 
```python
#docker images tag 
#docker tag --help
```
# Docker commands
```python

COPY - local to /var/www/html
EXPOSE 80 -> expose the TCP port number 80 i.e. http port number
CMD to run
RUN 
```
# Build the docker file
```python

#docker build -t mynginx
```
# Run the docker 
```python

#docker run -dit mynginx
#docker history mynginx
#docker images
#docker rmi <image name>
```
# Clean docker images

```python
#docker rmi -f <name of image>
#docker rmi --help

Dangling images.

#docker image prune

Remove both unused and dangling images
#docker system prune -a
```
# Check the docker occupied space.

```python

#docker system df
```

# Managing Container Images.
```python
#docker pull nginx
#docker images
#docker history nginx
#docker images --no-trunc
#docker images tag -> specific tag i.e. specific commit.
#docker tag --help
#docker tag nginx:latest nginx:myblog_stable
```
# Running the docker image
```python
#docker run -dit mynginx
#docker history mynginx
#docker images
```
# Deleteing the docker image 

```python

#docker rmi nginx:latest
#docker rm -f <name of image>
#docker rmi --help
#docker system prun -a # remove both unused and dangling images.
```
# How much disk space is used by docker?
``` python
#docker system df

```
# Docker running containers

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
# Restart the docker by its own.

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
# How to delete the container when exited.

``` python
#docker run --rm hello-world
#docker ps -a
```
# How to see the logs of the running docker container?


``` python

#docker logs -t <SHA> --> This shows logging with timestamp that's why -t is used.
#docker logs -f <container name>

ctrl +c --> to exit from viewing the logging.

#docker logs -tf <container name> 
```
# Searching the docker images from terminal


``` python

#docker pull jenkins/jenkins:lts
#docker search --help
#docker search --limit 5 apache --> this will ensure the search results are limited to 5 only.
#docker pull httpd:2-alpine 
#docker images
#docker system df 
#docker rmi <sha of jenkins> <sha of apache>
```
# Making containers available public


``` python

#docker run --name our_nginx -d -p 8080:80 nginx

8080 --> outside world i.e. the port exposed by the host machine.
80 --> inside port i.e. port in the docker container.

#docker ps 
# curl http://localhost:8080
```

# Using volume i.e. -v command


``` python

#mkdir webPages
#cd WebPages
#echo 'Hi from inside the container!' > index.html
-v -> volume for sharing files.
#cd ..
#docker run -p 8080:80 --name another_nginx -v ${PWD}/webPages:/user/h/nginxhtml:ro -d nginx
```
