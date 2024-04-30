#  Install & configure Maven build tool on Jenkins
Maven is a code build tool used to convert your code to an artifact. this is a widely used plugin to build continuous integration

<img width="317" alt="image" src="https://github.com/Sharsora/Devops-Project/assets/135323873/082b1a3c-158d-4967-8c19-d873032b0975">

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
	
1. Setup M2_HOME and M2 paths in the .bash_profile of the user and add these to the path variable
   ```sh
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
