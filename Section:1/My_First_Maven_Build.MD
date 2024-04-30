
# Create a First Maven Jenkins job to build hello-world project 
# *Jenkins Job name:* `My_First_Maven_Build`


### Steps to create "My_First_Maven_Build" Jenkin job
1. Login to Jenkins console
1. Create *Jenkins job*, Fill the following details,
   - *Source Code Management:*
      - Repository: `https://github.com/Sharsora/hello-world.git`
      - Branches to build : `*/main` / `*/master` 
   - *Build:*
     - Root POM:`pom.xml`
     - Goals and options: `clean install`

Build successfully and it creates a war file webapp.war

It's executed under /var/lib/jenkins/workspace/FirstMavenProject/webapp/target/webapp.war
under the target directory artifacts get created (webapp.war is an artifact nothing but our build outcome)

<img width="1009" alt="image" src="https://github.com/Sharsora/Devops-Project/assets/135323873/f3fca82f-1435-4b4d-93d0-ae55e757563f">
