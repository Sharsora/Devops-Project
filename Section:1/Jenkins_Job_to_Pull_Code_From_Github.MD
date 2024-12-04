# *Jenkins Job name:* `Pull_Code_From_Github`

- create a new item.
- Job name I have given pull code from github and it is a freestyle project.
- description I am giving same as job name.
- In the source code management select Git.
 - we should provide our github repository URL.
- usually you should provide credentials in case if it is a private repository, As of now it is a public repository so there is no credentials necessity.
- we are not yet building because appropriate build configurations we haven't done so apply and save it.
- I have created a new Jenkins job just to pull the code and let's build 
- this I am trying to build this job and it has cloned the repository and successful 
- job is successful and it successfully cloned onto our Jenkins server.
- whenever Jenkins do any build activities it will do under workspace.
- same we can verify on the Jnekins-Server
```[ec2-user@jenkins-server ~]$ cd /var/lib/jenkins/workspace/
[ec2-user@jenkins-server workspace]$ ls -la
total 4
drwxr-xr-x  4 jenkins jenkins   53 Dec  3 15:37 .
drwxr-xr-x 14 jenkins jenkins 4096 Dec  4 09:37 ..
drwxr-xr-x  2 jenkins jenkins    6 Dec  3 11:18 HelloWorldJob
drwxr-xr-x  4 jenkins jenkins   47 Dec  4 09:36 PullCodeFromGitHub
[ec2-user@jenkins-server workspace]$ cd PullCodeFromGitHub/
[ec2-user@jenkins-server PullCodeFromGitHub]$ ll
total 8
-rw-r--r-- 1 jenkins jenkins 6333 Dec  4 09:36 pom.xml
drwxr-xr-x 2 jenkins jenkins   23 Dec  4 09:36 webapp
[ec2-user@jenkins-server PullCodeFromGitHub]$ 

- by default Jenkins is going to store all the build related information under /var/lib/jenkins/workspace/
