- We create a new Jnekins Job to pull code from Github and deploy with help of maven and copy artifacts on to dockerhost. once it is availble on docker host from there copy inside to an container could be easy.
- copy the configurations of Build and deploy job, inside their configuration, instead of deplying we are going to copy artifacts onto docker host by using publish over ssh plugin.
- for that go to new iteam,copy from Buildanddeploy job so whatever configurations are there comes under here.
- in the post build action select Send build artifacts over SSH

