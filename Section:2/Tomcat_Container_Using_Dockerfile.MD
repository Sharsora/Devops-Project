- we can create tomcat container using docker file similar way we created earlier. but the problem we face while gtting default imgaes that we could not get the home page. we are getting HTTP 404 not found error. to overcome this one we need to pull tomcat image into docker file then we need to copy webapps.dist directory content on to webapps directory.

- we will create new Dockerfile, which can able to pull latest tomcat image then will move the content
