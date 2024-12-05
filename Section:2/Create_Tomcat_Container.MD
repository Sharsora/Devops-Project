
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
- I can create a container out of that by using command
```sh 
docker run
```
