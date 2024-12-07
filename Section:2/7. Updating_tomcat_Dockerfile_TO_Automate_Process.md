- now creating docker image along with artifacts (webapp.war), so that whenever we launch a new container it will come up with an application. For that we need to copy this articats where we have our Dockerfile.
- we wil create separate directory to keep Dockerfile and artifacts so that in future we can use that location to create docker images.
- we will create directory call docker in /opt
- in the jenkins we have configure that artifcats copied by dockeradmin, that the reason its best practice to give ownership of this docker directory to dockeradmin
```sh
[root@dockerhost opt]# chown -R dockeradmin:dockeradmin docker
[root@dockerhost opt]# 
```
- now copy the Dockerfile onto Docker directory (/opt/docker)

```sh
[root@dockerhost ~]# mv Dockerfile /opt/docker/
[root@dockerhost ~]# 
```
```sh
[root@dockerhost ~]# chown -R dockeradmin:dockeradmin /opt/docker/
[root@dockerhost ~]# cd /opt/docker/
[root@dockerhost docker]# ls -la
total 4
drwxr-xr-x 2 dockeradmin dockeradmin 24 Dec  7 15:24 .
drwxr-xr-x 6 root        root        59 Dec  7 15:16 ..
-rw-r--r-- 1 dockeradmin dockeradmin 89 Dec  7 07:12 Dockerfile
[root@dockerhost docker]#
```
- Now we will ask jenkins to copy artifacts in the new created path /opt/docker
- for that in the Jenkins Job BuildtoDeploy on Container - change the configuration -
- *Post-build Actions*
     - Remote directory: `//opt//docker` (using // otherwise it will copy in to dockeradmin's home directory itself)

- Now we need to create container along with .war file (artifact). then only we can access our application from web browse. For that we need to change Dockerfile
```sh
vi Dockerfile

FROM tomcat:latest
RUN cp -R /usr/local/tomcat/webapps.dist/* /usr/local/tomcat/webapps
COPY ./*.war /usr/local/tomcat/webapps
```
- now create image out of it

```sh
docker build -t tomcat:v1 .  (. represent that in current location we have Dockerfile and build that one also we have .war file at that location so install that also)
```
```sh
[root@dockerhost docker]# docker images
REPOSITORY   TAG       IMAGE ID       CREATED          SIZE
tomcat       v1        1cdfd941c8c7   21 seconds ago   472MB
```

- now container out of it

```sh
docker run -d --name tomcatv1 -p 8085:8080 tomcat:v1
```

- After copying artifacts, i am building docker container manually this is not right choice, we need to tell to jenkins job that once the artifacts get copied you need to create container as well.
