# Devops-Project


# Build and Deploy a complete JAVA application

We use 

Git - as a local version control system

Github - as a distributed version control system

Jenkins - as a continuous integration tool

Maven - as a build tool

Ansible - as a configuration Management and deployment tool

Docker - containerization 

Kubernetes - as a container management tool


All these environments on AWS Cloud

Usually, we have the source code with developers and developers commit this code onto a distributed version control system during the development phase.

Further, we are going to use the continuous integration tool called Jenkins.

Once Jenkins builds the code, it generates artifacts.

For those artifacts, we need to deploy it onto the target environment.

So, we need some tool that can able to deploy the artifacts on the target environment.

In our case, we are going to use Ansible as a deployment tool and it can able to deploy
our applications on your VM or your Docker container or Kubernetes.

In our case, initially, we will deploy our application on VM.

Then, we are going to deploy it on a Docker container.

At last, we are going to deploy it on Kubernetes.


