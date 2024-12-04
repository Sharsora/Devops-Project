#  Install & configure Maven build tool on Jenkins
Maven is a code build tool used to convert your code to an artifact. this is a widely used plugin to build continuous integration

<img width="317" alt="image" src="https://github.com/Sharsora/Devops-Project/assets/135323873/082b1a3c-158d-4967-8c19-d873032b0975">

### Pre-requisites

1. Setup Maven on Jenkins Server
  - we can run build server separately (by createing dedicated server and install maven over there) but to reduce complexity we will use Jenkins server as build server as well
2. Setup Environment Variables
  - Maven is Java based application that is the reason we need Java, Howvere Java is already installed on Jenkins server
  - need to setup JAVA_HOME path and M2, M2_HOME (Maven Environment Variables) path 
3. Install Maven Plugins
4. Configure Maven and JAVA
  - Because we haven't told to our Jenkins GUI that that is where JAVA is installed

#### Install Maven on Jenkins
1. Download maven packages https://maven.apache.org/download.cgi onto the Jenkins server. In this case, I am using /opt/maven as my installation directory
 - Link: https://maven.apache.org/download.cgi
    ```sh
     # Creating a maven directory under /opt
     mkdir /opt/maven
     cd /opt/maven
     # downloading maven version 3.6.0
     wget http://mirrors.estointernet.in/apache/maven/maven-3/3.6.1/binaries/apache-maven-3.6.1-bin.tar.gz
     tar -xvzf apache-maven-3.6.1-bin.tar.gz
     ```

##### Question
Why we need to setup environment variables?
-  Here in this case, we go to folder where maven is extracted and then go to bin folder in it
```[root@jenkins-server maven]# ls -la
total 36
drwxr-xr-x 6 root root    99 Dec  4 10:09 .
drwxr-xr-x 3 root root    56 Dec  4 10:10 ..
drwxr-xr-x 2 root root    97 Dec  4 10:09 bin
drwxr-xr-x 2 root root    76 Dec  4 10:09 boot
drwxr-xr-x 3 root root    63 Aug 14 08:48 conf
drwxr-xr-x 4 root root  4096 Dec  4 10:09 lib
-rw-r--r-- 1 root root 18920 Aug 14 08:48 LICENSE
-rw-r--r-- 1 root root  5034 Aug 14 08:48 NOTICE
-rw-r--r-- 1 root root  1279 Aug 14 08:48 README.txt
[root@jenkins-server maven]# cd bin/
[root@jenkins-server bin]# ls -la
total 32
drwxr-xr-x 2 root root   97 Dec  4 10:09 .
drwxr-xr-x 6 root root   99 Dec  4 10:09 ..
-rw-r--r-- 1 root root  327 Aug 14 08:48 m2.conf
-rwxr-xr-x 1 root root 5917 Aug 14 08:48 mvn
-rw-r--r-- 1 root root 6324 Aug 14 08:48 mvn.cmd
-rwxr-xr-x 1 root root 1684 Aug 14 08:48 mvnDebug
-rw-r--r-- 1 root root 2169 Aug 14 08:48 mvnDebug.cmd
-rwxr-xr-x 1 root root 1611 Aug 14 08:48 mvnyjp
[root@jenkins-server bin]# 
```
- here we have actual command of maven. we can excute here
```"./mvn -v "
```
	
1. Setup M2_HOME and M2 paths in the .bash_profile of the user and add these to the path variable
   ```sh'
   vi ~/.bash_profile
   M2_HOME=/opt/maven/apache-maven-3.6.1
   M2=$M2_HOME/bin
   JAVA_HOME=/usr/lib/jvm/java-11-openjdk-11.0.12.0.**************
   PATH=<Existing_PATH>:$M2_HOME:$M2:$JAVA_HOME
   ```
   If you don’t know Java Home path then find using command find / -name jvm you will get output /usr/lib/jvm or else you can find using command find / -name java-11*

   To check whether our changes are affected or not
   ```sh
   echo $PATH
   ```
   It's not yet updated because we have to re-login to root user or else we can use a command (source command read the .bash_profile again and load the values which are updatd)
   ```sh
   source .bash_profile
   echo $PATH
   ```

#### Checkpoint 
1. logoff and login to check maven version
  
    ```sh
    mvn --version
    ```
So far we have completed the installation of Maven software to support Maven plugin on the jenkins console. Let's jump onto Jenkins to complete the remaining steps. 

### Setup maven on Jenkins console
1. Install maven plugin without restart  
  - `Manage Jenkins` > `Jenkins Plugins` > `available` > `Maven Integration`

2. Configure maven path
  - `Manage Jenkins` > `Global Tool Configuration` > `Maven` > `Add Maven` > Remove install automatically and mention Maven Home Path `/opt/maven`
  - `Manage Jenkins` > `Global Tool Configuration` > `JDK` > `Add JDK` > Remove install automatically and mention JAVA Home Path `/usr/lib/jvm/java-11-openjdk-11.0.12.0.**************`
