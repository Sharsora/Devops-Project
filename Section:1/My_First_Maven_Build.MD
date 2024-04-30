
# Create a First Maven Jenkins job to build hello-world project 
# *Jenkins Job name:* `My_First_Maven_Build`


### Steps to create "My_First_Maven_Build" Jenkin job
1. Login to Jenkins console
1. Create *Jenkins job*, Fill the following details,
   - *Source Code Management:*
      - Repository: `https://github.com/Sharsora/hello-world.git`
      - Branches to build : `*/main`  
   - *Build:*
     - Root POM:`pom.xml`
     - Goals and options: `clean install package`


