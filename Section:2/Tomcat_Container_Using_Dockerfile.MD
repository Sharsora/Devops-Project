- we can create tomcat container using docker file similar way we created earlier. but the problem we face while gtting default imgaes that we could not get the home page. we are getting HTTP 404 not found error. to overcome this one we need to pull tomcat image into docker file then we need to copy webapps.dist directory content on to webapps directory.

- we will create new Dockerfile, which can able to pull latest tomcat image then will move the content.

- To remove dokcer file
```sh
rm Dockerfile
```

- now we will create new Dockerfile. here we will get tomcat image and then we need to move the content, for that we need know where exactly this located? It should be in the Catalina home directory. need to find out that what is the catalina home directory of docker file. for that search for tomcat official image in docker hub, in the documentation we got CATALINA_HOME:   /usr/local/tomcat. in this location you have webapps directorys.
- ( /* ) means whatever content is there 

```sh
vi Dockerfile

FROM tomcat:latest
RUN cp -R /usr/local/tomcat/webapps.dist/* /usr/local/tomcat/webapps
```
- now build this Dockerfile

```sh
docker build -t demotomcat .
```
```sh
docker images
```
```sh
docker run -d --name demotomcat-container -p 8084:8080 demotomcat
```

```sh
docker ps -a
```
