
### Set up our Docker container
- To create a docker container we need a docker image.

#### how do we get this docker image?
1. From the docker hub
 - docker hub is a public repository which contains the docker images.We can use a command ```docker pull ``` to take the image onto our local system.
2. Creating our own docker file.
 - we are going to pull the basic image from the docker hub itself and top of that one we can do our own customization with the help of docker file.
 - Docker file contains instructions what your docker container should get.To create a docker image out of docker file we are going to use ```docker build``` command.

### To pull the docker image from the docker hub
- visit hub.docker.com
- to pull a docker image you don't need an account. If you wish to push or keep your docker images onto docker hub we should have an account.
- I would like to deploy my application on tomcat container
- search for tomcat
- I need to pull this image onto my local system then I can create a container out of it.
- to pull this one onto my local system I can use command

```sh
docker pull 
```

- whenever we are pulling our image we need to add a tag. If we don't add any tag by default it is going to take with the latest
```sh
docker pull tomcat
```
- Whenever we execute this command it is going to pull the image onto our local system.
- there are different layers on our images because a image is created with multiple layers based on how many times we are updating it 

- check my images
```sh
docker images
```

- We need to create a container out of it to create a container we should run
```sh 
docker run
```
-  -d stands for detached mode, -name for name of the container, -p for port number by default tomcat runs onport number 8080
- Container runs inside a docker host right. So it will be accessible only inside the docker host. If we want to access it outside of the docker host then we need to map it to the external port. So the external port I can use 8080 itself or else 8081 to avoid the confusion. (What does it mean that internally tomcat is running on port number 8080 but externally
I am exposing it to external network on port number 8081)

```sh
docker run -d --name tomcat-container -p 8081:8080 tomcat
```
- to see what all docker containers are there
```sh
docker ps-a
```
- let's go and try to access it to access this container outside of the network. 
- we need to open 8081 as well
-  I could able to access it from the browser but my request is not reaching properly that is the reason we are getting HTTPS status 404 error which represents that it could not able to find the page which we are requesting however we have successfully reached to our Tomcat server that is the reason it is showing Tomcat this is a known issue

#### to solve error
- login to docker container with help of /bin/bash

```sh
docker exec -it tomcat-container /bin/bash
```
- you will go inside /usr/local/tomcat directory into docker container
- whenever we try to access tomcat from the browser, it will lookinto application in the webapps directory, but if you go inside webapps directory you don’t see any content.
- they are keeping information into webapp.dist. go inside of this
- we check here by ls -la we can see all the default apps ROOT docs example host-manager manager
- these content we need to copy into webapps directory, then only we can access our applications 

```sh
cp -R * ../webapps                   (R for recursive, * means whatever in the current directory, ../ means one step uowords webapps folder)
```

