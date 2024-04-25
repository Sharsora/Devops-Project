### Set up our Jenkins server

1. Login to the AWS console and create a new EC2 instance
   - Choose Amazon Linux 2 AMI
   - Select t2.micro instance type
   - Add tag Jenkins_Server
   - Create a new security group as Jenkins_Security_Group
   - Add new rule custom TCP port 8080
   - Create a new key pair name as DevOps_Project_Key and Download it
2. Connect EC2 instance and install JAVA & Jenkins
   ```sh
   ssh -i "DevOps_Project_Key.pem" ec2-user@public_ip_ec2-instance
   ```
   - login as root
   ```sh
   sudo su -
   ```
   Get the latest version of jenkins from https://pkg.jenkins.io/redhat-stable/ and install
   ```sh
   sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
   sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
   amazon-linux-extras install epel 
   amazon-linux-extras install java-openjdk11
   yum install jenkins
   ```
   ### Start Jenkins
   ```sh
   # Start jenkins service
   service jenkins start

   # Setup Jenkins to start at boot,
   chkconfig jenkins on
   ```
