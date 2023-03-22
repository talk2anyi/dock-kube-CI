# dock-kube-CI

Steps for configuring a CI-CD pipeline integration for jenkins, docker and kubernetes to deploy an application.


### Deploy a linux instance on aws and ssh into your instance.

### Install docker on the instance using the official docs
`https://docs.docker.com/engine/install/ubuntu/`

### Install jenkins and java dependencies on the server 
`https://www.digitalocean.com/community/tutorials/how-to-install-jenkins-on-ubuntu-22-04`

1. Add jenkins and docker to the sudoer groups `sudo usermod -aG docker jenkins`. This would add jenkins to docker group and allow it perform docker commands with sudo rights.

2. Run the command to add the jenkins user to the sudoers group

`sudo echo "jenkins ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/jenkins`

3. Run `sudo chown jenkins  /var/run/docker.sock` to allow jenkins access the docker.sock directory.

4. Switch to your jenkins user with
`sudo su - jenkins`

### Install and configure a kubernetes production cluster with KOPS (as a jenkins user on the server)
- Install aws cli
- Configure s3 bucket
- Install KOPS software
- Create a KOPS cluster

### Access the jenkins UI and setup a pipepline project 
`serverIP:8080`
