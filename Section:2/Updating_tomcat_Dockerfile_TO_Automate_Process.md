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
