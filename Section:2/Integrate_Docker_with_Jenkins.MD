#### To Integrate Docker with Jenkins

1. create dockeradmin user in the docker group on dockerhost
2. Install Publish over SSH plugin (to copy artifact from Jenkins to Docker Host)
3. Add Dockerhost to Jenkins Configure systems (to communicate with dockerhost from jenkins)

 - To check what users are there

```sh
cat /etc/passwd

xxxxxxx (system users)
xxx     (system users)
xx      (system users)
x       (system users)
ec2-user:x:1000:1000:EC2 Default User:/home/ec2-user:/bin/bash
```

```sh
[root@dockerhost ~]# cat /etc/group
xx
xx
docker:x:992:
```
- created user by useradd dockeradmin and set password by using passwd command
- add user to docker group, by using `usermod -aG docker dockeradmin`

- when you are trying to access using this new user dockeradmin in to docker host, you will get error. because it is not asking for password
- By default EC2 instance does not allows password based authentication. we should explicitly enable it.

#### How to enable password based authentication 
```sh
vi /etc/ssh/ssh_config

/PasswordAuthentication

# To disable tunneled clear text passwords, change to no here!
#PasswordAuthentication yes
#PermitEmptyPasswords no
PasswordAuthentication no
```

so here we need to uncomment first and then second one need to comment it out
```sh
vi /etc/ssh/ssh_config

# To disable tunneled clear text passwords, change to no here!
PasswordAuthentication yes
#PermitEmptyPasswords no
#PasswordAuthentication no
```
- now restart sshd service. Do not stop and start because you loose the connection to docker host as you are connected to ssh service itself.
```sh
service sshd reload
```

### Integration between Docker-host and Jenkins

Install "publish Over SSH"
 - `Manage Jenkins` > `Manage Plugins` > `Available` > `Publish over SSH`

Enable connection between Docker-host and Jenkins

- `Manage Jenkins` > `Configure System` > `Publish Over SSH` > `SSH Servers` 

	- SSH Servers:
                - Name: `docker-host`
		- Hostname:`<ServerIP>`
		- username: `dockeradmin`
               
       -  `Advanced` > chose `Use password authentication, or use a different key`
		 - password: `*******`

   - if you want to go with key based authentication then generat it 
   - login as dockeradmin
   - ssh-keygen
   - key will generate at path /home/dockeradmin/.ssh, you will have id.rsa & id.rsa.pub
