Create a aws Free Tair account and Launch a Ubuntu 16.04 LTS (t2.micro) instance and install Configuration Management Tool (Ansible) and Python also mandatory to perform configuration management activite in both Ansible Controller and Ansible Nodes. We have to establish a ssh connection between ansible controller and ansible nodes.
!$$$$$$$
1)Launch Ec2 Instance Using Ansible Playbook:

First of all, we will discuss the basic requirements that need to be initialized to launch an EC2 instance. We will need the following details:
        region => The region in which the instance needs to be launched.
        security group => The security group to be associated with the instance.
        image-id => The AMI id by which the instance is to be launched.
        instance-type => The type of the instance.
        key-pair => The Pem file to authenticate the login process.
        count => The number of instances to be launched.
        instance_tags => Name of th eLaunching Instances.
        
The statement “wait=yes” is used to let ansible wait for the instance to come. The statement “register: ec2″ register the output in ec2
variable so that we can run the query to find out different properties of the instance.By using these above tasks in the  ansible playbook
the instance will be created and configured. Make sure the host from which you are running the playbook must have enough permissions to
launch the EC2 instance. This playbook can run in only localhost machine where anible is installed.
####Run a palybook: ansible-playbook Launch-Instances.yml
With the help of above command we can Launch a two instances (MSR-test-Instance-1 & MSR-test-Instance-2).
!$$$$$$$
2) Installing Software Packages

!!!For NVM-Version 0.33.2. Write a Ansibel to playbook to install nvm For this requirement i have use SHELL module in ansible and download the mvn.sh script and run on ansible nodes (MSR-test-Instance-1 & MSR-test-Instance-2). 
####Run a palybook: ansible-playbook 1.NVM-Version0.33.2.yml
We can Check above NVM version is installed or not
Command: Sudo su -
Command: nvm--version 

!!!For Node-8.12.0. Write a ansible playbook Install Node-8.12.0
####Run a palybook: ansible-playbook 2.Node-8.12.0.yml
We can Check above Node version is installed or not
Command: node --version

!!!For Docker 18.06 or Latest. Write a playbook to install docker in ansible nodes. For this requirement i have used a COMMAND module in ansible to download the script fron get.docker.com and run it on ansible nodes.
####Run a palybook: ansible-playbook 3.Docker.yml
We can Check above Docker version is installed or not
Command: docker --version

!!!For Docker Compose-1.13 or latest. Write a playbook to install Docker compose. For this requirement i have to take a command to install docker compose and execute this in a ansible command module nad give the permissions of the /usr/local/bin/docker-compose .
####Run a palybook: ansible-playbook 4.Docker-compose.yml
We can Check above Docker compose version is installed or not
Command: docker-compose --version

!!!For Openssl-latest Version. Write a ansible playbook to install openssl. Download the openssl latest Version .tar file and extract it to ansible nodes. Using wget i can download it
####Run a palybook: ansible-playbook 5.OpenSSL.yml
We can Check above Openssl compose version is installed or not
Command: openssl --version -a

!!!For Git-Latest Version. Write a snible playbook to install git. Using apt module install the git, name=Git and state=Present
####Run a palybook: ansible-playbook 6.git.yml
We can Check above git compose version is installed or not
Command: git --version

!$$$$$$
3) Push playbook in to git hub
Create a Repositoey in local machine and initilze it (git init) and configure the username and email, and commit all changes in local repository, and finally pushes in to git hub (git push -u origin master).










        
