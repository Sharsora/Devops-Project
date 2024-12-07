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
