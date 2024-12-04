- Whenever I do some changes to my source code, immediately my build should trigger
- whenever there is some change in github, it should automatically identify and execute the build job and deploy the code
- select existing job, Build and Deploy job, select the configure
- we have build triggers
   - Build whenever a SNAPSHOT dependency is built (nothing but manul build)
   - Trigger builds remotely (if you wish to build the jenkins job from the remote server)
   - Build periodically (you wish to execute your job two times in a day so you can mentioned here when you want to execute your job, you can specify cron job entry)
     (it help us to execute the job irrespective of whether our code has been changed or not)
   - Poll SCM
     (this also works based on cron job)
     (in this case we need to schedul a job, in the specific period of time, it will go and validate whether there is any changes in repository or not. IF there are no changes build is not going to happen. If there are some changes build gets execute.)

### Difference between Build periodically and Poll SCM
- in periodically, irrespective of code change build will get execute
- in Poll SCM, it will go and validate whether there are changes or not, if there are changes then job will get execute, if there are no changes build wont happen.


