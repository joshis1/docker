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
