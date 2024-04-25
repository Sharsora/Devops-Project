### Set up our Jenkins server

1. Login to the AWS console and create a new EC2 instance
   - Choose Amazon Linux 2 AMI
   - Select t2.micro instance type
   - Add tag Jenkins_Server
   - Create a new security group as Jenkins_Security_Group
   - Add new rule custom TCP port 8080
   - Create a new key pair name as DevOps_Project_Key and Download it
2. Connect EC2 instance and install JAVA
   ```sh
   ssh -i "DevOps_Project_Key.pem" ec2-user@public_ip_ec2-instance
   ```
