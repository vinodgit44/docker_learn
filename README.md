# Docker 

Docker is an open-source OS-level virtualization platform that allows users to develop, deploy, and run
applications in independent containers.

- Docker registries
A Docker registry is an online library that stores container images to deploy and run on Docker. 

- Container images
A container image is  template with instructions for creating a Docker container. In the Docker
container, it has everything that an app needs to run like OS ,Software, application code

- Docker containers
A Docker container is a runtime instance of an image. A Docker container runs a discrete
process independent of other containers,
```
---------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------------
```

# Docker commands

# Image
- Pulling an image from online registry.
```
docker pull {imagename:tag}

```
- list images
```
docker images 
or 
docker image ls
```
- remove image
```
docker image rm {image name}
```
 
# Container
- Running container from image 

```
docker run --name {name of container} -d {imagename}
```
- Stop container 
```
docker stop {container name}

- For stopping all containers

docker stop $(docker ps -aq)
```

- Start a stopped container 
```
docker start {container name }
```

- List container 
```
docker ls -a
or
docker ps
```

- Remove a container 
```
docker rm {container id or name }

To remove running container forcefully

docker rm {container id or name } -f 

for removing all containers

docker rm $(docker ps -aq)
```

# Port
- For exposing ports (host 8080 : container 80}

```
docker run --name {name} -d -p 8080:80 image:tag}


NOTE*we can map multiple ports by adding by adding -p host:container 
```
# Volume
Allows us to share data between host and container or between containers
- Share between host and container 

```
docker run --name {name} -d -p {host port:container port} -v {host file  path :container path:ro } image:tag

eg. docker run --name website -d -p 8080:80 -v /media/delta/data11/demo_website:/usr/share/nginx/html:ro nginx:latest
```

NOTE: for hosting beautiful single page website template https://startbootstrap.com/themes/landing-pages
- Share between containers 
```
docker run --name {name} -d -p {host port:container port} --volumes-from {container_name} image:tag

eg. docker run --name website_copy -d -p 8081:80  --volumes-from website nginx:latest
```

# Accessing container by bash command

```
docker exec it {container name} bash
```


# Dockerfile

- It is used to build own images. Dockerfile has instructions for making own image.
- We always start with some image as base then we add our files into that image 
- make a file in directory named Dockerfile and write following command.

```
FROM nginx:latest
ADD ./website /usr/share/nginx/html
```

- Build Dockerfile
```
docker build --tag {name:tag} . 
```

.represents location of Dockerfile










