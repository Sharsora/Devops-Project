- We create a new Jnekins Job to pull code from Github and deploy with help of maven and copy artifacts on to dockerhost. once it is availble on docker host from there copy inside to an container could be easy.
- copy the configurations of Build and deploy job, inside their configuration, instead of deplying we are going to copy artifacts onto docker host by using publish over ssh plugin.
- for that go to new iteam,copy from Buildanddeploy job so whatever configurations are there comes under here.
- in the post build action select Send build artifacts over SSH
- in that transfer means which file need to upload, /var/lib/jenkins/workspace/webapp/target/webapps.war (webapp/target/*.war)
- i dont require prefix webapp/target so i will mentioned that in Remove prefix
- remote directory /home/dockeradmin if not specify it will take by default that only. (no need to specify)

### Steps to create "Deploy_on_Docker_Host" Jenkin job
 #### From Jenkins home page select "New Item"
   - Enter an item name: `Deploy_on_Docker_Host`
     - Copy from: `Deploy_on_Tomcat_Server`
     
   - *Source Code Management:*
      - Repository: `[https://github.com/yankils/hello-world.git](https://github.com/Sharsora/hello-world.git)`
      - Branches to build : `*/main`  
   - *Poll SCM* :      - `* * * *`

   - *Build:*
     - Root POM:`pom.xml`
     - Goals and options: `clean install`

 - *Post-build Actions*
   - Send build artifacts over SSH
     - *SSH Publishers*
      - SSH Server Name: `dockerhost`
       - `Transfers` >  `Transfer set`
            - Source files: `webapp/target/*.war`  (which files we would like to upload)
	       - Remove prefix: `webapp/target`
	       - Remote directory: `//home//ansadmin` or `.`
	 

Save and run the job now.
