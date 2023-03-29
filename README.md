
# dock-kube-CI - Docker-kubernetes-Jenkins integration

This repository contains a DevOps project that demonstrates the end-to-end process of building, testing, and deploying an application. The project consists of a sample web application and the infrastructure needed to deploy it on a cloud-based platform.

Technologies Used
- Docker
- Kubernetes
- Jenkins
- AWS (Amazon Web Services)
- Git

## Architecture

The project's architecture consists of three main components:

- Web Application: A sample web application built using Python Flask framework, which is containerized using Docker. The application displays a simple message on a web page.

- Kubernetes: The application is deployed to a Kubernetes cluster running on AWS Elastic Kubernetes Service (EKS).

- Docker: Docker allows the build of the image for the application and push to dockerhub registry. 

- Jenkins: Jenkins is used as the CI/CD tool to automate the building, testing, and deployment of the application. The Jenkins pipeline is configured to build the Docker image, run unit tests, and push the Docker image to the Docker Hub registry. Upon successful build and tests, the pipeline triggers the Kubernetes deployment using the Kubernetes YAML files.

## Getting Started

### Prerequisites

To run this project, you will need:

- Docker
- Kubernetes
- Jenkins
- AWS EC2 instance
- Git

## Installation

To get started with the project, follow these steps:

Clone the repository using the following command:

```bash
git clone https://github.com/talk2anyi/dock-kube-CI.git
```

Change to the project directory:
```bash
cd dock-kube-CI
```

Build the Docker image:
```bash
docker build -t {docker_username}/{image_name}:{tag} .
```

Push the Docker image to the Docker Hub registry:
```bash
docker push {docker_username}/{image_name}:{tag}
```

Configure the Kubernetes cluster and deployment files with your AWS credentials and Docker image information.

Deploy the application to the Kubernetes cluster:
```bash
kubectl apply -f hello-app.yml
```

Configure Jenkins and create a new pipeline using the Jenkinsfile provided in the repository.

## NB:

Add jenkins and docker to the sudoer groups `sudo usermod -aG docker jenkins`. This would add jenkins to docker group and allow it perform docker commands with sudo rights.

Run the command to add the jenkins user to the sudoers group

`sudo echo "jenkins ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/jenkins`

Run `sudo chown jenkins  /var/run/docker.sock` to allow jenkins access the docker.sock directory.

Switch to your jenkins user with
`sudo su - jenkins`


## Usage

Once the application is deployed, you can access it by navigating to the Kubernetes service URL in a web browser. The application will display a simple message on the page.

## Conclusion

This project demonstrates the end-to-end process of building, testing, and deploying an application using Docker, Kubernetes, and Jenkins. The project's architecture provides a scalable and reliable solution to deploy web applications on cloud-based platforms like AWS. By following the steps outlined in this readme file, you can get started with the project and learn more about DevOps methodologies and best practices.


