
### Set up our Docker container
- To create a docker container we need a docker image.

#### how do we get this docker image?
1. From the docker hub
 - docker hub is a public repository which contains the docker images.We can use a command ```docker pull ``` to take the image onto our local system.
2. Creating our own docker file.
 - we are going to pull the basic image from the docker hub itself and top of that one we can do our own customization with the help of docker file.
 - Docker file contains instructions what your docker container should get.To create a docker image out of docker file we are going to use ```docker build``` command.
