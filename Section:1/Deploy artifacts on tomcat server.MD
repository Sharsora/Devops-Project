- We need to update our source code
- To update our source code, We can pull this code onto our local workstation update the code and commit it to Github.
- Once it is committed we can compile and build our code with help of maven and we can deploy it onto tomcat server

### Step 1: 
- first I need to clone my code from github to my local system, update the code and I should commit it github.
- need to clone our hello world code onto my workstation
- I would like to clone this repository into this Desktop
- I will switch onto this location on my git bash
- clone from Github, copy the repository url that should be https and go here clone it
- So we have downloaded code onto our local system and if I see hello world is there
- I see whatever files you can see in the remote server same files are cloned over here
- I would like to update index.jsp file, go back to web apps under this src main web app, here we have index.jsp so we just need to edit this file
- searching for form filling html code so go here and this kind of output we are going to get if we use the code whatever is available over here
- taking this code ok so we will just update this one in our index.jsp and save it
- run 
```git status
- git add. (Added files to staging area)
- git status 
- git commit -m "updated index.jsp file" (I am committing these files on to the local repository)
- git push origin master (Now I am committing these changes on to the remote repository, so we are pushing the code on to remote repository)```

- I am trying to commit my code on to my github account it is asking for personal access token earlier it used to ask for the password
- recently github has enabled personal access token authentication that is the reason we must use this one
- But so far we haven't created any personal access token so we should go and create it now
- For that let's go back to our github account this is our github account and we should go to or we can just check for how to do that one
-  We should go to our account then settings under settings we should go to developer settings under that personal access token
-  Then we need to give some personal access token name once we have given we can choose when it can expire and also we can choose what kind of privileges we should give




