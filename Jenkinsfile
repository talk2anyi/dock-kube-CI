pipeline {
    agent any
    stages {
        stage('Git Clone') {
            steps {
                git credentialsId: 'Git-hub-Credentials', url: 'url of repo to clone'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t talk2anyi/hello-app .'
            }
        }
        stage('Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'Dockerhub-login', passwordVariable: 'Dockerhub_Password', usernameVariable: 'Dockerhub_Username')]) {
                sh 'docker login -u $Dockerhub_Username -p $Dockerhub_Password'
                }
            }
        }
        stage('Remove Docker Images') {
            steps {
                sh 'docker rmi $(docker images -q)'
            }
        }
        stage('Deploy App to Kubernetes') {
            steps {
              withAWS(credentials: 'awscredential', region: 'us-east-1'){
              echo 'deployment into kubernetes cluster'  
              sh 'kubectl apply -f hello-app.yml'
              }
            }
        }
    }
}
